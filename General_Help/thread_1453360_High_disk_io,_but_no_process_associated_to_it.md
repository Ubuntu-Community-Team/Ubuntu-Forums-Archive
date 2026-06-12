---
title: "High disk io, but no process associated to it"
date: 2010-04-13
forum: General Help
---

### Post by AlexBcn on 2010-04-13
Hi all,

I have a continous disk read in Ubuntu 9.10 after some hours of use. Initially it's normal.

I am using VMware, so I thought it may be behind it, but a "iotop" command shows an total disk read of ~10MB/s and any process reading more than some 30-40 Kb/s.

I have 4GB or RAM. The system monitor reports 1.9GB used and only 28kb of SWAP. 2 CPU stay below 50% usage.

free-m returns this:
------------------------------------------------------
             total       used       free     shared    buffers     cached
Mem:          3964       3919         44          0        336       1584
-/+ buffers/cache:       1998       1966
Swap:         4000          0       4000
------------------------------------------------------

Do you have any clue why the disk is moving so much?

Many thanks in advance.

---

### Post by warfacegod on 2010-04-13
How old is the HDD? It could be continuosly seeking the the disk for sectors that aren't bad. If it's a drive that you used on Windows, it could be highly fragmented if you left your files intact.

---

### Post by AlexBcn on 2010-04-13
Hi warfacegod,

thanks for you answer.

The HDD is 2 years old, and I am accessing a ext3 file system.

The only "odd" thing here may be than I am running a guest winXP VM in VMware, which has mapped the host linux ext3 file system. Anyway, XP shows 95% cpu free.

When I start running the VM, the total disk read is about 2MB/s, later on stays in aprox. 10MB/s. But strangely, any process seems to be reading.

---

### Post by warfacegod on 2010-04-13
Is VMware set to start automatically? I know virtually nothing about running... Virtual Machines (wished I'd thought that sentence out a little more:P). It seems to me that idling a Virtual Machine in the background could easily cause your I/O problems.

Try checking Startup Applications.

---

### Post by AlexBcn on 2010-04-13
Hi again,

I start the VM manually, and I have tried to close all other user applications (browser, etc.) and let the VMware on the foreground, but the disk IO keeps the same.

I don't know how to look further, since if the disk works hard and  "iotop" shows a high TOTAL DISK READ but no process seems to read... I get puzzled!

Thanks.

---

### Post by warfacegod on 2010-04-13
I'm out of ideas. I take it that it only does this when VMware is running?

---

