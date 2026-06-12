---
title: "Why systems get slow when writting to disk?"
date: 2010-01-18
forum: General Help
---

### Post by leandromartinez98 on 2010-01-18
This is a curiosity of mine, and I expect a technical answer, if someone knows it. Why the systems become so irresponsive when doing hard-disk input and output? This happens even if writing is done to a secondary disk where neither the system or the swap are stored.

---

### Post by tgalati4 on 2010-01-18
Depending on what you are doing and how much RAM you have, yes, disk access is slow.

For instance, I run Firefox from a ramdisk because it slows down the browser to write all of those cache files.

If you run out of RAM, and start using swap, then your system will slow to a crawl.  It won't crash, but you will get impatient, waiting for things to happen.

In a terminal, post the output of:

free

---

### Post by leandromartinez98 on 2010-01-18
I don't think I'm close filling my RAM (as you can see, I have 2.5gb free, and I'm not using swap, mostly). 

At this moment I'm transferring data through the network at a 10Mb/s rate, to a second hard-drive on my machine. The machine is usable, but it gets quite slow. Since this transfer does not use CPU to much and since my RAM is free, and the system/swap disk is not being used, how come the system gets so much slower? It gets much slower than if I run procs that consume 100% of my CPUs.


```

             total       used       free     shared    buffers     cached
Mem:       3800308    3718712      81596          0       8308    2491584
-/+ buffers/cache:    1218820    2581488
Swap:      3943948     362252    3581696

```

---

### Post by tgalati4 on 2010-01-18
I presume that you have an old 10 Mb/sec network card in your system?  That will be a bottleneck.  Linux expects infinitely fast memory, disk, and network I/O.  A slow link any any one of those can impact overall performance.

Output:

cat /proc/interrupts

Also:

sudo apt-get install htop
htop

---

### Post by leandromartinez98 on 2010-01-18
I don't think so, my machine is not old, and the network is gigabit (but not connected to an overall gigabit network in this case, of course).

But actually I'm asking from a more general point of view, the behaviour of my machine now is not particularly bad. The very high penalty on performance when writing/reading disks is something that I always usually observe (on Linux or anything else). Meaning, I don't think I have a problem, I just curious about this specific behaviour of computers in general. 

In this case was particularly intrigued since the disk being written is not even the disk that must be accessed for system stuff. I don't understand why this causes a penalty on performance at all.


```

          CPU0       CPU1       CPU2       CPU3       
  0:         24          0          4       1711   IO-APIC-edge      timer
  1:          0          0        424     331234   IO-APIC-edge      i8042
  4:          0          0          0          2   IO-APIC-edge    
  6:          0          0          0          5   IO-APIC-edge      floppy
  7:          1          0          0          0   IO-APIC-edge      parport0
  8:          0          0          0          1   IO-APIC-edge      rtc0
  9:          0          0          0          0   IO-APIC-fasteoi   acpi
 12:          0          0          0        267   IO-APIC-edge      i8042
 14:          0          0          0          0   IO-APIC-edge      pata_atiixp
 15:          0          0          0          0   IO-APIC-edge      pata_atiixp
 16:          4         10       2830    1576319   IO-APIC-fasteoi   ohci_hcd:usb3, ohci_hcd:usb4, HDA Intel
 17:          0          0        150     110647   IO-APIC-fasteoi   ehci_hcd:usb1
 18:          0          0          0          3   IO-APIC-fasteoi   ohci_hcd:usb5, ohci_hcd:usb6, ohci_hcd:usb7
 19:          0          0          0          0   IO-APIC-fasteoi   ehci_hcd:usb2
 24:   59643354          0          0          0  HPET_MSI-edge      hpet2
 26:          0          2       3007     840589   PCI-MSI-edge      ahci
 27:          0        115      69663  126032722   PCI-MSI-edge      eth0
 28:          0          0          0          0   PCI-MSI-edge      fglrx[0]@PCI:1:5:0
NMI:          0          0          0          0   Non-maskable interrupts
LOC:         62   52873672   50856138   49953667   Local timer interrupts
SPU:          0          0          0          0   Spurious interrupts
CNT:          0          0          0          0   Performance counter interrupts
PND:          0          0          0          0   Performance pending work
RES:  490397435  496464999  494952109  486165931   Rescheduling interrupts
CAL:       1792       1856       1995       1082   Function call interrupts
TLB:      87366      87019      82485      31935   TLB shootdowns
TRM:          0          0          0          0   Thermal event interrupts
THR:          0          0          0          0   Threshold APIC interrupts
MCE:          0          0          0          0   Machine check exceptions
MCP:       1716       1716       1716       1716   Machine check polls
ERR:          5
MIS:          0


```

---

### Post by tgalati4 on 2010-01-18
You can run the phoronix benchmarks and compare what others are getting for throughput with similar architecture.

I recently put Ubuntu Hardy server on an old Dell Poweredge 1750.  The disk throughput for a single 10K rpm SCSI disk is only 66MB/sec.  With RAID you can double or triple that depending on configuration.  That is one of the reasons to use RAID, to get over that slow link.

Checking the rest of the I/O on the poweredge, I routinely get 3-7 GB/sec transfer between RAM, L2 cache, and the 128 MB RAID cache.  So disk access is super slow compared to the rest of the system.

I don't know what your hardware is, but I would look at your rescheduling interrupts.  They seem high.  What process is causing all of those rescheduling interrupts?

---

### Post by leandromartinez98 on 2010-01-18
The moment I checked /proc/interrups I was running a 4-CPU parallelized job, so it may be the cause of those interrupts. I don't think that anything is wrong here. For instance, when updating the database (updatedb), don't you all get a much less irresponsive system? Why is that, even in 4-cpu machines (updatedb uses only one) and even with lots of RAM memory available? What is that a disk transfer requires that the actual interface with the user also requires? Cache?

---

### Post by tgalati4 on 2010-01-18
There are certain bad actors:  slocate database, synaptic/apt database, beagle/tracker database

Those processes can can cause the system to feel slow.  You would have to get into the code and do some profiling to determine the bottlenecks.

Using htop, those types of processes cause lots of I/O waits which reduce the "hands-on" speed.

Running firefox from a ramdisk gives an improvement for browsing.  You could isolate those bad actors and write scripts to run them in a ramdisk as well.

Also examine dmesg for any hardware or I/O errors.  Sometimes one piece of hardware can cause issues for the entire system.

Of course, it could be a bug:

[http://ubuntuforums.org/showthread.php?t=1367951](http://ubuntuforums.org/showthread.php?t=1367951)

---

