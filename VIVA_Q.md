# OS VIVA Questions & Answers

**OS Module 1: Introduction & OS Structure**

1.  **What is an operating system?**
    An operating system (OS) is system software that manages computer hardware and software resources and provides common services for computer programs. It acts as an intermediary between the user and the hardware.
2.  **Why is an operating system necessary?**
    An OS is necessary to manage complex hardware resources efficiently, provide a convenient interface for users and applications, and ensure the system operates correctly and securely.
3.  **What are the main objectives of an operating system?**
    The main objectives are convenience (making the computer easy to use), efficiency (managing resources optimally), and the ability to evolve (allowing new features without disrupting service).
4.  **List and explain the main functions of an operating system.**
    Main functions include process management, memory management, file system management, I/O device management, networking, and security/protection.
5.  **How does the OS manage hardware and software resources?**
    The OS manages resources by allocating them (CPU time, memory, devices) to various processes, scheduling their use, and reclaiming them when no longer needed, often using abstractions.
6.  **What do you mean by "Resource Allocation" in OS?**
    Resource allocation is the process by which the OS assigns available system resources (like CPU cycles, memory space, I/O devices) to competing processes or users according to a scheduling policy.
7.  **What is the difference between a system program and an application program?**
    System programs aid the operation and management of the computer system itself (e.g., compilers, loaders, shells), while application programs perform specific tasks for the end-user (e.g., word processors, browsers).
8.  **What is an OS structure and why is it important?**
    OS structure refers to the way the OS components are organized (e.g., monolithic, layered, microkernel). It's important because it impacts the system's design, implementation, maintainability, efficiency, and reliability.
9.  **Explain the Layered architecture of an operating system with an example.**
    In a layered architecture, the OS is divided into layers, each built upon the services of the one below it (e.g., THE OS). This modularizes the design but can have performance overhead.
10. **What are the advantages and disadvantages of the layered approach?**
    Advantages include modularity, easier debugging, and verification. Disadvantages include potential performance loss due to layer overhead and difficulty in defining the layers appropriately.
11. **What is a Monolithic kernel? Give an example.**
    A monolithic kernel is an architecture where most OS services (scheduling, file system, memory management) run in a single kernel address space. Examples include traditional Unix and Linux.
12. **How does a Monolithic kernel differ from a Microkernel?**
    Monolithic kernels integrate most services into the kernel space, whereas microkernels keep only essential services (like IPC, basic scheduling) in the kernel, running other services as user-space processes.
13. **Define a Microkernel. What are its advantages?**
    A microkernel provides only fundamental OS services in kernel mode, with other services running in user mode. Advantages include better reliability, security, and flexibility.
14. **What is the Linux kernel? What role does it play in the OS?**
    The Linux kernel is the core component of the Linux OS, responsible for managing hardware resources, scheduling processes, managing memory, and providing essential system services.
15. **What is a Shell in Linux?**
    A Shell is a command-line interpreter in Linux that acts as an interface between the user and the kernel, executing commands entered by the user.
16. **Name different types of Linux shells.**
    Common Linux shells include bash (Bourne Again SHell), sh (Bourne Shell), csh (C Shell), ksh (Korn Shell), and zsh (Z Shell).
17. **What are the responsibilities of the Shell?**
    The Shell interprets user commands, executes programs, manages input/output redirection, handles environment variables, and supports scripting for automation.
18. **How does the Shell communicate with the Kernel?**
    The Shell communicates with the Kernel primarily by making system calls to request kernel services, such as creating processes (`fork`, `exec`) or managing files (`open`, `read`).
19. **What are System Calls?**
    System calls are the interface through which user-level processes request services directly from the operating system kernel, such as I/O operations or process management.
20. **How are System Calls used in Linux?**
    In Linux, system calls are typically invoked via wrapper functions in standard libraries (like glibc), which handle the low-level details of trapping into kernel mode to execute the requested service.

**OS Module 2: Processes, Threads, Scheduling**

21. **What is a process in an operating system?**
    A process is an instance of a computer program that is being executed, containing the program code and its current activity (state, resources, etc.).
22. **How is a process different from a program?**
    A program is a passive set of instructions stored on disk, while a process is an active entity representing the execution of that program with its own state and resources.
23. **What are the different states of a process?**
    Common process states include New (being created), Ready (waiting for CPU), Running (executing), Waiting/Blocked (waiting for an event), and Terminated (finished execution).
24. **Explain the Process Life Cycle with a state diagram.**
    The Process Life Cycle involves transitions between states (New -> Ready -> Running <-> Waiting -> Terminated) triggered by events like scheduling, I/O requests, or completion. *(A diagram would visually show these states and transitions).*
25. **What is a Process Control Block (PCB)?**
    A Process Control Block (PCB) is a data structure maintained by the OS for every process, containing all the information needed to manage that process.
26. **What kind of information is stored in a PCB?**
    A PCB stores process state, process ID, program counter, CPU registers, memory management information, accounting data, and I/O status information.
27. **Why is the PCB important for context switching?**
    The PCB is crucial for context switching as it holds the entire execution context (state, registers, etc.) of a process, allowing the OS to save one process's state and restore another's.
28. **What is context switching and when does it occur?**
    Context switching is the process of saving the state of the currently running process and loading the state of another process. It occurs when the OS changes the process using the CPU, typically due to interrupts, system calls, or scheduler decisions.
29. **What is the difference between a process and a thread?**
    A process has its own address space and resources, while threads are units of execution within a process that share the process's address space and resources, making them lighter weight.
30. **What causes a process to transition from one state to another?**
    Transitions are caused by events such as scheduler dispatch (Ready->Running), I/O requests (Running->Waiting), I/O completion (Waiting->Ready), or process termination (Running->Terminated).
31. **What is CPU scheduling?**
    CPU scheduling is the act of selecting a process from the ready queue to be executed on the CPU when the CPU becomes idle.
32. **What is the purpose of a scheduler in OS?**
    The purpose of a scheduler is to allocate CPU time among competing processes efficiently, maximizing CPU utilization, minimizing wait times, and ensuring fairness.
33. **What is the difference between preemptive and non-preemptive scheduling?**
    Preemptive scheduling allows the OS to forcibly stop a running process to allocate the CPU to another (e.g., based on time slice or priority), while non-preemptive scheduling requires a process to voluntarily release the CPU.
34. **Explain First-Come, First-Served (FCFS) scheduling.**
    FCFS is a non-preemptive scheduling algorithm where processes are allocated the CPU in the order they arrive in the ready queue.
35. **What are the pros and cons of FCFS?**
    Pro: Simple to implement and understand. Con: Can result in high average waiting times, susceptible to the convoy effect (short processes stuck behind long ones).
36. **Explain Shortest Job First (SJF) scheduling.**
    SJF selects the process with the shortest estimated next CPU burst time for execution next; it can be preemptive (SRTN) or non-preemptive.
37. **Differentiate between SJF and Shortest Remaining Time Next (SRTN).**
    SJF is typically non-preemptive, selecting the shortest job and running it to completion/block. SRTN is the preemptive version, potentially switching to a new shorter job if its remaining time is less than the current job's remaining time.
38. **Which scheduling algorithm gives minimum average waiting time?**
    Shortest Job First (SJF), particularly its preemptive version (SRTN), provably gives the minimum average waiting time for a given set of processes.
39. **What is Round Robin (RR) scheduling? How is time quantum selected?**
    RR is a preemptive algorithm where each process gets a small unit of CPU time (time quantum); if not finished, it goes to the end of the ready queue. The quantum size balances responsiveness and context-switch overhead.
40. **What is Priority Scheduling?**
    Priority Scheduling assigns a priority level to each process, and the CPU is allocated to the process with the highest priority (can be preemptive or non-preemptive).
41. **What are the types of priority scheduling? (Preemptive and Non-preemptive)**
    Non-preemptive priority scheduling runs the selected highest-priority process until it blocks or finishes. Preemptive priority scheduling allows a higher-priority process to interrupt a running lower-priority process.
42. **How does starvation occur in priority scheduling?**
    Starvation can occur if low-priority processes are perpetually denied CPU time because higher-priority processes keep arriving. Aging can be used to mitigate this.
43. **Which algorithms are preemptive? Which are non-preemptive?**
    Preemptive examples: SRTN, Round Robin, Preemptive Priority. Non-preemptive examples: FCFS, Non-preemptive SJF, Non-preemptive Priority.
44. **How is turnaround time, waiting time, and response time calculated?**
    Turnaround Time = Completion Time - Arrival Time. Waiting Time = Turnaround Time - Burst Time. Response Time = Time of First CPU Allocation - Arrival Time.
45. **What is a thread?**
    A thread is the basic unit of CPU utilization within a process; it comprises a thread ID, program counter, register set, and stack, sharing code and data sections with other threads in the same process.
46. **How is a thread different from a process?**
    Threads share the same address space and resources of their parent process, making creation and context switching faster than for processes, which have separate address spaces.
47. **What are the types of threads? (User-level and Kernel-level)**
    User-level threads are managed by a user-level library without kernel support, while kernel-level threads are managed directly by the operating system.
48. **What is multithreading?**
    Multithreading is the ability of a process to manage multiple threads of execution concurrently, allowing different parts of the program to run seemingly simultaneously.
49. **What are the benefits of multithreading?**
    Benefits include increased responsiveness, efficient resource sharing between threads, economy (cheaper than creating processes), and better utilization of multiprocessor architectures (scalability).
50. **What are the challenges of using multithreading?**
    Challenges include the complexity of synchronization to avoid race conditions, potential for deadlocks, difficulty in debugging concurrent execution, and managing shared data correctly.
51. **Can multiple threads of the same process run simultaneously?**
    Yes, on a multi-core or multi-processor system, multiple threads from the same process can execute in parallel on different cores. On a single core, they run concurrently (interleaved).
52. **What is the impact of multithreading on CPU utilization?**
    Multithreading generally improves CPU utilization, especially on multi-core systems, as one thread can run while another is blocked (e.g., waiting for I/O).
53. **How does a thread share resources with other threads?**
    Threads within the same process share the process's code section, data section, heap memory, and open files/OS resources. Each thread has its own private stack and registers.

**OS Module 3: Concurrency, Synchronization, Deadlocks**

54. **What is concurrency in operating systems?**
    Concurrency is the execution of multiple instruction sequences seemingly at the same time, managed by the OS through interleaving processes/threads on a single CPU or true parallelism on multiple CPUs.
55. **How is concurrency different from parallelism?**
    Concurrency deals with managing multiple tasks making progress over time (can be interleaved on one core), while parallelism involves tasks executing simultaneously (requires multiple cores).
56. **What is inter-process communication (IPC)?**
    IPC refers to mechanisms provided by the OS that allow different processes to communicate with each other and synchronize their actions (e.g., shared memory, message passing).
57. **Name different IPC mechanisms.**
    Common IPC mechanisms include pipes, FIFOs (named pipes), message queues, shared memory, semaphores, mutexes, signals, and sockets.
58. **What is process synchronization and why is it needed?**
    Process synchronization is the coordination of concurrent processes accessing shared resources or data. It's needed to prevent race conditions and ensure data consistency.
59. **What problems can arise due to lack of synchronization?**
    Lack of synchronization can lead to race conditions, inconsistent data, incorrect program results, and potential deadlocks or livelocks.
60. **What is the critical section problem?**
    The critical section problem is designing a protocol to ensure that when one process is executing code that accesses shared resources (its critical section), no other process can execute in its critical section concurrently.
61. **What is mutual exclusion in process synchronization?**
    Mutual exclusion is a property ensuring that no two processes can be in their critical section at the same time, which is a fundamental requirement for solving the critical section problem.
62. **What are the requirements for mutual exclusion?**
    The requirements are: 1) Mutual Exclusion (only one process in CS), 2) Progress (decision on next process not postponed indefinitely), and 3) Bounded Waiting (limit on how many times others enter before a waiting process).
63. **Explain hardware support for mutual exclusion – what is a Test and Set Lock (TSL) instruction?**
    Hardware support includes atomic instructions like TSL, which reads the value of a memory word (lock) and sets it to a non-zero value in a single, indivisible operation, returning the original value.
64. **Why is hardware-based synchronization not always preferred?**
    Hardware solutions often involve busy waiting (wasting CPU cycles spinning on a lock) and might not scale well or provide convenient high-level synchronization abstractions.
65. **What is a semaphore?**
    A semaphore is a synchronization variable accessed only through two atomic operations, `wait()` (P) and `signal()` (V), used to control access to shared resources or coordinate processes.
66. **Explain the two types of semaphores: binary and counting.**
    A binary semaphore (mutex) has values 0 or 1, used for mutual exclusion. A counting semaphore has non-negative integer values, used to control access to a resource with multiple instances.
67. **How do wait() and signal() work in semaphores?**
    `wait(S)` decrements semaphore S; if S becomes negative, the process blocks. `signal(S)` increments S; if processes were waiting (S<=0 before increment), it wakes one up. Both are atomic.
68. **What is the Producer-Consumer problem?**
    It's a classic synchronization problem where producer processes generate data and put it into a shared buffer, while consumer processes remove data from the buffer, requiring coordination to avoid conflicts.
69. **How can semaphores solve the Producer-Consumer problem?**
    Semaphores solve it using a mutex for buffer access, a counting semaphore `empty` (tracking empty slots), and a counting semaphore `full` (tracking filled slots) to synchronize producers and consumers.
70. **What is a deadlock?**
    A deadlock is a situation where a set of processes are blocked because each process is holding a resource and waiting for another resource acquired by another process in the set.
71. **What are the four necessary conditions for deadlock?**
    The conditions are: Mutual Exclusion (non-sharable resources), Hold and Wait (holding resources while waiting for more), No Preemption (resources released voluntarily), and Circular Wait (a cycle of processes waiting).
72. **Explain each of these conditions with an example.**
    Mutual Exclusion: Printer used by one process at a time. Hold and Wait: Process holds File A, waits for File B held by another process. No Preemption: OS cannot take File A away. Circular Wait: P1 waits for P2's resource, P2 waits for P1's.
73. **What is a resource allocation graph (RAG)?**
    A RAG is a directed graph representing the state of resource allocations, with nodes for processes and resources, and edges showing requests (P->R) and assignments (R->P).
74. **How can a RAG help detect a deadlock?**
    A cycle in the RAG is a necessary condition for deadlock; if each resource type has only one instance, a cycle indicates a definite deadlock.
75. **What is the difference between a safe and an unsafe state?**
    A state is safe if the system can allocate resources to each process (up to its maximum) in some order and still avoid deadlock. An unsafe state *may* lead to deadlock.
76. **What are the methods of handling deadlocks?**
    Methods include: Deadlock Prevention (ensure one condition never holds), Deadlock Avoidance (use algorithms like Banker's to stay safe), Deadlock Detection and Recovery, or Ignoring the problem.
77. **How does deadlock prevention work?**
    Prevention works by imposing constraints that negate one of the four necessary conditions for deadlock, such as requiring processes to request all resources at once (denying Hold and Wait).
78. **Give examples of how each of the 4 conditions can be denied.**
    Mutex: Make resources sharable (not always possible). Hold/Wait: Request all resources initially. No Preemption: Allow resource preemption. Circular Wait: Impose resource ordering.
79. **What is deadlock avoidance?**
    Deadlock avoidance dynamically checks the resource allocation state to ensure a safe state is always maintained, typically requiring prior knowledge of maximum resource needs (e.g., Banker's Algorithm).
80. **Explain Banker's Algorithm with an example.**
    Banker's Algorithm checks if granting a resource request keeps the system in a safe state by simulating whether a sequence exists for all processes to finish given current and maximum needs. *(An example requires showing allocation/need matrices).*
81. **What are the inputs required for Banker's Algorithm?**
    Inputs are the number of processes/resources, currently available resources (`Available`), maximum resource needs per process (`Max`), and current allocation per process (`Allocation`).
82. **How does deadlock detection work?**
    Detection algorithms periodically check the system state (e.g., using a wait-for graph derived from the RAG) to see if a deadlock cycle exists among the processes.
83. **Once a deadlock is detected, how can the system recover?**
    Recovery involves either terminating one or more deadlocked processes or preempting resources from some deadlocked processes to break the cycle.
84. **What are the pros and cons of deadlock detection and recovery?**
    Pros: Allows potentially better resource utilization than prevention/avoidance. Cons: Overhead of detection algorithm, complexity and potential data loss during recovery.
85. **Explain the Dining Philosophers Problem.**
    It's a classic concurrency problem illustrating deadlock and starvation, where five philosophers need two chopsticks (shared resources) to eat, but acquiring them incorrectly can lead to a circular wait.
86. **How does this problem relate to synchronization and deadlocks?**
    It models resource allocation (chopsticks) where mutual exclusion is needed, highlighting how improper synchronization can lead to deadlock (circular wait) or starvation.
87. **Suggest at least one solution to the Dining Philosophers Problem.**
    Solutions include using a semaphore/monitor to ensure a philosopher picks up both chopsticks atomically, or allowing only four philosophers at the table simultaneously, or using an asymmetric pickup order.

**OS Module 4: Memory Management**

88. **What is memory management in an operating system?**
    Memory management is the OS function responsible for allocating main memory (RAM) to processes, keeping track of memory usage, and deallocating it when processes terminate.
89. **What are the main requirements of memory management?**
    Requirements include relocation (running processes anywhere), protection (preventing interference), sharing (allowing shared memory), logical organization (supporting program structure), and physical organization (mapping to hardware).
90. **What is the difference between logical and physical addresses?**
    A logical address is generated by the CPU and refers to a location within the process's virtual address space. A physical address is the actual location in the main memory hardware.
91. **What is memory partitioning?**
    Memory partitioning is dividing the main memory into sections (partitions) to hold multiple processes simultaneously. It can be fixed or dynamic.
92. **Explain fixed partitioning. What are its limitations?**
    Fixed partitioning divides memory into fixed-size partitions at boot time. Limitations include internal fragmentation (wasted space within partitions) and limits on process size.
93. **What is dynamic partitioning?**
    Dynamic partitioning allocates partitions of variable sizes specifically tailored to each incoming process, leading to holes of free memory between partitions.
94. **What is external fragmentation and internal fragmentation?**
    External fragmentation exists when total free memory is sufficient but scattered in non-contiguous blocks. Internal fragmentation is wasted space *within* an allocated memory block because the block is larger than needed.
95. **Explain First-Fit, Best-Fit, and Worst-Fit memory allocation strategies.**
    First-Fit allocates the first hole large enough. Best-Fit allocates the smallest hole large enough (minimizing leftover hole size). Worst-Fit allocates the largest available hole (maximizing leftover hole size).
96. **Which of these strategies is generally more efficient?**
    First-Fit is often fastest. Best-Fit tends to minimize wasted space but can create tiny unusable holes. Worst-Fit tries to leave large usable holes but may consume them quickly.
97. **How does fragmentation vary among these strategies?**
    First-Fit and Best-Fit can lead to more external fragmentation over time. Worst-Fit might reduce tiny fragments but consumes large holes faster. Internal fragmentation is typical of fixed partitioning/paging, not these dynamic strategies.
98. **What is paging in memory management?**
    Paging is a non-contiguous memory allocation technique dividing logical memory into fixed-size pages and physical memory into same-sized frames, allowing pages to be placed anywhere.
99. **What is the difference between a frame and a page?**
    A page is a fixed-size block in the logical (virtual) address space of a process. A frame is a fixed-size block in physical main memory.
100. **What is segmentation? How is it different from paging?**
    Segmentation divides memory based on logical program units (code, data, stack) of variable sizes. Paging uses fixed physical units (pages/frames), transparent to the programmer.
101. **Can paging and segmentation be combined? Explain with an example.**
    Yes, in segmented paging, memory is divided into segments, and each segment is then divided into pages (e.g., Intel x86 architecture used this).
102. **What is a page table?**
    A page table is a data structure used by the OS to store the mapping between a process's virtual pages and their corresponding physical frames in memory.
103. **What is the purpose of the Translation Lookaside Buffer (TLB)?**
    The TLB is a fast hardware cache that stores recently used page-to-frame mappings (page table entries) to speed up virtual-to-physical address translation.
104. **How does the TLB improve memory access time?**
    A TLB hit avoids accessing the potentially slower main memory page table, significantly reducing address translation time. A miss requires a page table lookup.
105. **What is virtual memory?**
    Virtual memory is a technique that allows processes to use more memory than is physically available by using disk space as an extension of RAM, loading only needed parts into memory.
106. **What is the advantage of using virtual memory?**
    Advantages include running larger programs, increasing the degree of multiprogramming, and simplifying memory management for programmers.
107. **Define demand paging.**
    Demand paging is a virtual memory method where pages are loaded from disk into main memory only when they are actually referenced (demanded) by the executing process.
108. **What is a page fault? What happens when one occurs?**
    A page fault is an interrupt generated when a process accesses a page not currently in physical memory. The OS handles it by loading the required page from disk into a free frame (possibly replacing another page) and resuming the process.
109. **Why are page replacement algorithms needed?**
    Page replacement algorithms are needed when a page fault occurs and there are no free frames in memory, requiring the OS to select a victim page to swap out to disk.
110. **Explain FIFO page replacement algorithm.**
    FIFO (First-In, First-Out) replaces the page that has been in memory the longest, irrespective of its recent usage pattern.
111. **What is the main drawback of FIFO?**
    FIFO can perform poorly by replacing frequently used pages if they are old, and it suffers from Belady's Anomaly (more frames can sometimes lead to more page faults).
112. **Describe the Optimal page replacement algorithm.**
    Optimal replaces the page that will not be used for the longest period in the future; it achieves the lowest possible page fault rate but is unimplementable.
113. **Why is the Optimal algorithm not practical in real systems?**
    It requires perfect knowledge of the future sequence of memory references, which is impossible to predict in a real system.
114. **Explain LRU (Least Recently Used) algorithm.**
    LRU replaces the page that has not been referenced for the longest amount of time, assuming past usage predicts future usage (based on locality).
115. **How is LRU better than FIFO?**
    LRU generally performs better as it uses recent history (locality of reference) to make replacement decisions, avoiding replacing frequently used pages just because they are old. It doesn't suffer from Belady's Anomaly.

**OS Module 5: File Systems**

116. **What is a file in the context of an operating system?**
    A file is a named collection of related information, recorded on secondary storage (like a disk), that the OS treats as a logical unit for storage and access.
117. **What are the basic operations that can be performed on a file?**
    Basic operations include Create, Delete, Open, Close, Read, Write, Seek (reposition), and Get/Set Attributes.
118. **What is the difference between a file and a directory?**
    A file contains data (user or system), while a directory (or folder) is a structure that organizes files and other directories, essentially containing references to them.
119. **What is metadata in file systems?**
    Metadata is data *about* a file, such as its name, size, type, location, ownership, permissions, and timestamps, stored separately from the file's actual content.
120. **What are the different file organization methods?**
    These refer to how file blocks are stored on disk: Contiguous Allocation (all blocks together), Linked Allocation (blocks linked via pointers), and Indexed Allocation (an index block points to data blocks).
121. **Explain sequential access. Where is it commonly used?**
    Sequential access reads/writes data in order from beginning to end. It's common for simple text files, pipes, and was standard for magnetic tapes.
122. **What is direct (random) access?**
    Direct access allows reading or writing data blocks at any arbitrary location within the file without processing preceding blocks, often used by databases.
123. **What is indexed access?**
    Indexed access uses an index (like in indexed allocation) containing pointers to file blocks, allowing direct access to specific blocks based on the index structure.
124. **How do access methods affect performance?**
    Sequential access is efficient for whole-file reads/writes. Direct/indexed access is fast for random lookups but might have higher overhead for sequential operations.
125. **What is the purpose of a directory in a file system?**
    Directories provide a hierarchical structure to organize files logically, making them easier for users to manage and locate, and mapping names to file system objects.
126. **What information is typically stored in a directory entry?**
    A directory entry typically contains the file name and a pointer (or inode number) linking to the file's metadata and data blocks.
127. **What are the types of directory structures?**
    Common structures include Single-Level, Two-Level (user directories), Tree-Structured (hierarchical), Acyclic-Graph (allows sharing via links), and General Graph (rare, allows cycles).
128. **Explain single-level, two-level, and tree-structured directories.**
    Single-Level: One global directory (naming conflicts). Two-Level: Master directory + user directories. Tree-Structured: Hierarchical structure of directories and subdirectories (most common).
129. **What is an acyclic graph directory? How is it used for file sharing?**
    An acyclic graph structure allows files or directories to appear in multiple directory paths (using links), facilitating sharing without data duplication while preventing cycles.
130. **What is the difference between absolute and relative path names?**
    An absolute path specifies a location from the root directory (e.g., `/usr/bin/`). A relative path specifies a location starting from the current working directory (e.g., `../docs`).
131. **What is file sharing and why is it useful?**
    File sharing allows multiple users/processes to access the same file concurrently or sequentially. It's useful for collaboration, saving space, and maintaining data consistency.
132. **How does an OS manage concurrent access to shared files?**
    The OS uses mechanisms like file locking (mandatory or advisory) and access permissions to control concurrent access, preventing data corruption or unauthorized actions.
133. **What are access control lists (ACLs)?**
    ACLs provide fine-grained access control by associating a list of specific users/groups and their permitted operations (read, write, execute) with a file or directory.
134. **What is the difference between user-level and group-level file permissions?**
    User-level permissions apply to the file's owner. Group-level permissions apply to users belonging to the file's designated group. (There's also 'other' permissions).
135. **How does the OS ensure security and consistency during file sharing?**
    Security is ensured through authentication and enforcing permissions (standard or ACLs). Consistency is maintained using locking mechanisms or atomic file operations.

**OS Module 6: I/O Management & Disk Scheduling**

136. **What are I/O devices? Give some examples.**
    I/O devices are hardware peripherals used for input (keyboard, mouse), output (monitor, printer), or storage (disk drive, SSD). They interface the computer with the external world or persistent storage.
137. **What is the difference between input, output, and storage devices?**
    Input devices send data to the computer (keyboard). Output devices receive data from the computer (monitor). Storage devices store data persistently (disk drive). Some devices do both (network card).
138. **What is the role of an I/O module?**
    An I/O module (or device controller) acts as an interface between the CPU/memory system and an I/O device, handling control signals, status reporting, and data buffering/transfer.
139. **How does the CPU communicate with I/O devices?**
    Communication occurs via I/O instructions and techniques like programmed I/O (polling), interrupt-driven I/O, or Direct Memory Access (DMA) for efficient bulk transfers.
140. **How is data organized on a disk?**
    Data on a magnetic disk is organized physically into platters, surfaces, concentric tracks per surface, and fixed-size sectors per track.
141. **What is a cylinder, track, and sector?**
    A sector is the smallest addressable unit of storage. A track is a circular path on a platter surface. A cylinder is the set of tracks at the same radial position on all surfaces.
142. **What is seek time and rotational latency?**
    Seek time is the time for the disk arm to move the heads to the cylinder containing the desired sector. Rotational latency is the time for the desired sector to rotate under the head.
143. **What is transfer time in disk operations?**
    Transfer time is the time taken to transfer the actual data between the disk and main memory once the head is positioned over the correct sector(s).
144. **What causes disk access delay?**
    The total disk access delay is primarily the sum of seek time, rotational latency, and transfer time. Controller overhead also contributes.
145. **Why is disk scheduling important?**
    Disk scheduling is important to optimize disk performance by minimizing total seek time and improving throughput and average response time for I/O requests.
146. **Explain the FCFS (First-Come, First-Served) disk scheduling algorithm.**
    FCFS services disk I/O requests in the order they arrive in the queue; it's simple but often inefficient in terms of head movement.
147. **What is the drawback of FCFS in disk scheduling?**
    FCFS can result in wild head swings and poor performance, as it doesn't optimize seek distances based on current head position.
148. **What is SSTF (Shortest Seek Time First)? How does it work?**
    SSTF selects the pending request closest to the current head position, minimizing seek time for the next immediate request.
149. **How can SSTF lead to starvation?**
    SSTF can cause starvation for requests on tracks far from the current head activity if a continuous stream of requests arrives nearby.
150. **Explain the SCAN (Elevator) algorithm.**
    SCAN moves the disk head back and forth across the disk, servicing requests in its path. It reverses direction only when it reaches one end of the disk.
151. **What is the difference between SCAN and CSCAN (Circular SCAN)?**
    SCAN services requests in both directions. CSCAN services requests only in one direction; upon reaching the end, it quickly returns to the beginning without servicing requests on the return trip.
152. **When is CSCAN preferred over SCAN?**
    CSCAN provides more uniform wait times compared to SCAN because it prevents requests at the far end from waiting for the head to service requests on the return trip.
153. **Explain the LOOK and C-LOOK algorithms.**
    LOOK and C-LOOK are variants of SCAN and CSCAN, respectively, where the head reverses direction immediately after the last request in that direction, without necessarily going to the physical end of the disk.
154. **How do LOOK and C-LOOK improve over SCAN and CSCAN?**
    They improve efficiency by preventing unnecessary head travel to the ends of the disk when no requests are pending there, reducing average seek time.
155. **Which disk scheduling algorithm gives the best performance overall?**
    No single algorithm is universally best; LOOK/C-LOOK often provide a good balance of performance and fairness. The best choice depends on the specific workload pattern.
156. **How do you decide which disk scheduling algorithm to use?**
    The decision depends on factors like the system's I/O workload (request patterns, load level) and performance goals (maximizing throughput vs. ensuring fairness/low variance in response time).