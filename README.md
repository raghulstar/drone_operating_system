# Drone Operating System

## Overview

This project simulates a basic operating system for a drone (Unmanned Aerial Vehicle) with navigation commands such as takeoff, survey, return to home, land, and failure. It includes mission planning using a graph-based shortest path algorithm to navigate from one location to another.

## Classes and Methods

### DroneOperation (Base Class)

Abstract base class defining the interface for all drone operations.
- `virtual void execute() = 0;`
- **Polymorphism:** This class uses polymorphism to allow derived classes to implement specific commands.

### Takeoff (Derived Class)

Represents the takeoff operation.
- `void execute() override;` - Outputs a message indicating the drone is taking off.

### Land (Derived Class)

Represents the landing operation.
- `void execute() override;` - Outputs a message indicating the drone is landing.

### ReturnToHome (Derived Class)

Represents the return to home operation.
- `void execute() override;` - Outputs a message indicating the drone is returning to home.

### Failure (Derived Class)

Represents a failure in the drone's operation.
- `void execute() override;` - Outputs a message indicating the drone operation has failed.

### MissionPlanning

Handles mission planning using Dijkstra's algorithm.
- `MissionPlanning(int nodes);` - Initializes the graph with nodes and random weights.
- `vector<int> dijkstra(int src, int dest);` - Finds the shortest path from source to destination.
- **Optimal Graph Search Algorithm:** Dijkstra's algorithm is used because it efficiently finds the shortest path in graphs with non-negative weights.

### Survey

Handles the surveying operation.
- `void execute(const vector<int>& path);` - Outputs the path to survey.

## Main Function

Demonstrates the workflow:
1. Initializes mission planning with 100 nodes.
2. Finds the shortest path from node 0 to node 99.
3. Executes takeoff, survey, return to home, and land operations.

## Optimal Graph Search Algorithm

Dijkstra's algorithm is used for finding the shortest path due to its efficiency and suitability for graphs with non-negative weights.

## Multi-threaded Operations

The code uses multi-threading to handle DroneOperations, MissionPlanning, and Survey operations to speed up the process:
- Each operation (takeoff, survey, return to home, and land) is executed in a separate thread.

## Simulation of Scenarios

The code simulates both best and worst-case scenarios:
- **Best-case scenario:** The shortest path is found and executed without any failures.
- **Worst-case scenario:** A failure operation is included to simulate an error in the drone's operation.


