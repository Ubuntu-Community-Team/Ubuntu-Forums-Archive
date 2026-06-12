---
title: "Use Grub as Main Bootloader"
date: 2010-04-25
forum: General Help
---

### Post by Bascotie on 2010-04-25
Hey everyone,

I have 2 hard drives, 1 with Windows 7, and one with Ubuntu.

Before installing Ubuntu I had PCLinuxOS then I got a book on learning Linux that is Ubuntu specific so I formatted it and installed Ubuntu 9.

My problem is:

When I boot up I get a WINDOWS bootloader first that lists:

Windows 7
Ubuntu

Then when I click Ubuntu I get the GRUB bootloader.

I've tried reinstalling Grub (maybe I did it wrong, I am a NEWBIE). I've also tried SuperGrub but none of the options worked, most returned error 15.

So I want ONLY GRUB to show up when booting. From there I think I can edit the grub file to set a timeout of 3-5 seconds, with Windows 7 as DEFAULT boot (Do I need to type "setactive" under my Windows 7 entry to do this part?)

Thank you much!

---

### Post by oldfred on 2010-04-26
Welcome to the forums.

When you say you get windows to show you a choice, do you have a wubi install. It has to boot from windows first.

Copy this first, so we can see your partitions & drives
```
sudo fdisk -l
```

---

### Post by mikewhatever on 2010-04-26
Try booting from the other hdd, presumably where grub is.

---

### Post by Bascotie on 2010-04-26
> **oldfred said:**
> Welcome to the forums.

When you say you get windows to show you a choice, do you have a wubi install. It has to boot from windows first. 

Copy this first, so we can see your partitions & drives
```
sudo fdisk -l
```

I did a Wubi install originally but I don't think it's the Wubi screen anymore, now that Ubuntu is installed.

Here's the fdisk:

> Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x9f64bdf3

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1          13      102400    7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/sda2              13       30402   244092928    7  HPFS/NTFS
Partition 2 does not end on cylinder boundary.

Disk /dev/sdb: 82.0 GB, 81964302336 bytes
255 heads, 63 sectors/track, 9964 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x1a98fd07

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        9965    80040960    7  HPFS/NTFS

Disk /dev/sdc: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x469d60df

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1      121601   976760001    7  HPFS/NTFS

Disk /dev/sdd: 640.1 GB, 640135028736 bytes
255 heads, 63 sectors/track, 77825 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00031cdb

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1               1       77826   625131832    7  HPFS/NTFS


The  last two are external drives. Also please read my reply to Mike as well, it might help you (read below), thanks :)

> **mikewhatever said:**
> Try booting from the other hdd, presumably where grub is.

I tried this but I get:

Boot0: testing
Boot0:error

and I have to restart and boot from the main hard drive with Windows 7 on it.

From the main Windows 7 drive I get this screen first:

"Windows boot manager"
"Windows 7"
"Ubuntu"

And I can choose Windows 7 to boot, or select Ubuntu which takes me to:

"GNU Grub Version 1.97~beta4"

There are 3 selections here:

Ubuntu bla bla..
Another Ubuntu bla bla bla..
Win7 on /dev/sda1

Oddly enough though the fdisk above shows Windows 7 on /dev/sda (not sda1, if that matters).

Hope it helps! Seems like both bootloaders are on the main hard drive.

---

### Post by oldfred on 2010-04-26
You have no linux partitions, so you are only booting with windows and then wubi.

You have the windows 7 new install where it uses a 100mb windows boot partition and then the rest of windows is in the second partition.

---

### Post by Bascotie on 2010-04-26
> **oldfred said:**
> You have no linux partitions, so you are only booting with windows and then wubi.

You have the windows 7 new install where it uses a 100mb windows boot partition and then the rest of windows is in the second partition.

Alrighty, does that mean I have to go through the 2 boot manager selections to get Ubuntu to boot everytime? It's not so bad I guess now that I have set the Windows boot loader timeout to 3 seconds (so I can turn the computer on and go away if I just wanna get into Windows). 

Thought, being a computer guy trying to learn Linux, I would have loved to be able to figure out how to set Grub as the bootloader and choose an operating system from there. That way, in the future, if I wanted to, I could simply change the grub file to set Linux as the main boot(without settings two separate timeouts if you catch what I'm saying).

Plus, it would satisfy my curiosity hehe. :KS

---

### Post by oldfred on 2010-04-26
You have lots of drives so I assume you have space. Ubuntu does not take much. 10-20GB for root, Swap the same as RAM and /home as large as you may want for data, if not planning on using it a lot since you have other NTFS places to store data /home could be another 20GB to start.

Dual Boot Win7 & Ubuntu
[http://ubuntuguide.org/wiki/Ubuntu:Karmic#Dual-Booting_Windows_and_Ubuntu](http://ubuntuguide.org/wiki/Ubuntu:Karmic#Dual-Booting_Windows_and_Ubuntu)
[http://lifehacker.com/5403100/dual+boot-windows-7-and-ubuntu-in-perfect-harmony](http://lifehacker.com/5403100/dual+boot-windows-7-and-ubuntu-in-perfect-harmony)
[http://news.softpedia.com/news/Installing-Ubuntu-9-10-126370.shtml](http://news.softpedia.com/news/Installing-Ubuntu-9-10-126370.shtml)
See info on windows resizing, but do not agree with grub2 complaints
[http://ubuntuguide.org/wiki/Multiple_OS_Installation#Changing_Windows_partition_sizes](http://ubuntuguide.org/wiki/Multiple_OS_Installation#Changing_Windows_partition_sizes)

---

### Post by Bascotie on 2010-04-26
> **oldfred said:**
> You have lots of drives so I assume you have space. Ubuntu does not take much. 10-20GB for root, Swap the same as RAM and /home as large as you may want for data, if not planning on using it a lot since you have other NTFS places to store data /home could be another 20GB to start.

Dual Boot Win7 & Ubuntu
[http://ubuntuguide.org/wiki/Ubuntu:Karmic#Dual-Booting_Windows_and_Ubuntu](http://ubuntuguide.org/wiki/Ubuntu:Karmic#Dual-Booting_Windows_and_Ubuntu)
[http://lifehacker.com/5403100/dual+boot-windows-7-and-ubuntu-in-perfect-harmony](http://lifehacker.com/5403100/dual+boot-windows-7-and-ubuntu-in-perfect-harmony)
[http://news.softpedia.com/news/Installing-Ubuntu-9-10-126370.shtml](http://news.softpedia.com/news/Installing-Ubuntu-9-10-126370.shtml)
See info on windows resizing, but do not agree with grub2 complaints
[http://ubuntuguide.org/wiki/Multiple_OS_Installation#Changing_Windows_partition_sizes](http://ubuntuguide.org/wiki/Multiple_OS_Installation#Changing_Windows_partition_sizes)

Odd, this whole time I thought Wubi already installed Ubuntu using that drive?

---

### Post by oldfred on 2010-04-26
You may have wubi in any NTFS partition. Where is root.disk?

---

### Post by Bascotie on 2010-04-26
> **oldfred said:**
> You may have wubi in any NTFS partition. Where is root.disk?


Thanks for the help guys. Turns out it was a Wubi install. I just installed OpenSUSE to give it a shot and it's working fine. I was able to use only the GRUB loader with Windows 7 as default boot after 4 seconds, thanks!

---

### Post by Bascotie on 2010-04-27
Back to Ubuntu! Did an official install, edited grub using the new editor (the one where you have to run the update-grub command afterwards).

Works great! Well not totally great, I'll make another forum about my new problem, but as far as this is concerned, SOLVED!

---

