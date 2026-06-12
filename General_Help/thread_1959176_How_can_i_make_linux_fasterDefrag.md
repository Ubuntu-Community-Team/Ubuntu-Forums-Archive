---
title: "How can i make linux faster?Defrag?"
date: 2012-04-15
forum: General Help
---

### Post by davidftechman on 2012-04-15
How can i speed up my linux distro(XUBUNTU) to get the best speed as possible and how do i defrag do i need to and how?

---

### Post by roelforg on 2012-04-15
> **davidftechman said:**
> How can i speed up my linux distro(XUBUNTU) to get the best speed as possible and how do i defrag do i need to and how?

New linuxer, am i right???
Defrag is something only needed on windows systems.
You can try:
(assuming /dev/sda is your install hd)
```

sudo fsck /dev/sda

```
And see what boots up with you,
try unity 2d instead of 3d and so on.

---

### Post by JazzPotato on 2012-04-15
Linus dosn't need defragmenting:
[http://geekblog.oneandoneis2.org/index.php/2006/08/17/why_doesn_t_linux_need_defragmenting](http://geekblog.oneandoneis2.org/index.php/2006/08/17/why_doesn_t_linux_need_defragmenting)

---

### Post by snowpine on 2012-04-15
First you must tell us about your hardware (RAM, CPU, Video card, etc.)

Then you must define in what way is your computer "slow:" Slow to boot? Slow to launch applications? Slow to calculate large spreadsheets? 

Finally you can launch the terminal command **top** to analyse your CPU and RAM usage and make an informed decision how to speed up your system. 

Looking forward to your reply.

---

### Post by matt_symes on 2012-04-15
Hi

> Defrag is something only needed on windows systems.> Linus dosn't need defragmenting:It is not entirely true that extX file system do not suffer from fragmentation. 

Files themselves can become fragmented although it tries to keep the filesystem meta-structures such as the inodes and dentries unfragmented.

See this file below for fragmentation.

```

matthew@matthew-Aspire-7540:~$ filefrag lawerence_krauss 
lawerence_krauss: 5 extents found
matthew@matthew-Aspire-7540:~$ 
```It's not so much of a problem under extX as on FAT32 or NTFS so i would not worry about it. This clarifies the above two quotes

Kind regards

---

### Post by davidftechman on 2012-04-15
> **snowpine said:**
> First you must tell us about your hardware (RAM, CPU, Video card, etc.)

Then you must define in what way is your computer "slow:" Slow to boot? Slow to launch applications? Slow to calculate large spreadsheets? 

Finally you can launch the terminal command **top** to analyse your CPU and RAM usage and make an informed decision how to speed up your system. 

Looking forward to your reply.
```
top - 14:25:01 up  2:26,  0 users,  load average: 1.03, 0.45, 0.37
Tasks: 135 total,   1 running, 129 sleeping,   0 stopped,   5 zombie
Cpu(s):  1.8%us,  0.7%sy,  0.0%ni, 97.5%id,  0.0%wa,  0.0%hi,  0.0%si,  0.0%st
Mem:    762216k total,   690004k used,    72212k free,   122556k buffers
Swap:   262136k total,    59456k used,   202680k free,   204740k cached
```

it is slow opening apps

---

### Post by snowpine on 2012-04-15
> **davidftechman said:**
> it is slow opening apps

Faster hard drive or SSD is the solution. (More RAM wouldn't hurt either.)

---

### Post by davidftechman on 2012-04-15
> **snowpine said:**
> Faster hard drive or SSD is the solution. (More RAM wouldn't hurt either.)
k thanks

---

### Post by snowpine on 2012-04-15
Also you forgot:

> **snowpine said:**
> First you must tell us about your hardware (RAM, CPU, Video card, etc.)

---

### Post by davidftechman on 2012-04-15
> **snowpine said:**
> Also you forgot:
768 mp of ram amd anthlon x2 dual core processor 1.90 ghz
ati radeon x1250

---

### Post by snowpine on 2012-04-15
That is a pretty fast computer; I am surprised Xubuntu is running slow. Do a forum Search on your video card and check that you're using the correct drivers.

---

### Post by davidftechman on 2012-04-15
> **snowpine said:**
> That is a pretty fast computer; I am surprised Xubuntu is running slow. Do a forum Search on your video card and check that you're using the correct drivers.
will do

---

### Post by wyliecoyoteuk on 2012-04-15
Top shows the average loads, a dual core processor counts as 2.0, so even the peak load of 1.05 is not high, a load of 1.5 is reasonable.
Launching apps, the speed is probably due to the HDD, but more memory (1Gb or more) might help.
If it is 768 Mb, the Ram is probably mismatched modules (512+256)as well.
Ram is cheap at the moment, a pair of matched sticks (i.e. 2x512MB) preferably identical to allow double data rate, will be quicker.

---

