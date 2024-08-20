# Enhanced MSTC Algorithm for Multi-Robot Systems

## Description

This project focuses on improving the security and efficiency of the Multiple Spanning Tree Coverage (MSTC) algorithm for multi-robot systems. By addressing critical vulnerabilities, such as the "Intruder Death Loop," and optimizing both offline and online MSTC algorithms, this implementation enhances the performance and robustness of multi-robot coverage path planning.

The algorithm partitions the map using a minimum number of bricks as spanning tree branches, greedily connects them to form a complete spanning tree, and applies the MSTC* strategy to find the optimal division around topological loops. This approach incorporates turn costs into path weights, ensuring balanced and efficient coverage across all robots.

## Key Features

- **Vulnerability Mitigation:** Addressed critical vulnerabilities like the "Intruder Death Loop" to ensure uninterrupted and secure operation.
- **Algorithm Optimization:** Enhanced both offline and online MSTC algorithms to improve coverage efficiency and performance.
- **Turn Minimization:** Integrated turn cost into path planning to optimize coverage routes.
- **Balanced Coverage:** Ensured even distribution of coverage responsibilities among robots.

## 1. Prerequisites

Ensure your system meets the following requirements:

- **Operating System:** Ubuntu 16.04 or 18.04 with ROS Kinetic or Melodic.
- **Gazebo Models:** Make sure Gazebo has all necessary models. If you're using ROS Kinetic, clone the models repository to avoid simulation issues.

```bash
cd ~/.gazebo && mkdir models
cd ~/.gazebo/models
git clone https://github.com/osrf/gazebo_models
```

## 2. Build the Package on ROS

Clone the repository into your ROS workspace and build the package:

```bash
cd ~/catkin_ws/src
git clone https://github.com/YourUsername/Enhanced-MSTC.git
cd ../
catkin_make
source ~/catkin_ws/devel/setup.bash
```

## 3. Run the Programs

Launch the simulation and run the necessary nodes:

```bash
roslaunch MSTC_Star_update main.launch
rosrun MSTC_Star_update realTf_broadcaster
rosrun MSTC_Star_update map_transformer
```

## 4. Parameters Explanation (main.launch)

- `/robot_number`: Specifies the number of robots in the simulation.
- `/allocate_method`: Choose between "DARP" or "MSTC" for allocation.
- `/MST_shape`: Select the spanning tree construction method: "DFS_HORIZONTAL," "DFS_VERTICAL," "KRUSKAL," "ACO," "HEURISTIC," "RECT_DIV," or "DINIC."
- `/coverAndReturn`: Decide whether robots should return to their depot after coverage (`true` or `false`).
- `/data_file_path`: Path for storing results, including planning time and coverage time (min and max).
- `/map_scale`: Determines the size of the coverage map relative to the number of image pixels.
- `/coverage_action`: Set to "false" if you want to visualize planning paths without actual coverage.

To use the enhanced MSTC algorithm (TMSTC*), set both `/MST_shape` to "MSTC" and "DINIC." Modify `main.launch` to adjust the number of robots or change the map by editing the image path in `map/map.yaml`.

## 5. Validation and Analysis

The improved MSTC algorithm has been rigorously validated through extensive analysis, demonstrating significant improvements in security, efficiency, and performance in multi-robot coverage path planning.

---
