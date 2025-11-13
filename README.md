# ROS2_Mapping_SLAM_Toolbox
This ROS 2 package contains a complete robot URDF model integrated with essential sensors and plugins for 2D SLAM mapping using slam_toolbox. It includes RGB-D camera, LiDAR, IMU, and odometry plugins with Gazebo and RViz support, enabling real-time 2D mapping, map generation, saving and sensor visualization in simulation.

---

## ⚙️ Features

- **Complete Robot Description:** Includes `.urdf` and `.xacro` files with linked `.stl` CAD meshes.  
- **Sensor Integration:** Equipped with 2D LiDAR, IMU, and odometry plugins for accurate mapping.  
- **SLAM Toolbox Integration:** Enables real-time 2D mapping.  
- **Map Saving & Loading:** Easily save generated maps (`.yaml` + `.pgm`) for later navigation use.  
- **Multi-Environment Simulation:** Test mapping in various Gazebo worlds like small rooms or warehouses.  
- **ROS 2 Compatibility:** Works seamlessly with `slam_toolbox`, `nav2`, and `gazebo_ros_pkgs`.  

---

## 🧠 Learning Objectives

By using this package, you will learn how to:

1. **Understand Robot Description in ROS 2**  
   - Explore how URDF/XACRO files define the robot’s physical structure, links, joints, and sensors.  
   - Visualize your robot model and sensor frames in RViz.  

2. **Perform 2D Mapping Using SLAM Toolbox**  
   - Launch `slam_toolbox` in mapping mode to create a real-time map from LiDAR data.  
   - Move the robot through teleoperation or navigation commands to scan the environment.  
   - Observe the generated occupancy grid map updating in RViz.  

3. **Save and Export the Map**  
   - After mapping, save the environment as .pgm and .yaml map files for future navigation.  

---

## Installation

### Change Workspace
```bash
cd ros_ws/src
```

### Clone This Repository
```bash
git clone https://github.com/yashbhaskar/ROS2_Mapping_SLAM_Toolbox.git
```

### Clone SLAM Toolbox Repository (optional you can also install through sudo this is for learning)
```bash
git clone -b humble https://github.com/SteveMacenski/slam_toolbox.git
```

### OR

### Install SLAM Toolbox Through sudo
```bash
sudo apt install ros-humble-slam-toolbox
```

### Build the Package
```bash
colcon build --packages-select my_bot slam_toolbox
source install/setup.bash
```

---

## 🚀 How to Run

### 1st Terminal : Launch robot
```bash
ros2 launch my_bot gazebo.launch.py
```

### 2nd Terminal : Start the slam_toolbox Mapping
```bash
ros2 launch slam_toolbox online_async_launch.py use_sim_time:=True
```

### 3rd Terminal : Move Using The Keyboard
```bash
ros2 run teleop_twist_keyboard teleop_twist_keyboard
```

- **Add Map:** In RViz, click **Add → By Topic → Map** to display the generated map.  
- **Add map Fixed Frame:** Change the **Fixed Frame** (top left) to `map` — the grey occupancy grid map should now appear.  
- **Move Robot:**white: free space, black: obstacle, grey: unknown. Now all we need to do is to make the robot move in the map, so that the grey (unknown) pixels will turn white or black. When we have a result that satisfies us, we can save the map..  

### 4th Terminal : Save Map
```bash
ros2 run nav2_map_server map_saver_cli -f my_genrated_map
```

### 💾 Alternative Way to Save the Map

You can also save the map directly from **RViz**:  
- Go to **Panels → Add New Panel → Map Saver**.  
- Use the **Save** button to export your current map (`.pgm` and `.yaml` files).

---

## ✉️ Contact

📧 Yash Bhaskar – ybbhaskar19@gmail.com

📌 GitHub: https://github.com/yashbhaskar

