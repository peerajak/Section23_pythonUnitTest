# Section23_pythonUnitTest



## rotate_robot_test_ros.py

```
rosrun robot_control rotate_robot_test_ros.py
```

## rotate_robot_srv.py

Terminal 1

```
rosrun robot_control rotate_robot_srv.py
```

Terminal 2

```
rosservice call /rotate_robot [TAB][TAB]
```

for example

```
rosservice call /rotate_robot "speed_d: 90.0
angle_d: 90.0
clockwise_yn: 'y'"
```

### rotate_robot_test_ros_srv.py

Terminal 1

```
rosrun robot_control rotate_robot_srv.py
```

Terminal 2

```
rosrun robot_control rotate_robot_test_ros_srv.py
```

## Rostest

file name rotate_robot_test_ros_srv.test

call rostest like this got error 

```
rostest robot_control rotate_robot_test_ros_srv.test
```

need to add  --reuse-master to handle ROS_MASTER_URI thingy

The correct way to call rostest

```
rostest robot_control rotate_robot_test_ros_srv.test --reuse-master
```

## Conclusion

To do service node testing, we first create a service node "rotate_robot_srv.py" and test working the service node with CLI service client call

```
rosrun robot_control rotate_robot_srv.py
```

```
rosservice call /rotate_robot "speed_d: 90.0
angle_d: 90.0
clockwise_yn: 'y'"
```

```
rosrun robot_control rotate_robot_test_ros_srv.py
```


The unit test script starts with "rotate_robot_test_ros_srv.py". 
After unit test script done, create test "launch file like" with rostest "rotate_robot_test_ros_srv.test"