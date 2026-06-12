---
title: "swap increased!!!"
date: 2009-11-18
forum: General Help
---

### Post by shaon3343 on 2009-11-18
[SIZE=2]**hi I've installed Ubuntu 9.04 few months ago. At the time of installation the size of my swap was 1.9 GB. and till last few days it showed normally 1.9 GB swap in the system monitor.  Now i surprizingly see that The size of the swap is showing 2.4 GB :o:o:o!!!!  Any idea why this happened? is it related to diskcleanup? please help me knowing that**[/SIZE].

---

### Post by philinux on 2009-11-18
Open a terminal and type

```
free -m
```

Post back what it says.

---

### Post by shaon3343 on 2009-11-18
**here it is: **
shaon@shaon-desktop:~$ free -m
             total       used       free     shared    buffers     cached
Mem:          2003        670       1332          0         39        270
-/+ buffers/cache:        360       1643
Swap:         2406          0       2406
shaon@shaon-desktop:~$

---

### Post by khelben1979 on 2009-11-18
If the swap is made like a dynamic file I sure can understand how it has been able to grow.

I always choose to create a harddrive partition for swap only myself.

---

### Post by philinux on 2009-11-18
> **shaon3343 said:**
> **here it is: **
```
shaon@shaon-desktop:~$ free -m
             total       used       free     shared    buffers     cached
Mem:          2003        670       1332          0         39        270
-/+ buffers/cache:        360       1643
Swap:         2406          0       2406
```
shaon@shaon-desktop:~$

Well there it is 2.4 gig but none used. 

```
sudo fdisk -l
```

---

### Post by ricardo.gloe on 2009-11-18
try ```
ls /dev/r*
``` and post the results. I seem to remember a time I had a swap issue where I also had an additional 500mb, and depending on the results, I can see if it's the same problem.

---

### Post by shaon3343 on 2009-11-18
> **ricardo.gloe said:**
> try ```
ls /dev/r*
``` and post the results. I seem to remember a time I had a swap issue where I also had an additional 500mb, and depending on the results, I can see if it's the same problem.
** here it is: **
shaon@shaon-desktop:~$ ls /dev/r*
/dev/ram0   /dev/ram12  /dev/ram2  /dev/ram6  /dev/ramzswap0
/dev/ram1   /dev/ram13  /dev/ram3  /dev/ram7  /dev/random
/dev/ram10  /dev/ram14  /dev/ram4  /dev/ram8  /dev/rtc
/dev/ram11  /dev/ram15  /dev/ram5  /dev/ram9  /dev/rtc0
shaon@shaon-desktop:~$

---

### Post by ricardo.gloe on 2009-11-18
Yep, same problem. I don't know how it got on my computer either...

Anyway, have a look at [http://code.google.com/p/compcache/](http://code.google.com/p/compcache/) for more information on it. 

I removed it following post #4 from the following thread: ttp://ubuntuforums.org/showthread.php?p=7268741

---

