# NTUA Operating Systems Laboratory (Spring Semester)

This repository contains my implementations and technical reports for the 4th-year Operating Systems Laboratory at the National Technical University of Athens.
Each lab focuses on core concepts of systems programming, Linux kernel development, and storage systems architecture.

### 1. The "Riddle" Challenge (Systems Programming & Unix Internals)
A multi-stage, sandboxed binary challenge designed to test deep knowledge of Unix systems programming and debugging utilities. 
*   **Concepts Covered:** System call tracing, process lifecycle management, signal handling, and Inter-Process Communication (IPC).
*   **Implementation Details:**
    *   Utilized low-level debugging tools (`strace`, `ltrace`, `/proc` filesystem analysis) to inspect execution states and binary behavior.
    *   Manipulated UNIX user/group permissions, dynamic environment variables, and file descriptors.
    *   Implemented asynchronous signal delivery (e.g., handling and overriding `SIGALRM`, `SIGUSR1`) and process synchronization.
    *   Constructed custom pipeline structures using Unix FIFOs (named pipes) to satisfy multi-process inter-communication constraints.

### 2. Lunix:TNG (Linux Kernel Character Device Driver)
Implementation of a fully functional Linux character device driver to process and expose data from an external wireless sensor network monitoring laboratory room metrics.
*   **Concepts Covered:** Kernel-space programming, device synchronization, concurrency, and user-to-kernel memory boundaries.
*   **Implementation Details:**
    *   Designed a dynamic Linux Kernel Module (LKM) capable of safely reading raw streams of sensory data (temperature, light levels, and battery voltage).
    *   Created corresponding virtual device nodes (`/dev/lunix*`) to bridge kernel-space buffering with user-space requests.
    *   Implemented concurrent access controls and blocking I/O (using wait queues and mutexes) to ensure thread-safe operation and prevent race conditions when queried by parallel user processes.

### 3. ext2-lite (Virtual Filesystem Engineering)
A lightweight, user-space virtual filesystem implementation conforming to a simplified version of the native **ext2** specification.
*   **Concepts Covered:** Disk storage layouts, layout structures, inode indexing, data blocks, and metadata management.
*   **Implementation Details:**
    *   Engineered custom C data structures to parse and map raw disk images, handling the superblock, block group descriptors, and inode allocation tables.
    *   Developed core filesystem operations including directory traversal, lookup mapping, and block allocation maps.
    *   Implemented standard read/write utilities capable of traversing directory trees and correctly reconstructing files block-by-block.

---

## 💻 Technical Stack

*   **Language:** C (POSIX compliant)
*   **Environment:** Linux (Debian under QEMU/KVM virtualization)
*   **Tools:** GCC, Make, GDB, Strace, Ltrace, etc.
