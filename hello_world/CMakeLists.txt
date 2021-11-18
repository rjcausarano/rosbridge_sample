cmake_minimum_required(VERSION 3.1)
project(hello_world)

find_package(catkin REQUIRED COMPONENTS
  roscpp
  std_msgs)

include_directories(${catkin_INCLUDE_DIRS})

catkin_package(
  INCLUDE_DIRS
  CATKIN_DEPENDS roscpp std_msgs
  DEPENDS
)

add_executable(talker src/talker.cpp)
target_link_libraries(talker ${catkin_LIBRARIES})

add_executable(listener src/listener.cpp)
target_link_libraries(listener ${catkin_LIBRARIES})

install(TARGETS
  talker
  listener
  RUNTIME DESTINATION ${CATKIN_PACKAGE_BIN_DESTINATION})