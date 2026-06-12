---
title: "Windows 7 installed - But Ubuntu says no?"
date: 2011-05-25
forum: General Help
---

### Post by Roasted on 2011-05-25
I'm trying to set up dual boot... as I've done dozens of times... I installed Windows 7 on one partition leaving 30gb unallocated for Ubuntu, but in the partitioning menu it says 100% unallocated. How can I get it to see Windows so I can properly dual boot?

---

### Post by wildmanne39 on 2011-05-25
> **Roasted said:**
> I'm trying to set up dual boot... as I've done dozens of times... I installed Windows 7 on one partition leaving 30gb unallocated for Ubuntu, but in the partitioning menu it says 100% unallocated. How can I get it to see Windows so I can properly dual boot?Hi, this guide should get you going. [http://members.iinet.net.au/~herman546/p18.html](http://members.iinet.net.au/~herman546/p18.html)

---

### Post by Roasted on 2011-05-26
To be honest, I'm not entirely sure what in that link is relevant to my issue. But I may just be absent minded and missing something as I read over it.

Just to re-hash a little but, I have a 250gb drive. My end goal here is to have:

1x250 - Windows 7 + 30gb Ubuntu root

2x1TB - Software Raid for Ubuntu home

I just have the 250 plugged in now, and I installed Windows 7 just fine. I admit, I did use the Windows partitioner, though. Disk management in W7 shows up with 100mb reserved/210gb Windows/30gb unallocated, however GParted (both older and the newest version) says /dev/sda1 is 100% unallocated with no partitions.

I do have to admit, I have two 250s, and I remember one being bad. I had used them on a usb bridge before and one kept giving me issues. I thought I marked which one it is, but maybe I picked the bad one without realizing it. After all, in the past Windows hasn't been the quickest to detect failing hard drives. One time I had dual boot on a bad hard drive and Ubuntu would notify the crap out of me that SMART data failed while Windows 7 had no idea.

That may be it... I'll try later. Has anybody heard of this case I posted above but with a GOOD drive, just to generate some fix ideas in case that's it?

---

### Post by gandaran on 2011-05-26
> **Roasted said:**
> I'm trying to set up dual boot... as I've done dozens of times... I installed Windows 7 on one partition leaving 30gb unallocated for Ubuntu, but in the partitioning menu it says 100% unallocated. How can I get it to see Windows so I can properly dual boot?
hi
can you see the windows files/partition from ubuntu?
if the boot windows 7 option is missing from grub then something is wrong with the disk setup, do you still have the 100MB windows 7 loader partition on disk?
try running _sudo update-gru_b from ubuntu, if it can detect windows it will fix the grub menu.
or post a screenshot of gparted, that would help figure it out.
for grub repair you can use [rescatux]("http://www.bootproblems.com/rescatux/"), rescatux can detect all OS and fix grub accordingly.

---

### Post by srs5694 on 2011-05-26
You've probably got one of the problems described [here.]("http://www.rodsbooks.com/missing-parts/index.html") (Sorry, that page is a bit too verbose and klunky; I need to rewrite it.) If so, chances are my [FixParts]("http://www.rodsbooks.com/fixparts/") program will fix the problem. I can't promise that, though; there are other possible causes. For a more detailed diagnosis, please run the following command from an Ubuntu boot (including the installer in "live CD" mode):

```
sudo fdisk -lu
```

Post the results here, between [noparse]```
[/noparse] and [noparse]
```[/noparse] tags.

---

### Post by Roasted on 2011-05-27
Thanks. I'll try that next opportunity I get. Is this a problem with my actual hard drive? I have NEVER seen it before, but these 250gb drives were always just raw data backups and never had an OS on them.

By the way - I was not using the faulty 250gb drive. I was using the working drive.

I'm tempted on putting my 160gb drive in there to see how it does...

---

### Post by srs5694 on 2011-05-27
If my hypothesis is correct it's a problem with the partition table (data) on the disk, not a physical fault with the disk. I can't promise I'm right, though; it's conceivable you've got a hardware fault that's producing similar symptoms.

---

### Post by Roasted on 2011-05-31
Hmm. I ended up fixing it in a strange way. On a hunch when I installed Windows 7 and set up the partitioning, I set it up like:

100mb NTFS (Windows Reserve)
200gb NTFS (Windows OS)
30gb  NTFS (Blank)

Once done I booted up Ubuntu and I could see all 3 partitions. I ended up just formatting the 30gb NTFS partition to EXT4 and I'm good to go now. How strange...

---

