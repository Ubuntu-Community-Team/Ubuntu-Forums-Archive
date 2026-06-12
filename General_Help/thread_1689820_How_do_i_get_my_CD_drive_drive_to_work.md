---
title: "How do i get my CD drive drive to work?"
date: 2011-02-17
forum: General Help
---

### Post by Macfunky on 2011-02-17
I have two computers running Ubuntu, one running Lucid, the other Maverick. I have the same problem on both computers, they won't recognise any CD's or DVD's. How do i go about getting them to work? When i go to the computer folder on both computers i see a CD drive icon but it does nothing. How can i find out if either of them are being recognised and how to get them working. They are both powered and i check the IDE connection on the back of both of them. No problems there. Any help would be great. Cheers :)

EDIT : Forgot to mention that the drive doesn't show up in devices.

---

### Post by quixote on 2011-02-18
Is this a USB CD drive that neither computer will recognize?  If so, my first thought would be a problem with the drive.  

If not, then it's weird.  Both Lucid and Maverick recognize all sorts of media, certainly CDs and DVDs, with no trouble.  If it's a removable drive, plug it in and power it up.  Then open a terminal (Applications > Accessories > Terminal) and type```
sudo fdisk -l       *("l" as in "list")*
```Does it show up in that list?

---

### Post by Macfunky on 2011-02-19
It's not a USB drive. It is an internal IDE drive. I have changed it for one i know worked on a previous version version of Ubuntu and i have the same issue with it. It's very odd. 

Output from sudo fdisk -l -

Disk /dev/sda: 300.1 GB, 300069052416 bytes
255 heads, 63 sectors/track, 36481 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00013ca5

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       35355   283987968   83  Linux
/dev/sda2           35356       36482     9046017    5  Extended
/dev/sda5           35356       36482     9046016   82  Linux swap / Solaris

---

### Post by quixote on 2011-02-21
That fdisk doesn't show any sign of recognizing it is bad.  I wonder if the HD cable or one of the sockets it plugs into could be bad?  It sure sounds like the problem is with the computer itself, not the drive.  But if it's a software/OS problem, ie Ubuntu, I could see maybe an incompatibility with a specific drive, but it's not going to have trouble with all drives. Ubuntu recognizes CD drives, and even if there are issues, it'll show up in fdisk.  Which leaves some sort of hardware issue....

---

