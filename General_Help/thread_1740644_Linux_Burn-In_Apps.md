---
title: "Linux Burn-In Apps"
date: 2011-04-27
forum: General Help
---

### Post by RoyLongbottom on 2011-04-27
[FONT=Verdana][SIZE=2]I have produced variations of my Windows based Reliability/Burn-In test programs. They are intended to **stress test CPUs, caches, RAM, buses, disks and other drives **using high processing speeds, to induce heating effects, and varying data bit order, to investigate possible pattern conscious faults. Common features are command line options to specify memory/storage demands, running time and different results log file names, for use in multiprocessor tests. Data read and results of calculations are also checked for correct or consistent values. Versions compiled to run on 32-Bit and 64-Bit processors are provided. For general information, details and results see: [/SIZE][/FONT]
 
[FONT=Verdana][SIZE=2][http://www.roylongbottom.org.uk/linux%20benchmarks.htm]("http://www.roylongbottom.org.uk/linux%20benchmarks.htm") [/SIZE][/FONT]
[FONT=Verdana][SIZE=2][http://www.roylongbottom.org.uk/linux%20burn-in%20apps.htm](http://www.roylongbottom.org.uk/linux%20burn-in%20apps.htm) [/SIZE][/FONT]
 
[FONT=Verdana][SIZE=2]The execution files and source code along with compile and run instructions can be downloaded in[/SIZE][/FONT]
 
[FONT=Verdana][SIZE=2][http://www.roylongbottom.org.uk/linux_burn-in_apps.tar.gz](http://www.roylongbottom.org.uk/linux_burn-in_apps.tar.gz) [/SIZE][/FONT]
 
[FONT=Verdana][SIZE=2]**BurnInSSE64 and BurnInSSE32** execute floating point instructions at an exceptionally fast speed for maximum heating effects. The main run time parameters are for test duration and data size for data transfers using caches or RAM.[/SIZE][/FONT]
 
[FONT=Verdana][SIZE=2]**IntBurn64 and IntBurn32** tests are based on assembly code with IntBurn32 using 32 bit integers and IntBurn64 accessing a larger number of 64 bit registers. Again, parameters can control running time and data size. Using multiple copies, these programs are appropriate to use as paging/swapping tests by allocating more memory space than available RAM capacity.[/SIZE][/FONT]
 
[FONT=Verdana][SIZE=2]**DriveStress64 and DriveStress32** measure drive and bus speeds (e.g. SATA or USB) whilst checking data read for correct values. Parameters control size of four files used in multiples of 10.3 MB, comprising 164 blocks each with words containing unique binary patterns. Timing can be changed to read the files multiple times with random sequences of the four files. Then, for a second phase, where each block of one file is read multiple times, reading disk based data from the drive&#8217;s buffer at maximum bus speeds. The programs also have a parameter that allows Linux to cache the data in RAM, providing another memory test.[/SIZE][/FONT]
 
[FONT=Verdana][SIZE=2]**Multitasking Scripts** - Examples are provided showing how to mix and match programs (including earlier compilations) and run time parameter to soak test complete systems for as long as is required. They also demonstrate how to organise dynamic displayed results in multiple X terminal windows. [/SIZE][/FONT]
 
[FONT=Verdana][SIZE=2]**Successes** - Three significant problems were identified during testing. The first was apparent excessive temperatures on a desktop PC, compared with earlier measurements via Windows. This was cured by clearing dust out of the CPU heatsink using a compressed air sprayer. Then there were two **Linux Peculiarities** that seem to be affected by power saving options. A desktop PC with a Core 2 Duo CPU showed a throughput increase of three times using both cores. Here, using one core with &#8220;On-Demand&#8221; CPU GHz (via Frequency Scaling Monitor), the processor was running at 1.6 GHz instead of 2.4 GHz. Then a laptop, again with a Core 2 Duo PC, overheated, causing the CPU to run at less than half speed. Unlike using Windows, with power on to Ubuntu, initial CPU temperatures were high with the fan not appearing to run as fast as it might. On an apparent random basis, the laptop started at a lower temperature and did not overheat, with the fan apparently running at high speed. [/SIZE][/FONT]
 
[FONT=Verdana][SIZE=2]See also:[/SIZE][/FONT]
[SIZE=2][/SIZE] 
[FONT=Verdana][SIZE=2][http://ubuntuforums.org/showthread.php?t=1636652&highlight=benchmarks](http://ubuntuforums.org/showthread.php?t=1636652&highlight=benchmarks)[/SIZE][/FONT]
 
[FONT=Verdana][SIZE=2][/SIZE][/FONT] 
[FONT=Verdana][SIZE=2]Roy[/SIZE][/FONT]

---

### Post by MooPi on 2011-04-27
Thanks Roy, I'm sure these will come in handy for new machines and testing reliability.

---

