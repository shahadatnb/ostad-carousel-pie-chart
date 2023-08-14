<template>
  <div>
    <canvas id="myChart"></canvas>
  </div>
</template>

<script setup>
import { ref, onMounted, onBeforeUnmount } from 'vue';
import Chart from 'chart.js/auto';

const chartRef = ref(null);
let chartInstance = null;

onMounted(() => {
    // Fetch data from a sample data source or manually create data for the chart
    const chartData = {
    labels: ['Red', 'Blue', 'Yellow'],
    datasets: [
        {
        data: [10, 20, 30],
        backgroundColor: ['#ff6384', '#36a2eb', '#ffce56'],
        },
    ],
    };

    // Create the pie chart
    //const ctx = chartRef.value.getContext('2d');
    const ctx = document.getElementById('myChart');
    chartInstance = new Chart(ctx, {
        type: 'pie',
        data: chartData,
    });
});

onBeforeUnmount(() => {
    // Clean up the chart instance
    if (chartInstance) {
    chartInstance.destroy();
    chartInstance = null;
    }
});

</script>

<style>
canvas {
  width: 100%;
  height: 100%;
}
</style>
