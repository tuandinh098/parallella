# parallella playground

The aim is to create a one stop environment for parallella development

### References:

https://github.com/peteasa/parallella-yoctobuild - A Simple build environment for [Parallella](http://www.parallella.org/) using [Yocto](http://www.yoctoproject.org/)

https://github.com/parallella/parallella-hw.git - PARALLELLA: Supercomputing for Everyone - open source board and FPGA designs associated with the Parallella project.

https://github.com/analogdevicesinc/hdl - Analog Devices HDL libraries and projects

https://github.com/Xilinx/device-tree-xlnx.git - Xilinx device-tree tcl generation scripts used with the Xilinx SDK to generate a template device tree.

### Provides:

A working environment for a developer to take an idea from concept to working release on the Parallella platform.  The Xilinx tools are required to build the parallella fpga and a few build essentials are required for the Yocto Linux build, but after that the job of ensuring that the matching Linux, Analog Devices hdl, Open Hardware is provided by choosing the appropriate branch in this repository and checking out the matching submodules.


## Instructions

### Getting Started Guide

I realise there is a lot to take in with this project so I have create a [Getting Started Guide](https://github.com/peteasa/parallella/wiki/Getting-started) and [Quick Start](https://github.com/peteasa/parallella/wiki/Quick-start) list of instructions.  [Feedback is always welcome](https://parallella.org/forums/viewtopic.php?f=49&t=3180)

### Installing required packages for yocto

To use `yocto` you first need to install some packages. See latest [Yocto Project Quick Start](http://www.yoctoproject.org/docs/latest/yocto-project-qs/yocto-project-qs.html). This assumes you are working on a Ubuntu machine:

```bash
$ sudo apt-get install gawk wget git-core diffstat unzip texinfo gcc-multilib build-essential chrpath socat libsdl1.2-dev xterm
```

### Installing required software for Xilinx fpga development

To use the parallella template project `./parallella-fpga/7020_hdmi` you need to install Vivado 2014.4.1 see http://www.xilinx.com/support/download/index.html/content/xilinx/en/downloadNav/vivado-design-tools/2014-4.html, download 2014.4 (Design Suite version) and 2014.4.1 update (only works with the Design Suite version)

### Cloning this repository

Clone this repository onto your Linux build machine:
```bash
$ git clone git@github.com:peteasa/parallella
$ cd parallella
```

Checkout the branch that provides the versions that you want to use then to prepare the environment and download the necessary git submodules, you need to run the `initgitsubmodules.sh` script. This only needs to be done once:

```bash
$ source initgitsubmodules.sh
```

The result will be new folders `examples`, `parallella-fpga/parallella-hw`, `parallella-fpga/7020_hdmi`, `parallella-fpga/AdiHDLLib`, `parallella-yoctobuild`, `parallella-yoctobuild/poky`, `parallella-yoctobuild/meta-xilinx`, `parallella-yoctobuild/meta-parallella` and `parallella-yoctobuild/meta-epiphany` created from specific commits on github.

### Setting up your shell environment

For full instructions to setup the parallella-yoctobuild environment see https://github.com/peteasa/parallella-yoctobuild

For partial instructions to setup and use xilinx tools to build an fpga visit https://www.parallella.org/2015/03/23/new-parallella-elink-fpga-design-project-now-available-in-vivado/ but load my provided template (vivado 7020_hdmi/7020_hdmi.xpr) found in ./parallella-fpga/7020_hdmi.xpr

For instructions that need to be adapted to add more to the fpga be inspired by http://parallellagram.org/

### EXPERIMENTAL: Adding your own projects or modifying this environment

There are four folders in .gitignore that are ignored by this repository.  You can use these folder to store code for your own projects:

```bash
$ mkdir mywork
$ mkdir project
$ mkdir projects
$ mkdir test
```

There is a corresponding folder in the parallella-yoctobuild directory for the yocto changes that you might need to make for your project. And a corresponding folder in the parallella-fpga directory for your fpga project.  If you use these folders for your work then you dont need to modify any of the files I provide, making git updating easier (no conflicts or local checked out files).

You may need to clean the parallella-fpga project before you attempt to update.  As this will remove a lot of generated files please consider running 

```bash
cd parallella-fpga
git clean -d -n ./
```

and if happy with the changes that will be made

```bash
git clean -d -f ./
```

Before you run updatesubmodules.sh to update and get the latest versions of the git submodules.

These instructions are experimental at this time. 

### Links to other information

Yocto Troubleshooting notes - [Troubleshooting notes](https://github.com/peteasa/parallella-yoctobuild/wiki/Troubleshooting-notes)

Vivado Troubleshooting notes - TODO

Instructions for contributors - [Instructions for contributors](https://github.com/peteasa/parallella-yoctobuild/wiki/Instructions-for-contributors)


---------------------------------------

  * TODO instructions for building the examples
  * TODO oh yes need to add / create the examples!
  * TODO instructions for adding new parts from the Analog Devices libraries

