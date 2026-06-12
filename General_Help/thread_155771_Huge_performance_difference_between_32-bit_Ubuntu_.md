---
title: "Huge performance difference between 32-bit Ubuntu and 64-bit FC3?"
date: 2006-04-05
forum: General Help
---

### Post by ZAxisMapping on 2006-04-05
Hello, for my work, I use two computers.  One machine I SSH into with a 7200 RPM IDE drive and FC3 x86_64:

```
$ uname -a
Linux dev 2.6.12-1.1381_FC3 #1 Fri Oct 21 03:57:59 EDT 2005 x86_64 x86_64 x86_64 GNU/Linux
```


The other is a Breezy Badger 5.10 32-bit, with 10K Raptor SATA that I run in gnome:

```
$ uname -a
Linux raster 2.6.12-10-386 #1 Sat Mar 11 16:13:17 UTC 2006 i686 GNU/Linux
```

My question is: why am I experiencing such horrible performance with standard GNU apps under the Ubuntu machine (which _completely_ dominates the other in every hardware component)?

In FC3:

```
$ time grep 'string' 50MB_file > out

real    0m0.114s
user    0m0.050s
sys     0m0.063s

```

Under ubuntu:

```
$ time grep 'string' SAME_50MB_file > out

real    1m35.205s
user    1m34.475s
sys     0m0.229s

```

They produce the same file, but damn, that's not even close.  They both have the same version of grep on each.  Furthermore, when I use "more" and page down through the same file...my gnome-terminal is updated MUCH faster *over the network* from the FC3 machine than on my own local file system under Ubuntu!!!  It's jerky and slow on each page down.  So, I believe this has something to do with I/O, but my Ubuntu machine should destroy the IDE FC3 one, but it's totally not.  Does it have anything to do with bigger memory access on the FC3 x86_64?

Any ideas???


PS - there is no RAID on either system and both are ext3.

---

### Post by ZAxisMapping on 2006-04-05
Sorry to reply to my question, but I discovered "hdparm" and tested it out.  The results are consistent with what I would expect hardware-wise - the Ubuntu machine should be much faster...but why would a basic grep command take so much longer?  

Does anyone have any ideas on what would be causing these issues on my Ubuntu machine?  Seems like it would be a software problem somewhere...


On 7200 RPM IDE, FC3:

```
# /sbin/hdparm -Tt /dev/hda

/dev/hda:
 Timing cached reads:   2672 MB in  2.00 seconds = 1335.54 MB/sec
 Timing buffered disk reads:  158 MB in  3.01 seconds =  52.41 MB/sec
```


On 10K Raptor SATA, Ubuntu 5.10 32-bit:

```
$ sudo hdparm -Tt /dev/sdb
Password:

/dev/sdb:
 Timing cached reads:   3056 MB in  2.00 seconds = 1527.47 MB/sec
 Timing buffered disk reads:  252 MB in  3.02 seconds =  83.51 MB/sec
```

---

### Post by nw15062 on 2006-04-05
On one system you are using a kernel compiled for X86_64 and on the other you are using a 386 Kernel, the 386 kernel has many limiting factors including how much ram is accessible, for people with over 800megs it is recommended you use the 686 kernel.

There are many features in modern processors that are not taken advantage of with a 386 kernel, that are functional in a 686.

Not to mention a 64 bit bus is considerably fast the a standard 32 anyday, despite there clock speed.

---

### Post by mrazster on 2006-04-05
I honestly don't have a clue why it is so much slower.
However I can provide you with my info...for comparison.

NF3 / FX55 / 2x1gb / Maxtor 300GB 16mbcache IDE

> 2.6.12-10-386

```
/dev/hda
Timings cached reads: 3936 MB in 2.00 seconds = 1967.32 MB/sec
Timing buffered disk reads: 182 MB in 3.02 seconds = 60.29 MB/sec
```

---

### Post by ZAxisMapping on 2006-04-05
Thank you for the quick replies and suggestions!

First off, I upgraded the kernel:

```
$ uname -a
Linux raster 2.6.12-10-686-smp #1 SMP Sat Mar 11 16:41:12 UTC 2006 i686 GNU/Linux
```

I have no idea why 386 was installed to begin with (not only that, but this is a dual core 64bit chip).  You may ask why I'm not running amd64 Ubuntu...I was, but I need to run so many 32 bit apps that it was becoming a nightmare (I love FC's 32 bit subsystem)....

Anyway, with the new kernel, I still get bad performance with the grep, but one thing I did notice was that performance varied greatly on the partitions...and unfortunately, for sdb5 (my OS partition), it is slower:

```
$ sudo hdparm -Tt /dev/sdb5

/dev/sdb5:
 Timing cached reads:   2808 MB in  2.00 seconds = 1402.81 MB/sec
 Timing buffered disk reads:  170 MB in  3.01 seconds =  56.54 MB/sec

```

However, this is dissapointing in itself, but it is in the same ballpark as the FC machine with inferior hardware.  In other words, I'm still a little confused...I would expect to get at least similar results....

PS - it seems crazy that I should see such a difference in performance on partitions, because I thought the number of blocks varies according to the cylinder location on the platter....ie, it shouldn't matter.

---

### Post by nw15062 on 2006-04-05
Keep in mind that FC3 is alot slimmer then Ubuntu 5.10

If I were to run windows 3.1 on my P4 HT it would run much faster then Windows XP

The real diffence is the support in the kernel compared to size of the kernel.

Plus you have a 64bit cpu trying to emulate a 32bit, I can run NES games on my palm where the NES was inferior to my palm but they run slower and look worse then palm games.

What you really need is ZEN, have the main kernel 64bit but run a virtualized 32 bit kernel for 32 bit applications.

Another thing to mention is have tried running the K7 Kernel for AMD chips rather then the 686 for Intel?

---

### Post by dcstar on 2006-04-05
[QUOTE=ZAxisMapping]Thank you for the quick replies and suggestions!

First off, I upgraded the kernel:

```
$ uname -a
Linux raster 2.6.12-10-**686-smp** #1 SMP Sat Mar 11 16:41:12 UTC 2006 i686 GNU/Linux
```

I have no idea why 386 was installed to begin with (not only that, but this is a dual core 64bit chip).  You may ask why I'm not running amd64 Ubuntu...I was, but I need to run so many 32 bit apps that it was becoming a nightmare (I love FC's 32 bit subsystem)....
.......[/QUOTE]
I would be very wary of running a SMP kernel made for Intel processors on an AMD CPU.

If you are going to use an AMD CPU, use an AMD K7 kernel.

---

### Post by ZAxisMapping on 2006-04-05
Okay, thanks again for clueing me in!  I now have the following:

```
$ uname -a
Linux raster 2.6.12-10-k7-smp #1 SMP Sat Mar 11 17:18:23 UTC 2006 i686 GNU/Linux

```

with the latest nvidia drivers working.  

The odd thing is that the same grep command again takes just as long.  One of the two cores is 100% for the duration of the command.  I find it really hard to believe that there would be such huge discrepancies in the running times of basic GNU apps across different distros (granted I'm comparing 32bit OS on a 64bit processor vs 64bit on 64bit processor).  But, it's a huge difference....doesn't this seem odd?

I'll look into ZEN this weekend when I get more time.

---

### Post by dcstar on 2006-04-06
[QUOTE=ZAxisMapping]
.......
The odd thing is that the same grep command again takes just as long.  One of the two cores is 100% for the duration of the command.  I find it really hard to believe that there would be such huge discrepancies in the running times of basic GNU apps across different distros (granted I'm comparing 32bit OS on a 64bit processor vs 64bit on 64bit processor).  But, it's a huge difference....doesn't this seem odd?

I'll look into ZEN this weekend when I get more time.[/QUOTE]
Ubuntu optimises its resources for single user performance, other distros might default to settings that give more resources to things like disk caching etc.

As an example, I have the following in my boot string to improve response in my Ubuntu system when other processes need to do disk I/O:
```
kernel		/boot/vmlinuz-2.6.12-10-k7 root=/dev/hda4 ro quiet **elevator=cfq**
```
There could well be other Ubuntu "tweaks" that could make a difference to the grep test (but I don't know of them........)


Having now done some kernel compilation and configuration recently, I can say with confidence that Ubuntu is "tweaked" towards desktop responsiveness above possible "under the hood" performance.

If you get hold of the new 2.6.16 kernel, you may be able to experiment with various kernel settings to see what effect they may have on you grep test, I'm sure the server based optimisation would help over the desktop one.

---

