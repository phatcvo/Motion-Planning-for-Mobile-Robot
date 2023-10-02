## Get ready
To install dependent packages, folloe the instructions in 
1. [Setup turtlebot3 on PC](https://emanual.robotis.com/docs/en/platform/turtlebot3/quick-start/#pc-setup)
    ```
    # Install ROS (noetic for Ubuntu 20.04)
    $ sudo apt update
    $ sudo apt upgrade
    $ wget https://raw.githubusercontent.com/ROBOTIS-GIT/robotis_tools/master/install_ros_noetic.sh
    $ chmod 755 ./install_ros_noetic.sh 
    $ bash ./install_ros_noetic.sh
    
    # Install Dependent ROS Packages
    $ sudo apt-get install ros-noetic-joy ros-noetic-teleop-twist-joy \
      ros-noetic-teleop-twist-keyboard ros-noetic-laser-proc \
      ros-noetic-rgbd-launch ros-noetic-depthimage-to-laserscan \
      ros-noetic-rosserial-arduino ros-noetic-rosserial-python \
      ros-noetic-rosserial-server ros-noetic-rosserial-client \
      ros-noetic-rosserial-msgs ros-noetic-amcl ros-noetic-map-server \
      ros-noetic-move-base ros-noetic-urdf ros-noetic-xacro \
      ros-noetic-compressed-image-transport ros-noetic-rqt* \
      ros-noetic-gmapping ros-noetic-navigation ros-noetic-interactive-markers
      
    # Install TurtleBot3 via Debian Packages
    $ sudo apt-get install ros-noetic-dynamixel-sdk
    $ sudo apt-get install ros-noetic-turtlebot3-msgs
    $ sudo apt-get install ros-noetic-turtlebot3
    
    # Additional setup
    echo 'export TURTLEBOT3_MODEL=waffle' >> ~/.bashrc 
    ```
2. [Install Simulation Package](https://emanual.robotis.com/docs/en/platform/turtlebot3/simulation/#gazebo-simulation). 
    ```
    $ cd ~/<your_dir>/catkin_ws/src/
    $ git clone -b noetic-devel https://github.com/ROBOTIS-GIT/turtlebot3_simulations.git
    $ cd ~/<your_dir>/catkin_ws && catkin_make
    ```
    Now you can test the installation with command: `$ roslaunch turtlebot3_gazebo turtlebot3_empty_world.launch`
3. Clone this repository in your ``<your_dir>/catkin_ws``.
    ```
    $ cd ~/<your_dir>/catkin_ws && git clone https://github.com/phatcvo/Motion-Planning-for-Mobile-Robot.git
    ```
4. Make modifications
  This Demo is based on old version of turtlebot3 open-source code. Therefore, some addition files are needed to run the demo.
    - remove `turtlebot3_simulations/turtlebot3_gazebo`:
      ```
      $ cd ~/<your_dir>/catkin_ws/src/turtlebot3_simulations && sudo rm -r turtlebot3_gazebo
      ```
    - Download ``turtlebot3`` dependencies: 
      ```
      $ cd ~/<your_dir>/catkin_ws/src && clone https://github.com/ROBOTIS-GIT/turtlebot3.git
      ```
5. Install packages
  - Install ROS related packages:
    - `$ sudo apt-get install ros-noetic-driver-base`
    - `$ sudo apt-get install ros-noetic-pol-ros`
    - `$ sudo apt-get install ros-noetic-tf2-sensor-msg`
  - Install libcurses5-dev`$ sudo apt-get install libcurses5-dev`
  - Install (update) basic packages: ``$ python -m pip install --user numpy scipy matplotlib``
  - Install pyclipper: ``$ pip install pyclipper`` (you may need `$ pip install --upgrade setuptools` if am error occures)
  - Install pykalman: ``$ pip install pykalman``
  - Install cvxopt: ``$ pip install cvxopt``
6. Build the packages: ``$ cd ~<your_dir>\catkin_ws && catkin_make``

## Run the example

Open a terminal, copy and run the following command.

```
$ roslaunch lidar_track turtlebot3_lidar_track_mode.launch
```

To change the goal of the robot, run

```
$ roslaunch demo_teleop turtlebot3_teleop_key.launch
```
## Reference

[Turtlebot3](https://emanual.robotis.com/docs/en/platform/turtlebot3/overview/#overview) motion planning in environment with moving obstacles. 
