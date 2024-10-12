# Leaderless-KV-Store-using-Tempo
A distributed, fault-tolerant, persistent and sharded Key-Value store using leaderless state machine replication and consensus algorithm "Tempo""

## THIS PROJECT WAS PUSHED INTO PRIVATE REPO CREATED BY PROF. SHUAI MU (http://mpaxos.com/) AT STONY BROOK UNIVERSITY. WITH REPO BEING PRIVATE, IT CANNOT BE FORKED. PLEASE EMAIL ME AND THE PROFESSOR FOR ACCESS (STRICTLY FOR VIEWING PURPOSES). ATTACHED ARE THE SCREENSHOTS OF THE ORIGINAL PRIVATE REPO FOR REFERENCE. THANK YOU.

<img width="960" alt="image" src="https://github.com/user-attachments/assets/3962f0c9-0dd7-4b06-9dd0-8350c1c8f242">

<img width="960" alt="image" src="https://github.com/user-attachments/assets/15d702ac-1f4e-41a3-8f55-453078655116">

<img width="960" alt="image" src="https://github.com/user-attachments/assets/350b5a0d-246a-4619-82fc-92dd42ff2452">

<img width="960" alt="image" src="https://github.com/user-attachments/assets/dacf1137-f8fd-4ac4-abed-552533d2e455">

#  Distributed Systems Labs in C++

MIT 6.824 style distributed systems lab rebuilt in C++.
It includes a series of labs in which you will build a transactional, sharded, fault-tolerant key/value storage system (like Google Spanner, MongoDB, etc). 

## TEMPO – EFFICIENT REPLICATION VIA TIMESTAMP STABILITY

## BY - SHREYAS HABADE (STONY BROOK UNIVERSITY 115911132)


## Lab environment

A modern linux environment (e.g., Ubuntu 22.04) is recommended for the labs. If you do not have access to this, consider using a virtual machine. 

## Getting started (Ubuntu 22.04)

Get source code:
```
git clone --recursive [repo_address]
```

Install dependencies:
```
sudo apt-get update
sudo apt-get install -y \
    git \
    pkg-config \
    build-essential \
    clang \
    libapr1-dev libaprutil1-dev \
    libboost-all-dev \
    libyaml-cpp-dev \
    libjemalloc-dev \
    python3-dev \
    python3-pip \
    python3-wheel \
    python3-setuptools \
    libgoogle-perftools-dev
sudo pip3 install -r requirements.txt
```
#   Code Structure:
1.	The algorithm of the protocol is implemented in the same folder as the Raft.
2.	Implementation consists of functions of Receiving commands, Timestamp Proposal generation, Payload, Fast Path, Slow Path, Commit commands, Clock bump, checking TimeStamp Stability, Commands Execution, and Recovery Method.
3.	All the methods are implemented the same way Raft is.
4.	Commands are submitted to the server through the SendCommand function.
5.	Requirements are the same as Raft.
6.	Command to compile- python3 waf configure build --enable-raft-test
7.	Command to run- build/deptran_server -f config/tempo_lab_test.yml
8.	To run the algorithm, I’ve made a new “tempo_lab_test.yml” file.
9.	RPCs same as Raft are used for communication amongst servers.


#   How to run the code and the tests:
1.	After successful compilation of the code with the above command, the “build/deptran_server -f config/tempo_lab_test.yml” command runs the algorithm by calling the setup function and runs the test cases as well.
2.	Consecutive test cases check the correctness and performance of the code.

#	Test Cases:
1.	Seven test cases are written to test the code.
   - testTempo();
   - testTempoAfterDisconnectingServers();
   - testTempoSlowPath();
   - testTempoSlowPathAfterDisconnectingServers();
   - testTempoRecovery();
   - testTempoSlowPathFail();
   - testTempoBasicPersistence();
2.	These test cases test the Fast Path, Slow Path, Timestamp Stability, Ordered Execution, Recovery, Graceful Shutdown and Persistence, etc features of the algorithm in normal and failure conditions.
3.	Test cases are written in test.cc with modules in testconf.cc file.


#	Results:
1.	Fast Path is tested and works according to the paper.
2.	Slow Path is tested and works according to the paper when two commands are submitted to two servers concurrently (page 3 of the paper). It is tested and sends commands to two servers concurrently with threads.
3.	Recovery is tested and command is recovered when the coordinator fails before committing.


## Author and acknowledgements
- Author: Shuai Mu, Julie Lee
- Algorithm Code Written and Implemented by Shreyas Habade

Many of the lab structure and the guideline text are taken from MIT 6.824. The code is based on the acedemic prototypes of previous research works including Rococo/Janus/Snow/DRP/Rolis/DepFast.
