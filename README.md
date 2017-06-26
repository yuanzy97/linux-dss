# OpenDSS for Linux

OpenDSS is an electric power Distribution System Simulator (DSS) for supporting distributed resource integration and grid modernisation efforts.

As explained in the background section, the original OpenDSS package ships with a Dynamic Linked Library (DLL) that allowing the user to interface with the solver via COM Server. However, this was limited to Windows.

This repository provides a procedure to acquire and compile a Linux (here Ubuntu 16.04) compatible shared object library, which is used in a sample `PyDSS` module.

## Usage

If you already have lazarus and Free Pascal installed, you may skip the setup.

### Setup

Start by installing all prerequisites, including the standard compiler and lazarus (with Free Pascal). Also two additional symbolic links need to be added for the compilation to function correctly.

```
sudo apt-get update
sudo apt-get upgrade
sudo apt-get install build-essential lazarus subversion
```

### Compile

Fully compile the library using:

```
make
```

This will save the final `libopendssdirect.so` in the `lib` directory, and a full copy of the OpenDSS source is stored in `electricdss`. If you want the OpenDSS source saved somewhere else, you can build like so:

```
make OPENDSS_DIR=some_other_dir
```

## Background

The Open Distribution System Simulator (OpenDSS, or simply, DSS) is a comprehensive electrical system simulation tool for electric utility distribution systems. OpenDSS technically refers to the open-source implementation of the DSS. It is implemented as both a stand-alone executable program and a COM DLL designed to be driven from a variety of existing software platforms. The executable version adds a basic user interface on to the solution engine to assist users in developing scripts and viewing solutions.

The program basically supports all rms steady-state (i.e., frequency domain) analyses commonly performed for utility distribution systems. In addition, it supports many new types of analyses that are designed to meet future needs, many of which are being dictated by the deregulation of US utilities and the formation of distribution companies worldwide. Many of the features found in the program were originally intended to support distributed generation analysis needs. Other features support energy efficiency analysis of power delivery and harmonics analysis. The DSS is designed to be indefinitely expandable so that it can be easily modified to meet future needs.

The OpenDSS program has been used for:



Through the COM interface, the user is able to add other solution modes and features externally and perform the functions of the simulator, including definition of the model data. Thus, the DSS could be implemented entirely independently of any database or fixed text file circuit definition. For example, it can be driven entirely from a MS Office tool through VBA, or from any other 3rd party analysis program that can handle COM. Users commonly drive the OpenDSS with the familiar Mathworks MATLAB program. This provides powerful external analytical capabilities as well as excellent graphics for displaying results.


The COM interface also provides direct access to the text-based command interface as well as numerous methods and properties for accessing many of the parameters and functions of the simulator's models. Through the command interface, user-written programs can generate scripts to do several desired functions in sequence. The input may be redirected to a text file to accomplish the same effect as macros and also provide some database-like characteristics. Many of the results can be retrieved through the COM interface as well as from various output files. Output files are typically written in Comma-separated Value (CSV) format that imports easily into other tools for post processing.

