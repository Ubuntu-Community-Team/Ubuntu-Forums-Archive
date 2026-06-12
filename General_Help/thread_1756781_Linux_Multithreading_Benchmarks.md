---
title: "Linux Multithreading Benchmarks"
date: 2011-05-12
forum: General Help
---

### Post by RoyLongbottom on 2011-05-12
[FONT=Verdana][SIZE=2]**More Free Benchmarks** - See also[/SIZE][/FONT]
 
 
[FONT=Verdana][[SIZE=2]http://ubuntuforums.org/showthread.php?t=1636652&highlight=benchmarks[/SIZE]]("http://ubuntuforums.org/showthread.php?t=1636652&highlight=benchmarks")[/FONT]
 
[FONT=Verdana][SIZE=2]I am converting my Windows multithreading benchmarks to run under Linux and will be releasing them one at a time with both 32 bit and 64 bit compilations. Details are available in:[/SIZE][/FONT]
 
 
[FONT=Verdana][[SIZE=2]http://www.roylongbottom.org.uk/linux%20multithreading%20benchmarks.htm[/SIZE]]("http://www.roylongbottom.org.uk/linux%20multithreading%20benchmarks.htm")[/FONT]
 
 
[FONT=Verdana][SIZE=2]Execution files, that do not need installing, and source code are in:[/SIZE][/FONT]
 
 
[FONT=Verdana][[SIZE=2]http://www.roylongbottom.org.uk/linux_multithreading_apps.tar.gz[/SIZE]]("http://www.roylongbottom.org.uk/linux_multithreading_apps.tar.gz")[/FONT]
 
 
[FONT=Verdana][SIZE=2]The first ones execute simple integer and floating point add instructions via assembly language. Floating point arithmetic is identical on the two versions, via SSE instructions that handle four calculations at a time via 128 bit registers. Performance is measured in Millions of Floating Point Operations Per Second (MFLOPS) with expected maximum speed of four adds per CPU clock cycle. Integer calculations are the same, except one uses 32 bit instructions/registers and the other the 64 bit varieties. For these, speed is measured in Millions of Instructions Per Second (MIPS). The default runs using four threads but a command line option allows selection of up to 64 threads. Following are 1 thread and 16 thread results from a quad core processor, via Ubuntu, showing near four times improvement in throughput. Of particular note is the out of order completion time. [/SIZE][/FONT]
 
 
[FONT=Courier New][SIZE=2]##############################################[/SIZE][/FONT]
 
[FONT=Courier New][SIZE=2]Assembler CPUID and RDTSC [/SIZE][/FONT]
[FONT=Courier New][SIZE=2]CPU AuthenticAMD, Features Code 178BFBFF, Model Code 00100F42 [/SIZE][/FONT]
[FONT=Courier New][SIZE=2]AMD Phenom(tm) II X4 945 Processor [/SIZE][/FONT]
[FONT=Courier New][SIZE=2]Measured - Minimum 3014 MHz, Maximum 3014 MHz [/SIZE][/FONT]
[FONT=Courier New][SIZE=2]Linux Functions [/SIZE][/FONT]
[FONT=Courier New][SIZE=2]get_nprocs() - CPUs 4, Configured CPUs 4 [/SIZE][/FONT]
[FONT=Courier New][SIZE=2]get_phys_pages() and size - RAM Size 7.81 GB, Page Size 4096 Bytes [/SIZE][/FONT]
[FONT=Courier New][SIZE=2]uname() - Linux, roy-64, 2.6.35-22-generic [/SIZE][/FONT]
[FONT=Courier New][SIZE=2]#33-Ubuntu SMP Sun Sep 19 20:32:27 UTC 2010, x86_64 [/SIZE][/FONT]
 
[FONT=Courier New][SIZE=2]4 CPUs Available[/SIZE][/FONT]
[FONT=Courier New][SIZE=2]##############################################[/SIZE][/FONT]
 
[FONT=Courier New][SIZE=2]Multithreading Add Test 64 bit Version 1.0 Thu May 5 11:35:37 2011[/SIZE][/FONT]
 
[FONT=Courier New][SIZE=2]Integer Additions 1 Threads[/SIZE][/FONT]
 
[FONT=Courier New][SIZE=2]Thread 1 - 8052 64 bit Integer MIPS[/SIZE][/FONT]
 
[FONT=Courier New][SIZE=2]SSE Floating Point Additions 1 Threads[/SIZE][/FONT]
 
[FONT=Courier New][SIZE=2]Thread 1 - 12046 32 Bit SSE MFLOPS[/SIZE][/FONT]
 
[FONT=Courier New][SIZE=2]##############################################[/SIZE][/FONT]
 
[FONT=Courier New][SIZE=2]Multithreading Add Test 64 bit Version 1.0 Thu May 5 11:36:11 2011[/SIZE][/FONT]
 
[FONT=Courier New][SIZE=2]Integer Additions 16 Threads[/SIZE][/FONT]
 
[FONT=Courier New][SIZE=2]Thread 1 - 2104 64 bit Integer MIPS[/SIZE][/FONT]
[FONT=Courier New][SIZE=2]Thread 16 - 2085 64 bit Integer MIPS[/SIZE][/FONT]
[FONT=Courier New][SIZE=2]Thread 12 - 2081 64 bit Integer MIPS[/SIZE][/FONT]
[FONT=Courier New][SIZE=2]Thread 4 - 2070 64 bit Integer MIPS[/SIZE][/FONT]
[FONT=Courier New][SIZE=2]Thread 8 - 2069 64 bit Integer MIPS[/SIZE][/FONT]
[FONT=Courier New][SIZE=2]Thread 15 - 2062 64 bit Integer MIPS[/SIZE][/FONT]
[FONT=Courier New][SIZE=2]Thread 7 - 2057 64 bit Integer MIPS[/SIZE][/FONT]
[FONT=Courier New][SIZE=2]Thread 11 - 2055 64 bit Integer MIPS[/SIZE][/FONT]
[FONT=Courier New][SIZE=2]Thread 6 - 2037 64 bit Integer MIPS[/SIZE][/FONT]
[FONT=Courier New][SIZE=2]Thread 14 - 2030 64 bit Integer MIPS[/SIZE][/FONT]
[FONT=Courier New][SIZE=2]Thread 3 - 2026 64 bit Integer MIPS[/SIZE][/FONT]
[FONT=Courier New][SIZE=2]Thread 2 - 2025 64 bit Integer MIPS[/SIZE][/FONT]
[FONT=Courier New][SIZE=2]Thread 13 - 2022 64 bit Integer MIPS[/SIZE][/FONT]
[FONT=Courier New][SIZE=2]Thread 10 - 2019 64 bit Integer MIPS[/SIZE][/FONT]
[FONT=Courier New][SIZE=2]Thread 9 - 2002 64 bit Integer MIPS[/SIZE][/FONT]
[FONT=Courier New][SIZE=2]Thread 5 - 2000 64 bit Integer MIPS[/SIZE][/FONT]
[FONT=Courier New][SIZE=2]Total - 32744 64 Bit Integer MIPS[/SIZE][/FONT]
[FONT=Courier New][SIZE=2]Aggregate - 32002 64 Bit Integer MIPS, based on last to finish[/SIZE][/FONT]
 
[FONT=Courier New][SIZE=2]SSE Floating Point Additions 16 Threads[/SIZE][/FONT]
 
[FONT=Courier New][SIZE=2]Thread 6 - 3049 32 Bit SSE MFLOPS[/SIZE][/FONT]
[FONT=Courier New][SIZE=2]Thread 14 - 3021 32 Bit SSE MFLOPS[/SIZE][/FONT]
[FONT=Courier New][SIZE=2]Thread 2 - 3016 32 Bit SSE MFLOPS[/SIZE][/FONT]
[FONT=Courier New][SIZE=2]Thread 8 - 3012 32 Bit SSE MFLOPS[/SIZE][/FONT]
[FONT=Courier New][SIZE=2]Thread 7 - 3010 32 Bit SSE MFLOPS[/SIZE][/FONT]
[FONT=Courier New][SIZE=2]Thread 3 - 3007 32 Bit SSE MFLOPS[/SIZE][/FONT]
[FONT=Courier New][SIZE=2]Thread 10 - 3005 32 Bit SSE MFLOPS[/SIZE][/FONT]
[FONT=Courier New][SIZE=2]Thread 5 - 3004 32 Bit SSE MFLOPS[/SIZE][/FONT]
[FONT=Courier New][SIZE=2]Thread 1 - 3002 32 Bit SSE MFLOPS[/SIZE][/FONT]
[FONT=Courier New][SIZE=2]Thread 13 - 3001 32 Bit SSE MFLOPS[/SIZE][/FONT]
[FONT=Courier New][SIZE=2]Thread 11 - 3000 32 Bit SSE MFLOPS[/SIZE][/FONT]
[FONT=Courier New][SIZE=2]Thread 9 - 2999 32 Bit SSE MFLOPS[/SIZE][/FONT]
[FONT=Courier New][SIZE=2]Thread 4 - 2995 32 Bit SSE MFLOPS[/SIZE][/FONT]
[FONT=Courier New][SIZE=2]Thread 16 - 2994 32 Bit SSE MFLOPS[/SIZE][/FONT]
[FONT=Courier New][SIZE=2]Thread 15 - 2993 32 Bit SSE MFLOPS[/SIZE][/FONT]
[FONT=Courier New][SIZE=2]Thread 12 - 2989 32 Bit SSE MFLOPS[/SIZE][/FONT]
[FONT=Courier New][SIZE=2]Total - 48097 32 Bit SSE MFLOPS[/SIZE][/FONT]
[FONT=Courier New][SIZE=2]Aggregate - 47819 32 Bit SSE MFLOPS, based on last to finish[/SIZE][/FONT]
 
[FONT=Courier New][SIZE=2][Will not format properly Couier New][/SIZE][/FONT]
[FONT=Courier New][SIZE=2][/SIZE][/FONT] 
[FONT=Courier New][SIZE=2]Roy[/SIZE][/FONT]

---

### Post by RoyLongbottom on 2011-05-17
[FONT=Verdana][SIZE=2]**MultiThreading Whetstone Benchmark**[/SIZE][/FONT]
[FONT=Verdana][SIZE=2][/SIZE][/FONT] 
[FONT=Verdana][SIZE=2]Announcing my second Windows multithreading benchmark to run under Linux with both 32 bit and 64 bit compilations. Details of all are available in:[/SIZE][/FONT]
[FONT=Verdana][SIZE=2][/SIZE][/FONT] 
[FONT=Verdana][SIZE=2][http://www.roylongbottom.org.uk/linux%20multithreading%20benchmarks.htm](http://www.roylongbottom.org.uk/linux%20multithreading%20benchmarks.htm) [/SIZE][/FONT]
[FONT=Verdana][SIZE=2][/SIZE][/FONT] 
[FONT=Verdana][SIZE=2]Execution files, that do not need installing, and source code are in:[/SIZE][/FONT]
[FONT=Verdana][SIZE=2][/SIZE][/FONT] 
[FONT=Verdana][SIZE=2][http://www.roylongbottom.org.uk/linux_multithreading_apps.tar.gz](http://www.roylongbottom.org.uk/linux_multithreading_apps.tar.gz) [/SIZE][/FONT]
 
[FONT=Verdana][SIZE=2][/SIZE][/FONT] 
[FONT=Verdana][SIZE=2]The Whetstone programs, initially used in 1972, were the first general purpose benchmarks that set industry standards of computer system performance. The overall performance rating is in Millions of Whetstone Instructions Per Second (MWIPS). Later, it was found necessary to measure the speed of the eight different test functions used, to demonstrate that compilers were not over optimising and to allow code tweaks to avoid this situation. The additional measurements are in terms of Millions of Operations Per Second (MOPS) or MFLOPS for straight floating point calculations. As the design authority, nominated by the original author, I have to say that versions that do not provide these separate measurements cannot be taken as valid. [/SIZE][/FONT]
[FONT=Verdana][SIZE=2][/SIZE][/FONT] 
[FONT=Verdana][SIZE=2]All threads are run using the same pass count, running time being extended when there are more threads than CPUs. The same calculations are carried out on each thread but using dedicated variables. The numeric results of calculations are logged for the first thread with others checked for the same values. [/SIZE][/FONT]
[FONT=Verdana][SIZE=2][/SIZE][/FONT] 
[FONT=Verdana][SIZE=2]There are four versions available for 32-Bit or 64-Bit (SSE) operation using single or double precision floating point. A command line variable can be used to specify between 1 and 64 threads to be used, with a default as the number of CPUs identified. An example of results is attached.[/SIZE][/FONT]
[SIZE=2][/SIZE] 
[SIZE=2][/SIZE] 
[SIZE=2]Roy[/SIZE]

---

### Post by RoyLongbottom on 2011-05-22
[FONT=Verdana][SIZE=2]**MultiThreading Memory Based MFLOPS Benchmark**[/SIZE][/FONT]

[FONT=Verdana][SIZE=2]Details, source and execution files of my third Windows multithreading benchmark converted to run under Linux are available in:[/SIZE][/FONT]
 
[FONT=Verdana][SIZE=2][http://www.roylongbottom.org.uk/linux%20multithreading%20benchmarks.htm](http://www.roylongbottom.org.uk/linux%20multithreading%20benchmarks.htm) [/SIZE][/FONT]

[FONT=Verdana][SIZE=2][http://www.roylongbottom.org.uk/linux_multithreading_apps.tar.gz](http://www.roylongbottom.org.uk/linux_multithreading_apps.tar.gz)[/SIZE][/FONT]

 
[FONT=Verdana][SIZE=2]For this one, each thread carries out the same calculations but on a different segment of shared memory data.The benchmark executes identical functions as my CUDA and OpenMP performance tests where the arithmetic operations executed are of the form x[i] = (x[i] + a) * b - (x[i] + c) * d + (x[i] + e) * f with 2, 8 or 32 operations per input data word. Array sizes used are 0.1, 1 or 10 million 4 byte single precision floating point words. The program checks for consistent numeric results, primarily to show that all calculations are carried out. The number of threads used is the same as the number of identified CPUs.[/SIZE][/FONT]
[FONT=Verdana][SIZE=2]Two versions, MPmflops64 and MPmflops32, were compiled, the first involving the default SSE floating point instructions and the second using the original i87 functions. Speed using SSE instructions is probably amongst the fastest obtainable from a single program, on a multi-core CPU. An example is nearly 28.8 GFLOPS on a 2.4 GHz Core 2 Duo, or 12 results per clock cycle. After noting this speed MPmflops32SSE, was produced and a parameter included to run the program as a reliability/burn-in test. An example of results on a quad core Phenom is attached, along with some using burn-in options on a laptop, where speed is reduced when the CPU reaches around 95°C.[/SIZE][/FONT]
 
[FONT=Verdana]Roy[/FONT]

---

### Post by RoyLongbottom on 2011-06-14
[FONT=Verdana][SIZE=2]**MP Memory Speed**[/SIZE][/FONT]
 
[FONT=Verdana][SIZE=2]Details, source and execution files of my fourth Windows multithreading benchmark converted to run under Linux are available in:[/SIZE][/FONT]
 
[FONT=Verdana][SIZE=2][http://www.roylongbottom.org.uk/linux%20multithreading%20benchmarks.htm](http://www.roylongbottom.org.uk/linux%20multithreading%20benchmarks.htm) [/SIZE][/FONT]
[FONT=Verdana][SIZE=2][http://www.roylongbottom.org.uk/linux_multithreading_apps.tar.gz](http://www.roylongbottom.org.uk/linux_multithreading_apps.tar.gz) [/SIZE][/FONT]
 
[FONT=Verdana][SIZE=2]This benchmark employs three different sequences of operations, on 64 bit double precision floating point numbers, 32 bit single precision numbers and 64 or 32 bit integers via two data arrays:[/SIZE][/FONT]
 
[FONT=Verdana][FONT=Courier New][SIZE=2]Result to memory x[m] = x[m] + s * y[m] [/SIZE][/FONT][/FONT]
[FONT=Verdana][FONT=Courier New][SIZE=2]Sum to memory x[m] = x[m] + y[m] [/SIZE][/FONT][/FONT]
[FONT=Verdana][FONT=Courier New][SIZE=2]Memory to memory x[m] = y[m] [/SIZE][/FONT][/FONT]
 
[FONT=Verdana][SIZE=2]Memory tested doubles up from 4 KB to 25% of RAM size, to use all caches and RAM. Speed measurements are data reading speeds in MegaBytes Per Second. The C programming calculations are identical to those used for an OpenMP version and one that can only use one core, details being in:[/SIZE][/FONT]
 
[FONT=Verdana][SIZE=2][http://www.roylongbottom.org.uk/openmp%20speeds.htm#anchor1](http://www.roylongbottom.org.uk/openmp%20speeds.htm#anchor1)[/SIZE][/FONT]
 
[FONT=Verdana][SIZE=2]MPmemspeed32 and MPmemspeed64 can be run using up to 64 threads, each one repetitively carrying out calculations on its own segment of data. With RAM sized data and many threads, performance is much faster as when the segments fit in preceding caches. The 32 bit version uses the old i87 floating point instructions and 32 bit integers. The other uses 64 bit integers and, as expected, compiles to use SSE instructions, but these are the slow scalar SISD variety but generally faster than using OpenMP. An example of results on a quad core Phenom is sttached.[/SIZE][/FONT]

[SIZE=2]Roy[/SIZE]

---

### Post by RoyLongbottom on 2011-06-23
[FONT=Verdana][SIZE=2]**MP Memory Bus Speeds**[/SIZE][/FONT]
[FONT=Verdana][SIZE=2][/SIZE][/FONT] 
[FONT=Verdana][SIZE=2]Details, source and execution files of my fifth Windows multithreading benchmark converted to run under Linux are available in:[/SIZE][/FONT]
[FONT=Verdana][SIZE=2] [/SIZE][/FONT]
[FONT=Verdana][SIZE=2][http://www.roylongbottom.org.uk/linux%20multithreading%20benchmarks.htm#anchor10](http://www.roylongbottom.org.uk/linux%20multithreading%20benchmarks.htm#anchor10)  [/SIZE][/FONT]
[FONT=Verdana][SIZE=2][http://www.roylongbottom.org.uk/linux_multithreading_apps.tar.gz](http://www.roylongbottom.org.uk/linux_multithreading_apps.tar.gz) [/SIZE][/FONT]
[FONT=Verdana][SIZE=2][/SIZE][/FONT] 
[FONT=Verdana][SIZE=2][/SIZE][/FONT]
[FONT=Verdana][SIZE=2]This benchmark reads data using AND instructions at a range of data sizes covering caches and RAM, where between 1 and 64 run time selected threads share the same data. The intention is to produce maximum data transfer speeds over CPU and memory buses. Some buses transfer data in bursts, typically 64 bytes at a time, the benchmark demonstrating this by reading single words from a range of possible burst sizes, also allowing reasonable estimates of maximum speed to be calculated.[/SIZE][/FONT]
[FONT=Verdana][SIZE=2][/SIZE][/FONT] 
[FONT=Verdana][SIZE=2]MPbusspeed64 and MPbusspeed32, the 64-Bit and 32-Bit versions have one test in common, reading integer data to 128 bit SSE2 registers, other tests using 64 bit or 32 bit registers. With data from caches, speed in terms of MB/second is often twice as fast at 64 bits, implying the same instruction execution speed. Attached are 64 bit and 32 bit results on a 3 GHz quad core Phenom II using 1 thread and 64 threads.[/SIZE][/FONT]
[FONT=Verdana][SIZE=2] [/SIZE][/FONT]
[SIZE=2]Roy [/SIZE]

---

### Post by RoyLongbottom on 2011-07-06
[FONT=Verdana][SIZE=2]**MP Memory Random Access Speeds**[/SIZE][/FONT]
[FONT=Verdana][SIZE=2][/SIZE][/FONT] 
[FONT=Verdana][SIZE=2]Details, source and execution files of my sixth and last Windows multithreading benchmark converted to run under Linux are available in:[/SIZE][/FONT]
[FONT=Verdana][SIZE=2] [/SIZE][/FONT]
[FONT=Verdana][SIZE=2][http://www.roylongbottom.org.uk/linux%20multithreading%20benchmarks.htm#anchor12](http://www.roylongbottom.org.uk/linux%20multithreading%20benchmarks.htm#anchor12) [/SIZE][/FONT]
[FONT=Verdana][SIZE=2][http://www.roylongbottom.org.uk/linux_multithreading_apps.tar.gz](http://www.roylongbottom.org.uk/linux_multithreading_apps.tar.gz) [/SIZE][/FONT]
[FONT=Verdana][SIZE=2] [/SIZE][/FONT]
[FONT=Verdana][SIZE=2]This benchmark uses the same code for serial and random access via a complex indexing structure and comprises Read (RD) and Read/Write (RW) tests. They are run to process data from L1 cache, L2 cache and RAM using up to 64 threads. The program uses data from the same array for all threads, but starting at different points. With reading and writing, there is a possibility that data can be corrupted when more than one thread updates the same data. Although it cannot be proven with this benchmark, it seems that the Operating System does not allow shared data to be updated in local caches and flushes them to update in shared data areas, producing significant performance degradation, particularly on random access. To avoid this possible corruption, extra tests (Mutex) have been included that allow only one thread at a time to access common data. This can still lead to using four threads being slower than one but, with random access, there can be a significant improvement compared with untethered multiple thread speeds, except when accessing RAM. [/SIZE][/FONT]
[FONT=Verdana][SIZE=2]MPrandmem64 and MPrandmem32, the 64-Bit and 32-Bit versions, both use 32 bit integer data arrays but sometimes produce different data transfer speeds. Attached are 64 bit and 32 bit results on a 3 GHz quad core Phenom II using four threads.[/SIZE][/FONT]
[FONT=Verdana][SIZE=2][/SIZE][/FONT] 
[FONT=Verdana][SIZE=2]Roy[/SIZE][/FONT]

---

