# The better rb1_ros2_description package

## Description
This package contains a ROS2 robot model description for Robotnik's RB-1 mobile base. The package has been modified and some additional features have been added. This is why I call the package the better version :)

## Installation instructions

The installation process is as simple as possible. Just clone (download) the package into your workspace and compile everything.  For example, you can use the following process:

```console
# cd ~/ros2_ws/src
# git clone https://github.com/rg-masterclass/rb1_ros2_description.git
# cd ..
# colcon build ; source install/setup.bash
```

## Getting started

As previously, this is a pretty easy step. Just run the simulation and wait for a while to get everything started and available. You can prepare some coffee or tea, it can take a while, depending on your hardware capabilities.

```console
# ros2 launch rb1_ros2_description rb1_ros2_xacro.launch.py
```

## Controller activation

The controller starts automatically, thanks to the mentioned above launch file. But, if you want to, you can use the ROS2 control command line interface and do it manually.

## Moving the robot

#### Automatic

```console
# ros2 topic pub --rate 10 /rb1_base_controller/cmd_vel_unstamped geometry_msgs/msg/Twist "{linear: {x: 0.0, y: 0, z: 0.0}, angular: {x: 0.0,y: 0.0, z: 0.2}}"
```

#### Manual

```console
# ros2 run teleop_twist_keyboard teleop_twist_keyboard --ros-args --remap cmd_vel:=/rb1_base_controller/cmd_vel_unstamped
```

## Moving the robot's lifting unit

If you want to move the lifting platform up or down, you have to publish to the /lifting_effort_controller/commands topic. You can do it with the following commands:

#### Up

```console
# ros2 topic pub /lifting_effort_controller/commands std_msgs/msg/Float64MultiArray "{data: [10.0]}" --once
```

#### Down

```console
# ros2 topic pub /lifting_effort_controller/commands std_msgs/msg/Float64MultiArray "{data: [0.0]}" --once
```

Have a nice fun! See you in the other repositories!

## Disclaimer (old):  
This package only modifies/adapts files from these repositories/packages:  
- [RobotnikAutomation/rb1_base_sim](https://github.com/RobotnikAutomation/rb1_base_sim) licensed under the BSD 2-Clause "Simplified" License
- [RobotnikAutomation/rb1_base_common/rb1_base_description](https://github.com/RobotnikAutomation/rb1_base_common/tree/melodic-devel/rb1_base_description), licensed under the BSD License
- [RobotnikAutomation/robotnik_sensors],(https://github.com/RobotnikAutomation/robotnik_sensors) licensed under the BSD License
