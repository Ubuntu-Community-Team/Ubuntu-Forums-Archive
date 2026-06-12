---
title: "dual boot ubuntu =D  and windows =/"
date: 2009-08-21
forum: General Help
---

### Post by lmm5247 on 2009-08-21
i start school monday and i need to have microsoft project 2007 installed. problem is, i haven't run windows on my laptop in forever.

i was planning on dual booting but had a question about where to put my stuff that totals 80gb in size.



should i place all my files in the ubuntu partition of the drive?

or in the windows partition and then mount the windows partition from within ubuntu when i need my files? 

the upside to the second method is that i get to access my files in both operating systems without the need to reboot. is that a good idea? or will it slow things down?

thanks

---

### Post by lildigiman on 2009-08-21
I have a third(and fourth actually, also) partition, which I call "Documents" which holds everything that isn't a program or system file.

That makes it VERY easy for Ubuntu and Windows to read.

It has to be NTFS though (no ext3 or 4).

Hope this helps.

---

### Post by lmm5247 on 2009-08-21
> **lildigiman said:**
> I have a third(and fourth actually, also) partition, which I call "Documents" which holds everything that isn't a program or system file.

That makes it VERY easy for Ubuntu and Windows to read.

It has to be NTFS though (no ext3 or 4).

Hope this helps.


you can do that?! thats genius! :D

how would i do that? install windows, then ubuntu, then create another partition out of the free space? 

what kind of software would i use to do this? the partition manager when i'm installing ubuntu?

---

### Post by lildigiman on 2009-08-21
First install Windows, as you normally would, then Install Ubuntu, and in the partition editor that appears during install, choose "CUSTOM" and create up to 4(four) partitions if you would like to do so, on a single drive. Make sure to keep the Windows Partition.

Be careful though, if you have data on the drive already that you want to keep (or even if you don't) you might want to google how to use the partition editor before doing anything.

---

### Post by JC Cheloven on 2009-08-21
> **lildigiman said:**
> First install Windows, as you normally would, then Install Ubuntu, and in the partition editor that appears during install, choose "CUSTOM" and create up to 4(four) partitions if you would like to do so, on a single drive. Make sure to keep the Windows Partition.

Be careful though, if you have data on the drive already that you want to keep (or even if you don't) you might want to google how to use the partition editor before doing anything.

As far as I can remember, when you install windoze it will use the whole disk. If you are presented with a menu for partitioning, be sure to make a partition of the desired size for windows (don't run the defaults). It may be difficult to 'persuade' windows to leave the disk space once it has got it (I ran into this problem several times).

Just to be sure, I would add a first step: boot from ubuntu live cd, start gparted and partition the whole disk as desired. 
[INDENT]Just an example: if your hd is 180Gb, make a first 40Gb ntfs partition for windows, a second 140Gb ntfs (or fat32) for your data, a third 36Gb for ubuntu, and a fourth ~2Gb swap with the remaining space. [/INDENT]
Then install win, ub, in that order, in their prepared partitions.
 
note: if you want more than 4 partitions you'll need to do a special thing (a kind of container partition called "extended partition").

---

### Post by jrox717 on 2009-08-22
Just so you know, if you already have Ubuntu on your computer, you don't need to reinstall (though you should back everything up, just in case!) Partition your disk with gParted (you can make a shared NTFS partition now, too), then install Windows in the unallocated space (take careful note of the partition sizes). Then, restore grub:

> 
1. Pop in the Live CD, boot from it until you reach the desktop.
2. Open a terminal window or switch to a tty.
3. Type "grub"
4. Type "root (hd0,6)", or whatever your harddisk + boot partition numbers are (my /boot is at /dev/sda7, which translates to hd0,6 for grub). (( a = 0, b = 1, etc; 1 = 0, 4 = 3, etc))
5. Type "setup (hd0)", ot whatever your harddisk nr is.
6. Quit grub by typing "quit".
7. Reboot. 

[http://ubuntuforums.org/archive/index.php/t-24113.html](http://ubuntuforums.org/archive/index.php/t-24113.html)

---

### Post by lmm5247 on 2009-08-30
thanks to everyone for their help =)

after many trials heres how i did it:

using the system restore discs that came with my laptop i was presented with an option to recover to a custom partition size, i chose 45GB.

then, i used windows built-in disk management tool to format the remaining free space as ntfs.

then, i installed ubuntu and using the sliders on the partition manager, chose a 40GB space for ubuntu, leaving the other 100GB for my stuff.

thanks again everyone =)

---

