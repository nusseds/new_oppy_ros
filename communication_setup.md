# Setting up WDS bridging
- The router connected to the base station will be used as the master router. The other router is the client router.
- WDS briding should be enabled on the client router so that it is connected to the SSID of the master router.
- DHCP should be disabled on the client router.
- Assign static IP to Jetson and basestation.
- Testing can be done to see if the bi-directional connection is established between the jetson and the base station:
  - ping base_station_ip.
  - netcat:
    - Listen on one computer: nc -l port_number.
    - On the other computer: nc -p port_number ip_of_the_listened_computer.
    - Characters typed in one computer should be echoed on the other computer.
    
# Configuring environment variables and hosts
- Setting up ROS_IP environment variable on both Jetson and basestation: export ROS_IP=their_respective_ip.
- roscore will be run on Jetson, modify /etc/hosts on the basestation to map the address of Jetson to its hostname.
- Setting up ROS_MASTER_URI environment variable on the basestation: export ROS_MASTER_URI="http://jetson_host_name:roscore_port"
- Testing the ros connection:
  - Run roscore on Jetson.
  - Publish topic on either computer then try to echo the same topic on the other computer.
