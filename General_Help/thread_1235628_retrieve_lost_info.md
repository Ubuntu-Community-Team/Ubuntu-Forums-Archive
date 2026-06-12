---
title: "retrieve lost info"
date: 2009-08-09
forum: General Help
---

### Post by crunkenstein on 2009-08-09
Hi, I recently switched from Vista to Ubuntu and I have both partitioned on my harddrive. First I downloaded the boot iso and used daemon tools to start it up. I chose the option to install Ubuntu like a program without a dedicated partition. Later, I decided to fully install. My computer had 3 partitions, 2 of which showed up as drives. I was using C:ACER (I have an Extensa 4420) and left D:DATA unused as I thought it was for backups/recovers. It turns out my recovery data is actually on the first partition which doesn't show up as a drive. I deleted D, created a small partition for the iso (so I could install diskless) and rebooted. All seemed to be going pretty well. It's been a few days and I've encountered some major problems.

1. I don't know how to access the data from the first partition-free Ubuntu installation (ie .txt documents I saved to the desktop.)

2. I can no longer operate Windows Vista. When I start it fires up the recovery program from the first partition. I suspect this problem started when I used the Ubuntu explorer to open a file in C:ACER then saved my changes because the two partitions have different formats. I read that messing with NTSF (sp?) files could be dangerous but in hindsight I really had no idea what I was getting into. Is there something I can do like delete the altered file?

I consider the first problem of much greater importance than the second. Does anyone have any advice?

---

### Post by Barafu Albino Cheetah on 2009-08-09
don't panic and think what you do. But at first, show us what fdisk -l /dev/sda (or whatever your HDD is) shows.

---

### Post by crunkenstein on 2009-08-09
*breath* I couldn't get the command you suggested to open anything. Reponses ranged from 'unable to open' to 'permission denied'

walt@Blackbird:~$ fdisk

Usage: fdisk [-l] [-b SSZ] [-u] device
E.g.: fdisk /dev/hda  (for the first IDE disk)
  or: fdisk /dev/sdc  (for the third SCSI disk)
  or: fdisk /dev/eda  (for the first PS/2 ESDI drive)
  or: fdisk /dev/rd/c0d0  or: fdisk /dev/ida/c0d0  (for RAID devices)
  ...
walt@Blackbird:~$ 

My partition is in a grid kind of like this. Kin?d of ugly but I hope it helps?

partition||filesystem||mount point||label||size||used||unused||flags

unalloca||unalloca||
dev/sda1||fat32.....||.................||PQGRID||...||...||...||boot
dev/sda2||ntfs.......||media/ACER||ACER
unalloca||unalloca||
dev/sda4||extended||
dev/sda5||ext3......||/
dev/sda6||linux_swap||
dev/sda6

---

### Post by Barafu Albino Cheetah on 2009-08-09
Did you use sudo - where permissions denied?

---

### Post by crunkenstein on 2009-08-09
Oh, thank you! Here we go *scrounge*

walt@Blackbird:~$ sudo fdisk -l /dev/sda
[sudo] password for walt: 

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0a38f52b

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        1275    10240000   27  Unknown
/dev/sda2            1275       10367    73028608    7  HPFS/NTFS
/dev/sda4           10470       19457    72196110    5  Extended
/dev/sda5           10470       19085    69207988+  83  Linux
/dev/sda6           19086       19457     2988058+  82  Linux swap / Solaris
walt@Blackbird:~$

---

### Post by crunkenstein on 2009-08-09
Edit

About the Vista not working, it only took a simple repair. I was afraid to touch the recovery manager because I didn't want my whole drive getting written over with the defaults from the day I bought it. Moral of the story, live dangerously!

And now for something entirely different.
I still want to know how to get into the archive of my previous ubuntu installation. There's an ubuntu folder under C:\ but there's nothing of my old files in it. Still looking for help. Thank you in advance!

---

### Post by Post Monkeh on 2009-08-09
while i've never installed ubuntu in windows, i'd imagine if your ubuntu folder on your windows partition is empty, then you've lost the data.

if there ARE files in there, but nothing readable, then i should think you would have to boot into vista, then i'd imagine there should be an option to load ubuntu (ie the ubuntu you installed from within vista - i presume it is vista that handles the which of the systems - either ubuntu or vista - loads at startup, when you install ubuntu to the windows partition. when you install ubuntu to its own partition, grub handles all that.)

if you can no longer boot into your first ubuntu install, it's possible the vista repair has borked it. you'd have to boot into vista, reinstall ubuntu from WITHIN vista, and hope that it will detect and keep your existing files and settings from before.  if it does, you can boot into your windows install of ubuntu, and copy whatever files you need to a memory stick (presuming you can't copy them to a seperate location on your windows drive.)

---

### Post by crunkenstein on 2009-08-09
Okay, I'm reading this response and it sounds really good. Along the lines of something I was thinking with some additional points I didn't even know about. Here's a few criticisms. I was never able to access files on the Ubuntu desktop from the Ubuntu folder in C:\ while logged into Vista. It looks the same now as it did before the second install. I could try reinstalling 'Ubuntu Inside Windows' but will that delete information on my current partitioned install of Ubuntu as it would probably need to uninstall it? I'll give it a shot if I feel I can retrieve my current files.

---

### Post by Post Monkeh on 2009-08-09
> **crunkenstein said:**
> Okay, I'm reading this response and it sounds really good. Along the lines of something I was thinking with some additional points I didn't even know about. Here's a few criticisms. I was never able to access files on the Ubuntu desktop from the Ubuntu folder in C:\ while logged into Vista. It looks the same now as it did before the second install. I could try reinstalling 'Ubuntu Inside Windows' but will that delete information on my current partitioned install of Ubuntu as it would probably need to uninstall it? I'll give it a shot if I feel I can retrieve my current files.
It shouldn't affect your "full" installation. As for not being able to access your ubuntu folder from windows, i'd expect that, but you should, i think, be able to access your other disks from within ubuntu, or at the very least be able to copy whatever you need to a memory stick, or even email it to yourself. Reinstalling ubuntu from windows though may overwrite your first windows install, you may like to wait to see if anyone else knows how to recover your first installation

---

### Post by crunkenstein on 2009-08-09
I believe you're correct. After further reading I've come to believe that my 'desktop' was actually saved inside a Linux Virtual Hard Disk aka root.disk which can be read by a file such as vmware. The .disk file is no longer in my ubuntu file. I believe it to be gone for good. I still appreciate any feed back or advice that people have to offer.

---

