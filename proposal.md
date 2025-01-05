# Systems Final Project: 
## Group members: Ashley Zhu, Kellen Yu
## Overview
A multithreaded iterative FDM solver for the heat equation. 

## Technical Design:
Using the Finite Difference Method, we will simulate how heat dissipates through a space over a certain time interval. In order to achieve a high level of accuracy, the resolution of the grid must be very high and the individual time steps must be very small. This is a very computationally expensive process, one we hope to expedite through parallel processing techniques. 

A .csv file describing the initial conditions of the space is read by our solver. Then 2 multi-dimensional arrays are allocated in shared memory, one for the conditions regarding the current time step and the other for the updated conditions regarding the next time step. After each successful time step, the updated conditions are saved to a separate file, and then overwritten to the current time step array. This process is repeated until the end of the specified time interval is reached. 

Each child will have access to both shared memory arrays. To make sure that no child reads the same address at the same time, we will use semaphores pertaining to certain portions of the array. 

If possible, we plan to create a python visualizer that uses matplotlib or similar graphics libraries to visually represent the data. We also hope to create a tool that makes the process of setting up initial conditions easier, possibly letting 3D models to be taken in, or simpler geometries. 

### Quick breakdown of concepts incorporated into this project
- Memory Allocation
- File I/O
- Process Management (fork, exec)
- Shared Memory
- Semaphores

## Breakdown of work
### MVP
Kellen: File I/O functions and handlers
Ashley: Shared memory management + Semaphores
Kellen: Sub-process creation and management functions
Ashley: FDM Calculation functions

### Extra
Kellen: Visualization tool
Ashley: Initial setup tools

## User Interface: 
	The user will be prompted to input a time interval, the number of intervals they would like to stimulate, and a resolution. From this, a new data file will be created with the temperature updates for the additional intervals. 

## Timeline
- [ ] 1/6 : Initial Proposal
- [ ] 1/8: FDM Calculation functions and File I/O functions complete
- [ ] 1/11: Shared memory management and Sub-process management complete
- [ ] 1/12: Testing examples completed
- [ ] 1/13: MVP completed
- [ ] 1/15: Visualization tool complete and set up tool complete
- [ ] 1/18: Visualization animation tool. 
- [ ] 1/20: Video completed 

