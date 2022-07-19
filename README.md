# Triangle-Discovery-in-MultiLayered-Networks
This project regards triangle listing in graphs. More specifically, given a large set of relatively small graphs that correspond to the same set of nodes but in different time, the overall triangles are listed and sorted according to their frequency and the top-k triangles can be selected. Two datasets were analyzed containing 733 and 122 graphs, respectively and the algorithm that was implemented is Node Iterator. The project was contacted using the **Scala** programming language and the Apache **Spark** framework.


## Table of Contents

[0. Installation](https://github.com/vickypar/Triangle-Discovery-in-MultiLayered-Networks#0-installation)

[1. About](https://github.com/vickypar/Triangle-Discovery-in-MultiLayered-Networks#1-about)

[2. Data](https://github.com/vickypar/Triangle-Discovery-in-MultiLayered-Networks#2-data)

[3. Approach](https://github.com/vickypar/Triangle-Discovery-in-MultiLayered-Networks#3-approach)

[4. Results](https://github.com/vickypar/Triangle-Discovery-in-MultiLayered-Networks#4-results)


## 0. Installation 

The code requires Scala and the Apache Spark framework.

## 1. About

**Triangle Discovery in Multi-Layered Networks** is a project that was created as a semester Project in the context of “Mining from Massive Datasets” class.
MSc Data and Web Science, School of Informatics, Aristotle University of Thessaloniki.

## 2. Introduction

- Triangles in Graphs 
  - A group of three vertices that are connected to each other
  - {𝑢, 𝑣, 𝑤} ∈ 𝑉  form a triangle if {(𝑢, 𝑣), (𝑢, 𝑤), (𝑣, 𝑤)} ∈ 𝐸
  - Smallest nontrivial clique

![image](https://user-images.githubusercontent.com/95586847/179771791-7a56ac5a-9a54-4f4f-b10b-371e9cc9d311.png)
  
- Problem Definition - Triangle Listing
  - Given an undirected and unweighted graph G(V,E) over time
  - List all the triangles along with their frequency
  - Select top-k triangles

## 3. Data

The dataset was provided by the “Stanford Large Network Dataset Collection” which contains autonomous systems graphs, i.e., graphs of the Internet.
The two datasets that were analyzed along with some details about them are described in the following table.

![image](https://user-images.githubusercontent.com/95586847/179772411-2af1cc52-e1f1-42ba-bb39-39b4a8ede160.png)

- Each instance:
  - Given as a separate text file
  - Represents the evolution of the graph through time
  - Corresponds to the same set of nodes
  - Contains the edges that form the graph

- Example:

Graph - Instance             |  Text File
:-------------------------:|:-------------------------:
![image](https://user-images.githubusercontent.com/95586847/179773704-baf79b7f-0ded-461b-aa1c-ba6c11f82bef.png)  |  ![image](https://user-images.githubusercontent.com/95586847/179773782-f1f716c8-5d7c-4bf8-a082-2f9f04217c34.png)


## 4. Approach

### 4.1 Preprocessing
- Load the files while keeping the file name and removing unwanted staff
- Convert it into a dataframe
- Transform the columns of the dataframe into the desired form of (filename, src, dest)
- Concatenate source and destination as (src, dest)
- Group-by file name and aggregate pairs as a list 
- Change the file number with its index number
- Store the final dataframe in a csv file

![image](https://user-images.githubusercontent.com/95586847/179775454-a13d9c7f-1896-4ee5-b364-5cfea6d68ec5.png)

### 4.2 Node Iterator Algorithm



## 5. Results
The experiments were run using a virtual machine on an AMD Ryzen 7 5800H processor with 16GB RAM and the top-10 triangles found at each dataset are presented in the following tables along with their fre-quencies.

Dataset: as-733             |  Dataset: as-Caida
:-------------------------:|:-------------------------:
![image](https://user-images.githubusercontent.com/95586847/179765092-c5f3d896-1e1d-41fb-8e41-e7b69a14caeb.png)  |  ![image](https://user-images.githubusercontent.com/95586847/179765458-edbe3221-d054-4146-8971-9351bcb641c0.png)

The time needed to preprocess the data and list the triangles is depicted in the figures that follow for a different number of cores. Both figures show that the solution is scalable since when more cores are uti-lized, less time is needed.


Dataset: as-733             |  Dataset: as-Caida
:-------------------------:|:-------------------------:
![image](https://user-images.githubusercontent.com/95586847/179766817-2a8736f4-5e52-4c45-8492-125655b2d7ba.png)  |  ![image](https://user-images.githubusercontent.com/95586847/179766872-a4f19fe9-5886-4139-a897-9dac720bcd4e.png)


