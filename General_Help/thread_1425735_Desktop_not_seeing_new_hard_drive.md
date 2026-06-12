---
title: "Desktop not seeing new hard drive"
date: 2010-03-09
forum: General Help
---

### Post by archeryrob on 2010-03-09
I got Ubuntu  Desktop 9.10 32bit installed on a P4 machine. A little hard is hosting the software. I wanted to use this like a file server and after installation was up and working I added a [SIZE=1]Western Digital - Caviar Black 1TB Internal Serial ATA drive.

It does not even know it's there. I did a search and since i am in desktop I am using a GUI and do not know how to add a hard drive with text string, or where to do to do it. 

How can I add this hard drive? I am new to this as Windows seemed to notice the addition.
[/SIZE]

---

### Post by cpressland on 2010-03-09
It'll need Partitioning before it comes up. Just install GParted and partition it up with that in an EXT3 or EXT4 filesystem, then give the drive Read and Write permissions.

---

### Post by Roasted on 2010-03-09
Windows detected it?? I've never had Windows detect a new hard drive, mostly because when you buy a new hard drive, it doesn't have a valid partition table – requiring you to go into Disk Management to format it with NTFS ~ same deal with Ubuntu. Use Gparted to format it with a file system. I'd recommend EXT3 or EXT4.

---

### Post by cpressland on 2010-03-09
Yeah dude, when you put a new drive into a Windows Machine you get a window come up asking you to 'initialise' it. It's suprisingly easy.

---

### Post by Roasted on 2010-03-09
> **cpressland said:**
> Yeah dude, when you put a new drive into a Windows Machine you get a window come up asking you to 'initialise' it. It's suprisingly easy.

On the contrary, I hear GParted is relatively easy to open as well. ;)

Are we talking about Vista/7? XP doesn't do this, and has never done this for me in any machines I've added brand new drives to...

---

### Post by cpressland on 2010-03-09
Just loaded up a VM, added a new drive, it found it... weird.

Anyway. GParted is easy to use :)

---

### Post by Roasted on 2010-03-10
> **cpressland said:**
> Just loaded up a VM, added a new drive, it found it... weird.


of XP??

---

### Post by archeryrob on 2010-03-11
OK, how do you add a new drive with Gparted? I got it and I hit "refresh device list" and no new devices.

The original hard drive is just an old old one. 8 GB IDE on the CD rom bus. This just stores the Ubuntu for booting, all files will be stored and shared on the new 1TB SATA drive plugged into slot 0 on the mother board and I powered it down and plug into the other port. I am not seeing a drive to manage on this computer. This drive was working and was in a windows computer just before I posted this first message.

Any ideas, am I being stupid, cause I don't see it. I see the 8gb drive and it's partitions but nothing to add.

---

### Post by archeryrob on 2010-03-12
Any advice? Total reinstall, different hard drive, one on IDE bus and one on ATA bus?

---

### Post by matrix14 on 2010-03-12
Check your /boot/grub/device.map

Check whether or not other hdd device mapped within.

Check also with use command:

```

sudo lshw

```

---

### Post by archeryrob on 2010-03-12
No not mapped, all it says is:

(hd0)  /dev/sda

So, how do I map it? People before sounded like Gparted would find it and a few simple clicks and some formatting it was done. But not here, at least not yet.

---

### Post by archeryrob on 2010-03-13
OK, I run Puppy Linux and it only comes up with SDA1 (IDE 8Gb hard drive) and SR0 (CD drive)

So, can there be a conflict in the machine or Ubuntu with IDE and SATA drives on the same mother board. Motherboard will not recognize SATA drives because of IDE drives OR might just be a bad mother board?

Any thoughts? The only other choice is to rip out the IDE drive, try and re-install and see if Ubuntu will install on the SATA only.

---

### Post by archeryrob on 2010-03-13
OK, removed the IDE 8gb drive, left the SATA on Port 0 there is only 0 and 2 as 1 and 3 are not soldered on.

trying to determine if Ubuntu has issues with the hard drive [SIZE=1](Western Digital - Caviar Black 1TB Internal Serial ATA drive[/SIZE]) or if I have a bad MB. Any way to tell?

---

