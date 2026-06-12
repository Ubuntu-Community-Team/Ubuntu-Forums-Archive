---
title: "More Free Benchmarks"
date: 2010-12-03
forum: General Help
---

### Post by RoyLongbottom on 2010-12-03
[FONT=Verdana][SIZE=2]More benchmarks for Ubuntu. See my my last post at:[/SIZE][/FONT]
 
[FONT=Verdana][SIZE=2][http://ubuntuforums.org/showthread.php?t=1632576](http://ubuntuforums.org/showthread.php?t=1632576) [/SIZE][/FONT]
 
[FONT=Verdana][SIZE=2]The second 64-Bit and 32-Bit benchmarks ported to Linux are intended to demonstrate maximum arithmetic instruction speeds as millions of add instructions per second (integer MIPS and Floating Point MFLOPS) for instruction types x86, x87, x64, MMX, SSE, SSE2 and 3DNow (AMD only). Assembly code is used for optimum performance. The benchmark execution files and source codes can be downloaded from:[/SIZE][/FONT]
 
[FONT=Verdana][SIZE=2][http://www.roylongbottom.org.uk/max_cpu_speeds.tar.gz](http://www.roylongbottom.org.uk/max_cpu_speeds.tar.gz) [/SIZE][/FONT]
 
[FONT=Verdana][SIZE=2]More detailed descriptions and results can be found in the following. Speed is demonstrated as up to 8 results per clock cycle or 24000 MIPS for a 3 GHz CPU.[/SIZE][/FONT]
 
[FONT=Verdana][SIZE=2][http://www.roylongbottom.org.uk/linux%20benchmarks.htm](http://www.roylongbottom.org.uk/linux%20benchmarks.htm) [/SIZE][/FONT]
[FONT=Verdana][SIZE=2][http://www.roylongbottom.org.uk/whatcpu%20results.htm#anchorLinux](http://www.roylongbottom.org.uk/whatcpu%20results.htm#anchorLinux) [/SIZE][/FONT]
 
[SIZE=2][FONT=Verdana]An example log file is attached.[/FONT][/SIZE]

 
[SIZE=2]Roy [/SIZE]

---

### Post by RoyLongbottom on 2010-12-13
[FONT=Verdana][SIZE=2][COLOR=black]**Linux OpenMP Benchmarks**[/COLOR][/SIZE][/FONT]
 
[FONT=Verdana][SIZE=2][COLOR=black]Latest benchmarks, ported to run via 32-Bit and 64-Bit Linux, use OpenMP procedures and software that arranges automatic parallel processing of shared memory data, when more than one processor is provided. As is the case here, the programs can be arranged to run without OpenMP implications, by omitting a compiler directive. The benchmarks show some best case and worst case performance. The benchmark execution files, source code and instructions can be downloaded in:[/COLOR][/SIZE][/FONT]

[FONT=Verdana][SIZE=2][COLOR=black][www.roylongbottom.org.uk/linux_openmp.tar.gz]("http://www.roylongbottom.org.uk/linux_openmp.tar.gz") [/COLOR][/SIZE][/FONT]

[FONT=Verdana][SIZE=2][COLOR=black]with description and results in:[/COLOR][/SIZE][/FONT]

[FONT=Verdana][SIZE=2][COLOR=black][http://www.roylongbottom.org.uk/linux%20openmp%20benchmarks.htm](http://www.roylongbottom.org.uk/linux%20openmp%20benchmarks.htm) [/COLOR][/SIZE][/FONT]

[FONT=Verdana][SIZE=2][COLOR=black]The original OpenMP benchmark uses relatively large data arrays sized at 0.4, 4.0 and 40 MBytes with 2, 8 and 32 floating point calculations per word (4 Bytes). This can demonstrate performance gains of nearly four times using a quad core processor compared with a single CPU. However, at 64 bits and unlike the OpenMP version, the normal compilation makes full use of SSE instructions, leading to a single processor appearing to be much faster than a dual core system.[/COLOR][/SIZE][/FONT]

[FONT=Verdana][SIZE=2][COLOR=black]The other benchmark (MemSpeed) measures performance of single and double precision floating point and integers. processing data from all levels of caches and RAM. Again there are 32 bit, 64 bit, OpenMP and non-OpenMP versions. Here, appropriate MP performance is possible at mid data sizes, but speeds are extremely slow with L1 cache sized data due to the long startup time.[/COLOR][/SIZE][/FONT]

[FONT=Verdana][SIZE=2][COLOR=black]Attached are example results of the two benchmarks.[/COLOR][/SIZE][/FONT]
 
[FONT=Verdana][SIZE=2][COLOR=black]Roy[/COLOR][/SIZE][/FONT]

---

### Post by RoyLongbottom on 2010-12-22
[FONT=Verdana][SIZE=3]Linux Memory Benchmarks[/SIZE][/FONT]

[FONT=Verdana][SIZE=2]This package contains 32 bit and 64 bit versions of three benchmarks that measure different aspects of memory speeds with data volumes accessed from caches and RAM. The execution files, source code and instructions can be downloaded in:[/SIZE][/FONT]

[FONT=Verdana][SIZE=2][http://www.roylongbottom.org.uk/memory_benchmarks.tar.gz](http://www.roylongbottom.org.uk/memory_benchmarks.tar.gz) [/SIZE][/FONT]

[FONT=Verdana][SIZE=2]**BusSpeed** - This demonstrates the difference in performance on processing and transferring 32 bit and 64 bit integers. It also shows where data is transferred in bursts over buses.[/SIZE][/FONT]

[FONT=Verdana][SIZE=2]**RandMem** - This uses identical programming code to read and write memory serially and randomly. Here, random access leads to much lower performance where data is read in bursts, as only part of the data is used.[/SIZE][/FONT]

[FONT=Verdana][SIZE=2]**SSEfpu** - This has assembly code to fully utilise registers employed in dealing with single precision (SSE) and double precision (SSE2) floating point numbers, compared with old x87 instructions and inefficient SSE code that can be produced by a compiler. Extensions over the original SSE benchmark can demonstrate performance faster than might be expected.[/SIZE][/FONT]

[FONT=Verdana][SIZE=2]More detailed descriptions and results can be found in the following:[/SIZE][/FONT]

[FONT=Verdana][SIZE=2][http://www.roylongbottom.org.uk/linux%20benchmarks.htm](http://www.roylongbottom.org.uk/linux%20benchmarks.htm) [/SIZE][/FONT]
[FONT=Verdana][SIZE=2][http://www.roylongbottom.org.uk/busspd2k%20results.htm#anchorLinux](http://www.roylongbottom.org.uk/busspd2k%20results.htm#anchorLinux) [/SIZE][/FONT]
[FONT=Verdana][SIZE=2][http://www.roylongbottom.org.uk/randmem%20results.htm#anchorLinux](http://www.roylongbottom.org.uk/randmem%20results.htm#anchorLinux) [/SIZE][/FONT]
[FONT=Verdana][SIZE=2][http://www.roylongbottom.org.uk/sse3dnow%20results.htm#anchorLinux](http://www.roylongbottom.org.uk/sse3dnow%20results.htm#anchorLinux) [/SIZE][/FONT]
 
[FONT=Verdana][SIZE=2]Roy [/SIZE][/FONT]

---

### Post by RoyLongbottom on 2011-01-08
[FONT=Verdana]**[SIZE=2]Linux CUDA Graphics MFLOPS Benchmark and Burn-In Tests[/SIZE]**[/FONT]

[FONT=Verdana][SIZE=2]The latest porting to Linux measures Millions of Floating Point Operations Per Second (MFLOPS) using CUDA, from nVidia. This provides programming functions to use GeForce graphics processors for general purpose computing. The graphics can have tens to hundreds of processing elements that can be easily used for parallel computing. The benchmark demonstrates some best and worst case performance using varying data array size and increasing scientific processing instructions per data access. Three basic tests are run with data in and out to external RAM, data out only and calculations with no reference to main RAM. Then there are extra tests with lower overheads or using cache like shared memory. [/SIZE][/FONT]

[FONT=Verdana][SIZE=2]Four versions are available covering Single and Double Precision floating point compiled to run on 32 and 64 bit Linux systems. The benchmarks, source code and instructions can be downloaded in:[/SIZE][/FONT]

[FONT=Verdana][SIZE=2][http://www.roylongbottom.org.uk/linux_cuda_mflops.tar.gz](http://www.roylongbottom.org.uk/linux_cuda_mflops.tar.gz) [/SIZE][/FONT]

[FONT=Verdana][SIZE=2]with further details and results in:[/SIZE][/FONT]

[FONT=Verdana][SIZE=2][http://www.roylongbottom.org.uk/linux_cuda_mflops.htm](http://www.roylongbottom.org.uk/linux_cuda_mflops.htm) [/SIZE][/FONT]

[FONT=Verdana][SIZE=2]Attached are example results using a graphics card with 128 processing elements. Maximum speed of the PCI-E bus used is equivalent to 1000M 32 bit words per second, limiting Data Out Only tests to 2000, 8000 and 32000 MFLOPS with 2, 8 and 32 floating point operations per word transferred. With Data In and Out, maximums are half this value. Calculate Only is likely to depend on video RAM speed, where maximum throughput is 70.4 GB or 17.6 G words per second. With data in and out, 8.8 Gw/second can be assumed. Multiplying this by 2, 8 and 32 operations indicates maximum speeds of 17600, 70400 and 281600 MFLOPS. Performance demonstrated is up to 70% of all these values. Maximum speed specification of the graphics card, using linked multiply, add and multiply, is 705 GFLOPS. Best achieved is 171 GFLOPS, but without the optimum instruction sequence and with some high speed cache memory accesses.[/SIZE][/FONT]

[FONT=Verdana][SIZE=2]The program checks that all calculated results are correct, particularly useful when used as a reliability/burn-in test. The following shows how to do it and has example results demonstrating 26 degrees C increase in GPU temperature after 3 minutes.[/SIZE][/FONT]

[FONT=Verdana][SIZE=2][http://www.roylongbottom.org.uk/linux_cuda_mflops.htm#anchor6](http://www.roylongbottom.org.uk/linux_cuda_mflops.htm#anchor6) [/SIZE][/FONT]

---

### Post by RoyLongbottom on 2011-03-03
**[FONT=Verdana][B]Linux Disk, USB and LAN Benchmarks (DriveSpeed and LanSpeed)**[/FONT][/B]
 
[FONT=Verdana]Drivespeed tests are for use in benchmarking disk drives, solid state and flash drives connected by SATA, PATA, USB or FireWire buses. Lanspeed benchmarks are to measure wired or wireless network speeds. All the benchmarks are compiled, for 32 bit and 64 bit working, from the same C/C++ code except the LAN benchmarks do no use direct I/O, whereby the data is not transferred via a file cache in main memory. The tests carried out are:[/FONT]
 
[FONT=Verdana]**Writing and Reading Large Files** - Five files each of 8 MB, 16 MB and 32 MB are used. System is instructed not to cache the data (not LanSpeed).[/FONT]
 
[FONT=Verdana]**Writing and Reading Cached Data** - Five files of 8 MB are used. Performance normally reflects memory speed.[/FONT]
 
[FONT=Verdana]**Reading Bus Speed** - The same data is read repetitively at block sizes between 64 KB and 1 MB. This normally reads data from the disk’s buffer to show maximum bus speeds.[/FONT]
 
[FONT=Verdana]**Random Reading Speed** - 1 KB blocks are read randomly from 7 file sizes between 2 MB and 128 MB. Results reflect the disk's buffer size and rotation speed.[/FONT]
 
[FONT=Verdana]**Writing and Reading Small Files** - 500 files are written, read and deleted at 6 different file sizes each between 2 KB and 64 KB. Besides speed, milliseconds per file is provided to reflect overheads.[/FONT]
 
[FONT=Verdana]**Run time parameters** - These are provided to write and read larger files and to specify the drive and file path to be used.[/FONT]
 
[FONT=Verdana]The benchmarks can be downloaded from:[/FONT]
 
[FONT=Verdana][http://www.roylongbottom.org.uk/linux_disk_usb_lan_benchmarks.tar.gz](http://www.roylongbottom.org.uk/linux_disk_usb_lan_benchmarks.tar.gz) [/FONT]
 
 
[FONT=Verdana]For further details and results see:[/FONT]
 
[FONT=Verdana][http://www.roylongbottom.org.uk/linux_disk_usb_lan_benchmarks.htm](http://www.roylongbottom.org.uk/linux_disk_usb_lan_benchmarks.htm) [/FONT]
 
[FONT=Verdana][http://www.roylongbottom.org.uk/linux%20benchmarks.htm](http://www.roylongbottom.org.uk/linux%20benchmarks.htm) [/FONT]
 
[FONT=Verdana]Example log files are attached for a fast eSATA disk drive and a Netbook wireless connection. With these, data transfer speed on writing large files ten times or more faster than for the smallest ones. Supplied results show that USB flash drives can have a much larger difference. [/FONT]
 
[FONT=Verdana]Note that running these Linux tests is more difficult than Windows versions as it is sometimes necessary to force execute and write permissions. Then, with network tests, the files have to be mounted on the local system - folders and file names copied to a temporary directory.[/FONT]
 

[FONT=Verdana]Roy[/FONT]

---

### Post by RoyLongbottom on 2011-08-24
[FONT=Verdana][SIZE=2]**Image Processing Benchmark**[/SIZE][/FONT]
 
[FONT=Verdana][SIZE=2]My Windows image processing benchmark is the latest converted to run under Linux with 32-Bit and 64-Bit compilations using Simple DirectMedia Layer (SDL) functions. The benchmarks generate BMP files and measure speed of saving, loading, scrolling, rotating and editing of 0.5, 1, 2, 4 etc. to 512 MB images. The programs automatically adjust maximum image size used, depending on available main memory, but run time parameters can be used to change this. The execution files, source code, compilation and running instructions can be found in: [/SIZE][/FONT]
 
[FONT=Verdana][SIZE=2][http://www.roylongbottom.org.uk/linux_image_processing_benchmarks.tar.gz](http://www.roylongbottom.org.uk/linux_image_processing_benchmarks.tar.gz) [/SIZE][/FONT]
[FONT=Verdana][SIZE=2]with further details and all results in: [/SIZE][/FONT]
[FONT=Verdana][SIZE=2][http://www.roylongbottom.org.uk/linux%20image%20processing%20benchmarks.htm](http://www.roylongbottom.org.uk/linux%20image%20processing%20benchmarks.htm) [/SIZE][/FONT]
 
[FONT=Verdana][SIZE=2]Systems benchmarked were desktops, a laptop and a netbook using internal and external (eSATA) disk drives plus usb flash memory and disk drives. Linux versions used were 32-Bit and 64-Bit Ubuntu 10.10 with GNOME 2, 64-Bit Ubuntu 11.04 with Unity on two different graphics arrangements, 64-Bit Fedora 14 with GNOME 2 and 64-Bit OpenSuse 11.4 with KDE. [/SIZE][/FONT]
 
[FONT=Verdana][SIZE=2]The enlarge/editing and rotation tests are faster than the Windows version. One main reason is that the programming procedures used for with Windows are not as efficient, whereby additional memory outside the user’s space is used. [/SIZE][/FONT][FONT=Verdana][SIZE=2]On the other hand, scrolling speeds are much slower as SDL (used here) does not use caching in video RAM. Scrolling is the only test where significant speed differences are produced on different Linux distros, but each is fastest on a particular PC. The time to repaint the screen varied between 6 and 10 milliseconds on the fastest PC, with a large screen size. Netbook painting times were between 5 and 11 milliseconds, but the large screen had three times as many pixels. Note that 10 milliseconds equates to 100 Frames Per Second (FPS), adequate with no other timing constraints.[/SIZE][/FONT]
 
[FONT=Verdana][SIZE=2]Results are saved in a text log file and displayed on a Terminal (if used for command line). An Example is below.[/SIZE][/FONT]
 
```

#####################################################################
   Image Editing Speeds 64 Bit Version 1, Sat Aug  6 09:45:47 2011
 
   Input Enlarge    Save    Load  Scroll  Scroll  Rotate  Max MB
   Image Display         Display  Repeat Overall  90 deg  Memory
  Mbytes    Secs    Secs    Secs   msecs  MB/Sec    Secs    Used
 
     0.5    0.02    0.01    0.01    0.83  601.15    0.01   440.2
     1.0    0.02    0.05    0.02    1.63  612.30    0.02   441.9
     2.0    0.02    0.02    0.03    3.31  634.52    0.02   445.4
     4.0    0.03    0.04    0.06    5.66  625.44    0.03   451.6
     8.0    0.05    0.08    0.11    6.73  584.70    0.05   464.7
    16.0    0.09    0.16    0.20    6.77  580.53    0.08   489.5
    32.0    0.16    0.29    0.31    6.70  587.05    0.16   541.1
    64.0    0.29    0.59    0.71    6.94  566.85    0.32   672.4
   128.0    0.59    1.32    1.22    6.64  592.54    0.65   785.3
   256.0    1.14    2.35    2.60    6.63  593.46    3.51  1129.9
   512.0    2.27    4.90    4.73    6.65  591.47    3.91  1822.9
 
               End at Sat Aug  6 09:46:58 2011
 
 #####################################################################
  Configuration Details
 
  Assembler CPUID and RDTSC       
  CPU GenuineIntel, Features Code BFEBFBFF, Model Code 000006F6 
  Intel(R) Core(TM)2 CPU          6600  @ 2.40GHz 
  Measured - Minimum 2402 MHz, Maximum 2402 MHz 
  Linux Functions 
  get_nprocs() - CPUs 2, Configured CPUs 2 
  get_phys_pages() and size - RAM Size  3.87 GB, Page Size 4096 Bytes 
  uname() - Linux, roy-64Bit, 2.6.35-24-generic 
  #42-Ubuntu SMP Thu Dec 2 02:41:37 UTC 2010, x86_64 
 
  Memory stats from /proc/meminfo
     MemTotal:   3963.8 MB   A
      MemFree:   3181.8 MB   B
      Buffers:     46.5 MB   C
       Cached:    297.5 MB   D
 
  Memory Used:    438.0 MB = A - B - C - D
  Current Directory Path (getcwd) and drive space (statvfs): 
  /home/roy/all64/bmpspd
  Total MB   11263, Free MB    9446, Used MB    1817
  See files hd1.txt and hd2.txt for details of drive used
 
  SDL_GetVideoInfo
  hw_available flag is 0 - cannot create hardware surfaces
  Display size 1280 x 1024 pixels at 32 bits
 
  SDL_VideoDriverName = x11
 
  Graphics (command - lspci | grep -i vga > vga.txt)
  VGA compatible controller: nVidia Corporation G84 [GeForce 8600 GT] (rev a1)
 
 #####################################################################
  Files hd1.txt and hd2.txt
 
 Filesystem           1K-blocks      Used Available Use% Mounted on
 /dev/sdb1             11534708   3789268   7159504  35% /
 
 lrwxrwxrwx 1 root root 10 2011-08-06 09:42 scsi-SATA_ST3320613AS-> ../../sdb1
 
 #####################################################################

```

---

### Post by RoyLongbottom on 2011-11-22
[FONT=Verdana][SIZE=2][FONT=Verdana]**OpenGL Benchmark**[/FONT][/SIZE][/FONT]
 
[FONT=Verdana][SIZE=2]My latest benchmark conversion produced programs, videogl32 and videogl64, that are 32-Bit and 64-Bit Linux compilations of OpenGL code used for testing via Windows. Details and results can be found in [/SIZE][/FONT]
 
 
[FONT=Verdana][SIZE=2][http://www.roylongbottom.org.uk/linux%20opengl%20benchmarks.htm](http://www.roylongbottom.org.uk/linux%20opengl%20benchmarks.htm) [/SIZE][/FONT]
 
[FONT=Verdana][SIZE=2]The benchmarks measure graphics speed in terms of Frames Per Second (FPS) via six simple and more complex tests. The first four tests portray moving up and down a tunnel including various independently moving objects, with and without texturing. The last two tests, represent a real application for designing kitchens. The first is in wireframe format, drawn with 23,000 straight lines. The second has colours and textures applied to the surfaces. [/SIZE][/FONT]
 
[FONT=Verdana][SIZE=2]The textures are obtained from 24 bit BMP files that can be up 256 x 256 pixels at 192 KB. The BMP files and Linux execution files can be found in[/SIZE][/FONT]
 
[FONT=Verdana][SIZE=2][http://www.roylongbottom.org.uk/linux_opengl_benchmarks.tar.gz](http://www.roylongbottom.org.uk/linux_opengl_benchmarks.tar.gz) [/SIZE][/FONT]
 
[FONT=Verdana][SIZE=2]along with source code, compilation and running instructions. Windows benchmarks from the same source code are also included. [/SIZE][/FONT]
 
[FONT=Verdana][SIZE=2]The benchmarks were run on a variety of Ubuntu, Fedora and OpenSuse distros and different PC hardware, with nVidia, ATI and Intel graphics. Newly installed Linux systems do not [so far] provide OpenGL hardware acceleration and, except for nVidia, finding such a driver that works with a particular release is seemingly impossible, in some cases. As a default, the benchmark runs using a full screen window, but input parameters allow different sized windows to be used, via Terminal commands or a script file. Following are example log files from tests using a Core 2 Duo CPU and GeForce 8600 GT graphics, using a default driver and one from nVidia. Decreasing performance, as the window size increases, suggests a graphics speed limitation, with constant performance indicating that processor speed is the limiting factor. [/SIZE][/FONT]
 
```

#####################################################################
 
  Assembler CPUID and RDTSC       
  CPU GenuineIntel, Features Code BFEBFBFF, Model Code 000006F6 
  Intel(R) Core(TM)2 CPU          6600  @ 2.40GHz 
  Measured - Minimum 2403 MHz, Maximum 2403 MHz 
  Linux Functions 
  get_nprocs() - CPUs 2, Configured CPUs 2 
  get_phys_pages() and size - RAM Size  3.87 GB, Page Size 4096 Bytes 
  uname() - Linux, roy-64Bit, 2.6.35-24-generic 
  #42-Ubuntu SMP Thu Dec 2 02:41:37 UTC 2010, x86_64 
  Graphics (command - lspci | grep -i vga > vga.txt)
  VGA compatible controller: nVidia Corporation G84 [GeForce 8600 GT] (rev a1)
 
 #####################################################################
 
 Linux OpenGL Benchmark 64 Bit Version 1, Tue Oct 25 18:36:45 2011
          Running Time Approximately 5 Seconds Each Test
 
 Window Size  Coloured Objects  Textured Objects  WireFrm  Texture
    Pixels        Few      All      Few      All  Kitchen  Kitchen
  Wide  High      FPS      FPS      FPS      FPS      FPS      FPS
 
   320   240   3670.2   2326.6   1160.9    678.8    401.0    229.2
   640   480   2463.1   2033.9    896.3    666.3    414.5    231.3
  1024   768   1089.2    987.3    541.6    440.9    401.8    214.6
  1280  1024    727.0    680.8    412.1    338.3    400.2    194.0
 
                   End at Tue Oct 25 18:38:58 2011
 
```
 
 
Roy

---

