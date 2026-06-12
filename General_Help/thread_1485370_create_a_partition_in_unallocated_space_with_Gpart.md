---
title: "create a partition in unallocated space with Gparted in Ubuntu 10.04"
date: 2010-05-16
forum: General Help
---

### Post by aske on 2010-05-16
Hello,

I am trying to partition my unallocated part of the disc in my laptop in ubuntu 10.04 using Gparted.

Here is a screenshot of my disk and its partitions:
[[img]http://www.geting.se/image.php/242684-part1.png[/img]](http://www.geting.se/viewimage/image/242684-part1.png)

when i select the unallocated space i can ONLY create a PRIMARY partition..the LOGICAL and EXTENDED ones are grayed out.. i want to partition this unallocated space in two or three parts, and it seems i only have one (out of the four) primary partitions left.. so i cannot create the partitions i want!

please help me, why are these options grayed out and what can i do to fix that?

thank you,
anthony

---

### Post by uRock on 2010-05-16
I think you can only have one Extended partition. You may have to mount with the LiveCD and extend the extended partition to encompass all of the space for creating logical partitions.

---

### Post by techunit on 2010-05-16
That is correct. It looks as though you already have a extended partition but your already in ubuntu. You should reboot into a live cd and expand it enough for you to put all the paritions you want into it. Hope this helps

---

### Post by aske on 2010-05-16
does this mean reinstalling everything, or my files and system will be safe?

can you please give me more detailed instructions, forgive me i am a (kind of) novice user i don't want to mess things up i just configured my system with everything necessary..!

thank you

---

### Post by srs5694 on 2010-05-16
No, you don't need to reinstall everything. Boot an Ubuntu live CD or an emergency recovery system like [PartedMagic](http://partedmagic.com) or [System Rescue CD.](http://www.sysresccd.org/) You should then be able to launch GParted, click on /dev/sda3, and resize it to fill the disk. The unpartitioned space will then be within the extended partition, enabling you to create as many additional logical partitions as you like. On some systems, you may need to click on the swap space and select the option to disable it, though. (Some live/emergency CDs activate swap space, which will prevent you from modifying the extended partition. If swap space is active, it'll have the little key icon next to it in GParted, as it does in your screen shot. That icon means the partition is locked and cannot currently be changed.)

---

### Post by uRock on 2010-05-16
Your files should be fine, but with any partitioning operation there is always the chance of loss of data.

To extend the partition with the LiveCD, you just open gparted within the LiveCD and click on sda3 (extended partition) then right click and selecte resize, the drag the slider to make the extended encompass the unallocated space.

---

### Post by Werner7 on 2010-05-16
Yea, well you can only have 4 primary partitions, or 3 primary one extended. And you can have as many logical partitions in your extended drive. 

And no, you don't have to reinstall. Just run the live CD version. Open up the partitioner. And resize it. You may do backups, but this shouldn't loose any of your data. But things happen.

---

### Post by uRock on 2010-05-16
> **srs5694 said:**
> (Some live/emergency CDs activate swap space, which will prevent you from modifying the extended partition. If swap space is active, it'll have the little key icon next to it in GParted, as it does in your screen shot. That icon means the partition is locked and cannot currently be changed.)
If this happens, simply right click on your swap partition and click swapoff.

---

### Post by garvinrick4 on 2010-05-16
> **aske said:**
> does this mean reinstalling everything, or my files and system will be safe?

can you please give me more detailed instructions, forgive me i am a (kind of) novice user i don't want to mess things up i just configured my system with everything necessary..!

thank you
Why the ntfs partitions when no Windows installed? Cannot work on any partition that is mounted ( the keys). Always use install CD under try only mode when working on sizing (Live CD). If you have over 2 or so gig of Ram no need for swap. When you resize you do not lose your data. Do make a backup of all Data you want to keep when working on your drive. (always) Can always put grub back in place if getting rid of ntfs or windows formatted partitions that have boot flag. Let us know what you decide to do.

---

### Post by techunit on 2010-05-16
You should back-up your home folder to a cd or exteral harddrive harddrive first before you attempt any repartitioning...

---

