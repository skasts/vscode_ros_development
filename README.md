# VSCode ROS1 development
This repository has an example setup for VSCode to build and debug ROS code to be used in conjunction with the ROS extension for VSCode. See [these videos](https://www.youtube.com/watch?v=PBbEhRf8QjE&list=PL2dJBq8ig-vihvDVw-D5zAYOArTMIX0FA) for more explanation on how to use the VSCode ROS extension.

## Prerequisits
- Clone this repository with submodules to run the examples for debugging `git clone --recurse-submodules git@github.com:skasts/vscode_ros_development.git`
- Install VSCode ROS extension
- Always source workspace in the terminal where you run `code .`

## Building 
There is a build task to catkin build set up in `tasks.json`. 
- Build ROS code with `CTRL`+`SHIFT`+`b`

## Debugging
- Can **only** debug nodes that are started from a **launch file**
- You can **exclude nodes** from being debugged in launch.json

### Configurations

#### C++ and Python configuration
The debugger needs to know where to find your code. This information is stored in `c_cpp_properties.json` for C++ and in `settings.json` for Python. If you built your workspace and sourced it before opening VSCode, you can use functions of the ROS extension to update your debug configuration.
- Python: `ctrl`+`shift`+`p` -> ROS: Update Python path
- C++: `ctrl`+`shift`+`p` -> ROS: Update C++ Properties

#### Debug configuration
Run and debug configurations are stored in `launch.json`. You can automatically create a launch configuration for a ROS launch file using the ROS extension. Before, close all open files (if not, you won't see the ROS debug configuration template).
- *Run and Debug* from left panel
  - Create a launch.json file
  - ROS: Launch
  - Choose pkg
  - Choose launch file
- Add nodes from the launch file that you don't want to debug to the configuration in `launch.json`.

### Usage
- Set breakpoints in your code
- Press `F5` to launch your debug configuration. If you have multiple configurations, you can select one under *Run and Debug* from left panel
- If debugging multiple nodes: 
  - Debugging panel has a drop down menu to choose current node from
  - Each node gets an own debug terminal where you can see its output
- Use `F5` to continue (go until next breakpoint)
- Use `F10` to step to next line that gets executed

### Example configurations
- ROS: Debug single C++ Node (Talker)
- ROS: Debug Multiple C++ Nodes (Talker and Listener)
- ROS: Debug single Python Node (advanced Publisher)
- ROS: Debug Multiple Python Nodes (Talker and Listener)