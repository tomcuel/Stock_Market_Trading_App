# 🧩 Test_Functionnalities

This directory gathers all **technical test modules** of the project.  
It allows validation of the main mechanisms — **multithreading, mutex control, password encryption, and socket communication** — **without being NRT** or tied to the final sources.

Each subfolder focuses on a specific technical functionality.

---

## 🧱 [Mutex](./Mutex)
Collection of mutex-based concurrency experiments.

### 🔹 [Engine_Mutex](./Mutex/Engine_Mutex)  
Tests the **core engine locking logic** (market + portfolio access and trades).  
Demonstrates `std::shared_mutex` and `std::mutex` cooperation between readers/writers.

### 🔹 [Improved_Mutex](./Mutex/Improved_Mutex)
Enhanced version introducing **fine-grained mutexes** for concurrent trading.  
Used to test **performance scaling** under multiple clients and symbols.

### 🔹 [Mutex_Interaction](./Mutex/Mutex_Interaction)
Explores **interactions between multiple mutexes**, focusing on **deadlock prevention** and proper lock ordering.

### 🔹 [Separated_Mutex](./Mutex/Separated_Mutex)
Validates **mutex isolation per object or subsystem** (client, portfolio, market).  
Ensures modularity and minimal contention between independent operations.

---

## 🔐 [Password_Cryptage](./Password_Cryptage)
Tests for password **hashing, salting, and verification mechanisms**.  
Ensures secure client authentication and consistent encryption/decryption flow.

---

## 🌐 [Socket](./Sockets)
Tests for socket-based communication between components. Each folder demonstrates different socket-level configurations.

### 🔹 [Launcher](./Sockets/Launcher)
Test **multi-client test launcher** in C++ that automatically runs several clients communicating with a central server.  
Used to verify **parallel socket connections**, **logging**, and **thread-safe message handling**.

### 🔹 [Multi_Thread](./Sockets/Multi_Thread)
Tests and demonstrations of **thread creation, synchronization, and shared data access**.  
Used to verify consistent output ordering, thread-safe updates, and thread lifecycle management.

### 🔹 [Socket_cpp_python](./Sockets/Socket_cpp_python) 
Hybrid test with a **C++ server** and a **Python client**.

### 🔹 [Socket_first](./Sockets/Socket_first)
Minimal example to verify **basic TCP send/receive** between one server and one client (text only).

### 🔹 [Socket_Network](./Sockets/Socket_Network)
Multi-client test setup with **networked message routing**, used to validate connection stability and concurrent handling.

### 🔹 [Socket_Network_cpp_python_Tkinter](./Sockets/Socket_Network_cpp_python_Tkinter)
Full pipeline test:  
**C++ trading server ↔ Python client ↔ Tkinter GUI**, verifying **live updates**, **GUI responsiveness**, and **cross-language socket consistency**.

---

## [SQL_in_cpp](./SQL_in_cpp)
Examples and tests showing **SQLite usage in native C++**. Useful for validating persistence and local storage integration for the future engine.

---

## 🧭 Purpose

These modules ensure each subsystem works correctly **in isolation** before integration into the final **NRT trading engine**.

Run them individually to validate:
- Thread and mutex correctness  
- Socket communication  
- SQL persistence & data integrity  
- Password encryption  
- System robustness under concurrent load
