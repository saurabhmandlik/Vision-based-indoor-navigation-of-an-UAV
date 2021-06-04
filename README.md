
# Indoor non-GPS Autonomous Navigation of UAV using AprilTag Marker 

This repository explains the autonomous navigation and position of drone in indoor environment. Here, I have used Intel RealSense camera to navigate the UAV using AprilTag marker. 

### Required Set-up

#### Software and Dependencies to be needed

    1. Ubuntu 18.04
    2. ROS Melodic
    3. Mission Planner
    4. RViz
    5. vision_to_mavros ROS packages
    6. TensorFlow 
    7. Python 2.7
    
    
#### Hardware used

    1. Raspberry Pi 4
    2. Intel RealSense Camera
    3. Raspberry Pi camera V2.0
    4. UAV
    5. PixHawk 4
    6. RC transmitter
    7. 4500 mAh LiPo Battery
    8. StromPi and Battery module
    

#### The repository is divided into two parts:
    1. Detect the predetermined object using computer vision approach
    2. Autonomously navigate UAV using marker
    

### 2. Autonomously Navigate the UAV using AprilTag marker:

Few things we have to understand to get into this topic.

#### A. MAVROS  (http://wiki.ros.org/mavros)
MAVROS is a ROS package that enables MAVLink extendable communication between computers runnig ROS for any ground station. It's officially bridge between ROS and ArduPilot by translating ROS topics into MAVLink messages.

##### Features of MAVROS

    -Communication with autopilot via serial port, UDP or TCP (e.g. PX4 Pro or ArduPilot)
    -Plugin system for ROS-MAVLink translation
    -Parameter manipulation tool
    -Waypoint manipulation tool
    -PX4Flow support (by mavros_extras)
    -OFFBOARD mode support
    -Geographic coordinates conversions.

##### MAVROS Installation

    sudo apt-get install python-catkin-tools python-rosinstall-generator -y
     
    mkdir -p ~/catkin_ws/src
    cd ~/catkin_ws
    catkin init
    wstool init src


    rosinstall_generator --rosdistro melodic mavlink | tee /tmp/mavros.rosinstall

    rosinstall_generator --upstream mavros | tee -a /tmp/mavros.rosinstall

    wstool merge -t src /tmp/mavros.rosinstall
    wstool update -t src -j4
    rosdep install --from-paths src --ignore-src -y

    ./src/mavros/mavros/scripts/install_geographiclib_datasets.sh
    
    catkin build
    source devel/setup.bash
    
#### Pixhawk FCU
Pixhawk is a flight controller unit that is used for many applications of multicopters, rovers etc.  It offers a wide variety of flight modes from fully manual to fully autonomous. As part of the wider ArduPilot software platform it works seamlessly with a variety of Ground Control Station programs that are used to setup the vehicle, monitor the vehicle’s flight in real-time and perform powerful mission planning activities.
For this project, I have used Pixhawk 4 FCU.

![image](https://user-images.githubusercontent.com/67440191/120722181-a1fe3d00-c4cf-11eb-9db3-75c651216857.png)




### Hardware Setup
Connect Pixhawk FCU to LiPo battery. 
connect FCU to on board computer raspberry pi through USB Port of FCU. 
Connect realsense camera to raspberry pi 4.





