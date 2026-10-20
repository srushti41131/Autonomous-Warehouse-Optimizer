# 🤖 Autonomous Warehouse Fulfillment Optimizer

![RL](https://img.shields.io/badge/RL-Reinforcement%20Learning-blue) 
![Python](https://img.shields.io/badge/Python-3.10+-yellow)
![PPO](https://img.shields.io/badge/Algorithm-PPO-green)

## 📌 Project Overview
This project implements a **Deep Reinforcement Learning (DRL)** agent designed to optimize robot routing in a simulated warehouse environment. The goal is to maximize fulfillment efficiency by minimizing **Order Cycle Time** and reducing operational costs associated with collisions and energy consumption.

## 💼 Business Impact
In a real-world logistics setting, inefficient routing leads to increased labor costs and delayed shipments. This AI solution targets three key **KPIs**:
- **Throughput Optimization:** Reducing the number of steps to reach a target.
- **Risk Mitigation:** Minimizing collisions with warehouse infrastructure (shelves).
- **Energy Efficiency:** Reducing unnecessary movement to preserve robot battery life.

## 🛠️ Technical Implementation

### 1. The Environment
Built using `Gymnasium`, the simulation consists of a 2D grid representing a warehouse floor with static obstacles (shelves) and dynamic target locations.

### 2. The Brain (The Agent)
I utilized the **Proximal Policy Optimization (PPO)** algorithm from the `Stable-Baselines3` library. PPO was chosen over DQN for its superior stability and faster convergence in discrete navigation tasks.

### 3. Solving the "Sparse Reward Problem"
Initially, the agent struggled to find the target through random exploration (known as the Sparse Reward problem). To solve this, I implemented **Reward Shaping**. 

**The Reward Function:**
- **Success (+100):** Revenue generated upon successful delivery.
- **Collision (-10):** Maintenance cost incurred by hitting a shelf.
- **Distance Guidance (+1 / -1.5):** A "compass" reward based on **Manhattan Distance**, rewarding the agent for moving closer to the target and penalizing it for moving away.

## 📈 Results
- **Convergence:** The agent successfully learned to navigate the warehouse, moving from random wandering to direct pathfinding.
- **Efficiency:** Significant reduction in average steps per delivery compared to the untrained state.
- **Safety:** Achieved a 0% collision rate during final testing evaluations.

## 🚀 How to Run
1. Clone the repo:
   ```bash
   git clone https://github.com/srushti41131/Autonomous-Warehouse-Optimizer.git

2.Install dependencies:
pip install gymnasium stable-baselines3 numpy matplotlib shimmy torch
