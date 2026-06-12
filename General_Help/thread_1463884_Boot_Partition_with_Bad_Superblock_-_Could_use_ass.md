---
title: "Boot Partition with Bad Superblock - Could use assistance!"
date: 2010-04-27
forum: General Help
---

### Post by GenXer on 2010-04-27
Well, I've managed to get myself into a bit of a pickle. 

I've got an unreadable /boot partition with bad superblock errors.

I was running somewhat low on space on the /boot partition, so I decided to give gparted a shot for resizing the partition.  I unmounted /boot and the swap partition, and asked gparted to shrink swap by about 100MB, and then grow /boot by that amount of space.  The reason I chose swap was that it was the next in order on the drive, and gparted seemed to require the space to be in order on the drive in order to add it to /boot.

Gparted successfully (according to its log) shrank the swap partition, but when attempting to grow /boot it encountered errors.  This left the /boot partition unreadable, with bad superblock errors.  I've tried several standard approaches to recovering a good superblock, but none have been able to find a good superblock or access the partition contents. :confused:

*I'll pause here for an important note!  The system is still running at the Gnome desktop.  I realize if I were to attempt to reboot, it would go down and not come back up, but having it still running may (I hope) give me access to repair options that might not be available otherwise?*

So at this point, I've got a good, readable root partition that's mounted.  I've got a bad, unreadable /boot partition with bad superblock errors, and a swap partition that I'm not completely sure of the condition of. I'd like to recover the system by fixing the /boot and swap partitions if at all possible.

Suggestions?  Things to try, or things to be sure to *not* try?  I'm happy to retry recovering the /boot superblock if that's an option, and I'm happy to try things again that I've already tried.  Thanks in advance for the help!!

---

### Post by GenXer on 2010-04-28
Bump? Not sure of the best way to get this in the right location so its noticed by the right people.

---

### Post by nic.de.muyer on 2010-04-28
Well, I wouldn't worry bout the swap for now, taken you have a wee bit of memory (like 1GB or more), your system will run fine without it.  
Let's focus on the /boot first.  

Now before anything else, you wouldn't happen to have a full backup of your system (or from a bit older system?).  If so, I'd suggest to just delete the boot partition, recreate it (with boot flag), newfs it and copy over the /boot files from the backup. 
Unless I overlook something now, that should suffice.

If not, I have a feeling booting with a untu live cd and copy over the livecd's-environment /boot to your /boot might also work.

:edit:
btw, as you mention "I've tried several standard approaches", I assume you already tried to just fsck the partition holding the boot partition, right?

---

### Post by klemes on 2010-04-28
Some simple questions.What version of Ubuntu you are using and what is the filetype system of /boot?
Better if you showed us the output of sudo fdisk -l
and sudo fsck /dev/sda1 (assuming /boot is in /dev/sda1)

Maybe if you concentrate on getting a bootable system instead trying to resurrect the /boot partition would have better results.Have you thought of making a /boot directory under /root (dev/sda3?) and editing the /etc/fstab accordingly ??Then if you reinstalled the linux-image-generic package and then doing a grub update maybe you'll get a working system again as a temporary fix.In this solution the only think I don't know if other files found normally in the /boot partition are required to boot and how to get them back.If you solve this with the input of others we may succeed in having a bootable system again......

---

### Post by dino99 on 2010-04-28
Pay attention:

- only tweak your partitions if you dont use them  ](*,)

The solution is to boot on an extern system like partedmagic from cd or usb

---

### Post by GenXer on 2010-04-28
Thanks for the suggestions, all.  I'll post back with more information this evening, and with what I get when I try to fsck the /boot partition.  I have indeed done that, and don't get useful results.

More later.

---

### Post by GenXer on 2010-04-28
When I run fsck on the boot partition, I get:

```
fsck /dev/sda1
fsck from util-linux-ng 2.16
e2fsck 1.41.9 (22-Aug-2009)
fsck.ext2: No such file or directory while trying to open /dev/sda1

The superblock could not be read or does not describe a correct ext2
filesystem.  If the device is valid and it really contains an ext2
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
    e2fsck -b 8193 <device>
```fsck -l results in:

```
Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00063b25

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1          18      144553+  83  Linux
/dev/sda2              19         255     1903702+  82  Linux swap / Solaris
/dev/sda3             256        7550    58597087+  83  Linux
/dev/sda4            7551       60801   427738657+   5  Extended
/dev/sda5            7551       60801   427738626   83  Linux
```From what you guys have said so far, it doesn't sound like there's an automated tool that's reliable to recover the bad superblock?  I understand your advice Klemes on making a boot directory and redirecting /etc/fstab as a temp fix.  Is there any sort of recovery tool that would let me reinstall Ubuntu without overwriting the existing system, that is to say, configured packages and settings and such?  I do have a backup of critical system data, however as you may've guessed by now I don't have a backup of the boot partition, as if I did I'd simply reformat /boot and then copy the data back onto it.

Dino99 - you say the solution is to boot on an external system, but I'm not sure what I'd do then?

---

### Post by klemes on 2010-04-30
Well have you tried the command suggested by running fsck:

sudo e2fsck -b 8193 /dev/sda1

also alternative superblock backup locations are 16384 and 32768.

Also you can use mke2fs command with the -n option to supply alternative superblock entries locations.

---

### Post by psusi on 2010-04-30
It sounds like you don't have an sda1 device.  ls /dev/sda* and see if it shows up.  If it doesn't, try sudo partprobe and see if that gets it to show up.

If it wasn't there and partprobe gets it to show up, then try to fsck it:

sudo e2fsck -f /dev/sda1

If it ends up being all trashed, then I'd say just reformat it and reinstall the kernel package, then reinstall grub.

---

### Post by GenXer on 2010-04-30
From a root terminal, e2fsck results in:

```
e2fsck -b 8193 /dev/sda1
e2fsck 1.41.9 (22-Aug-2009)
e2fsck: No such file or directory while trying to open /dev/sda1

The superblock could not be read or does not describe a correct ext2
filesystem.  If the device is valid and it really contains an ext2
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
    e2fsck -b 8193 <device>
```If I run mke2fs, I get:

 ```
mke2fs -n /dev/sda1
mke2fs 1.41.9 (22-Aug-2009)
Could not stat /dev/sda1 --- No such file or directory

The device apparently does not exist; did you specify it correctly?
```Partprobe doesn't do much better:

[HTML]partprobe
Error: Error informing the kernel about modifications to partition /dev/sda1 -- Device or resource busy.  This means Linux won't know about any changes you made to /dev/sda1 until you reboot -- so you shouldn't mount it or use it in any way before rebooting.
Warning: The kernel was unable to re-read the partition table on /dev/sda (Device or resource busy).  This means Linux won't know anything about the modifications you made until you reboot.  You should reboot your computer before doing anything with /dev/sda.[/HTML]Given that the GUI for GParted, which I used to start this whole process, lists sda1 as the boot partition, I'm confident that *was* the boot partition to begin with.  I realize partprobe wants me to reboot because of the change to the partition tables, however, I also know if I reboot that I won't be able to boot the system anymore.  I want to make sure there's nothing else I can do with the system booted that I wouldn't be able to do once I try to reboot and obviously can't b/c of the b0rked boot sector.

psusi - If I reformat the boot partition and then reinstall the kernel (I'll have to research how but I'm sure I can find out), will I then just be able to use that to boot to my existing installation of Ubuntu?

---

### Post by psusi on 2010-04-30
It looks like something is preventing /dev/sda1 from existing.  It is entirely possible that there is nothing wrong with your /boot partition, and it will be fine if you reboot.  If not, have a livecd handy to boot from to repair.  By the way, what version of Ubuntu are you running?

---

### Post by GenXer on 2010-04-30
I'm running 9.10, Karmic Koala.

That's an interesting point.  I'm going to complete a backup of the wiki that I host on this box, and once that's done (representing the critical data), reboot, and have the live CD handy to see what can be done.

I'll post back once I try the reboot.

---

