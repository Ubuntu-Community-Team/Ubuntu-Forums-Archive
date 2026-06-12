---
title: "install alongside win7 and Vista both"
date: 2011-02-20
forum: General Help
---

### Post by hill0093 on 2011-02-20
I have an HP ENVY17 notebook PC with two drives in it.
I have the ubuntu 10.10 ISO DVD in the drive and have it booted.
dev/sdb has
  dev/sdb1 ntfs with windows vista on it for my very old programs.
  free space 209GB where I want to install ubuntu.
  dev/sdb2 ntfs that I want to use for shared space.
dev/sda has HP Windows home premium on it.
It took a little care to get it allocated this way.
So I suppose I just highlight the free space, 
but what should be in the bootloader selection?
I don't want to screw up the booting of all these things.

---

### Post by hill0093 on 2011-02-20
Looks like the two choices are /dev/sda and dev/sdb.

---

### Post by Quackers on 2011-02-20
If you want to keep Vista separate you can install grub to sdb, then make that drive the first bootable HDD in your bios. If that isn't an option you can install grub to sda.

---

### Post by hill0093 on 2011-02-20
I chose "Install alongside other operating systems".
I clicked "advanced partitioning tool".
I selected the "free space" of 200GB on /dev/sdb.
I left the bootloader alone at /dev/sda.
I pressed "install now", 
and it says "No root file system is defined".
Do I partition the free space into swap space (how much?),
and the rest into the ubuntu partition? or what?

---

### Post by Quackers on 2011-02-20
If you are installing 10.10, the "install alongside" option is a bad one! There is a very good chance that it will wipe out your existing system!
Back out of the installer program up to the point where you chose that option. Then, instead choose "specify manually" and double click on the free space in the next window to install into.
For partitioning you must selesct the size, type (ext4) and mount point ( which for a basic installation is / (from the drop down menu - it signifies "root").
If you don't select a mount point you get the "root system not defined" error.

---

### Post by hill0093 on 2011-02-20
Thanks, Feels like we might get there.
After the double click, the 
new partition size is the whole 200GB,
and it's called logical and location is beginning.
Doesn't seem quite totally correct to me, but
I don't know meaning of these words.

---

### Post by Quackers on 2011-02-20
Logical is ok. You can choose what size you want it to be. If you want to use hibernation (as opposed to suspend) you should make a swap partition too, which would need to be slightly larger than the amount of ram you have. If you have 2GB of ram or more and don't intend to use hibernation you will be ok without swap, or alternatively a small one.

---

### Post by hill0093 on 2011-02-20
After making the ext4 partition, I have 10715 MB left.
What do I do about mount point, and is it also logical?

---

### Post by Quackers on 2011-02-20
For swap? No mount point is required for swap. 10GB is a lot of swap!

---

### Post by hill0093 on 2011-02-20
I mean 10.715 GB for swap.

---

### Post by hill0093 on 2011-02-20
Thanks, sorry we crossed.
I'm going to try install now.

---

### Post by Quackers on 2011-02-20
Yes, that's a big swap space :-) That's bigger than some people's root partition :-)

---

### Post by hill0093 on 2011-02-20
I can boot each of the three.
The boot menu is the Ubuntu boot menu with
the first 2 being ubuntu, the next 2 being memory test,
the 5th being Windows 7 on /dev/sda1,
the 6th being Vista on /dev/sda2, 
the 7th being Vista on /dev/sda3.
the 6th doesn't work, and after select Win 7,
I get a choice of Win7 or Vista.
I s'pose it would be nice to get rid of the 6th, but
I s'pose getting rid of the 7th would be disaster.
Any suggestions? 
Is there a way I give you points for helping?

I have 8GB of memory, and was just following your 
suggestion even if you didn't know the size.
How would you suggest I make it smaller?
Do I need any unallocated space on either of the disks?

---

### Post by oldfred on 2011-02-20
A little late, but in case you end up installing again.

For the Total space you want for Ubuntu:
Ubuntu's standard install is just / (root) & swap, but it is better to add another partition for /home:
1. 10-20 GB Mountpoint / primary or logical beginning ext4(or ext3)
2. all but 2 GB Mountpoint /home logical beginning ext3(or ext4)
3. 2 GB Mountpoint swap logical

Depending on how much memory you have you may not absolutely need swap but having some is still recommended. I do not hibernate (boots fast enough for me) but if hibernating then you need swap equal to RAM. And if dual booting with windows a shared NTFS partition is also recommended. But you usually cannot create that as part of the install, just leave some space. Or partition in advance (recommended).
One advantage of partitioning in advance is that the installer will use the swap space to speed up the install. Thanks Herman for the tip.

Basics of partitions:
[https://help.ubuntu.com/community/DualBoot/Partitions](https://help.ubuntu.com/community/DualBoot/Partitions)
[https://help.ubuntu.com/community/HowtoPartition](https://help.ubuntu.com/community/HowtoPartition)

Because windows combines all its boot loaders into one active partition, grub can only directly boot that one. Sometimes you can repair the other install after moving boot flag and make both bootable from grub.

Discusses installs but same for repairs.
To get each MS to have its own boot loader make a second primary partition and set its boot flag on, then install the 2nd product in it. Multibooters, Pictures here worth 1000+ words
[http://www.multibooters.co.uk/multiboot.html](http://www.multibooters.co.uk/multiboot.html)
A user who installed two windows & it worked to boot from grub directly
[http://ubuntuforums.org/showthread.php?t=1271600](http://ubuntuforums.org/showthread.php?t=1271600)

Do not worry about small unused spaces. They always had some space between partitions, but now with SDD & Advanced format drives they have increased the rounding slightly and now you see the spaces. If large then you can reuse or expand an adjacent partition.

---

### Post by Quackers on 2011-02-20
No unallocated space is required (unless you want to make a new partition).
With regard to swap you should have decided the size when you wre setting it up. You can change it, but it is not as easy now it is there. I would recommend leaving it for the moment, until you get more accustomed to using Ubuntu.

No way to give points for helping, but a small fish would be nice :-)
You're welcome!

---

### Post by hill0093 on 2011-02-20
Thanks for the extended information, a study in itself,
which I might do.

What software do I use to remove the nonworking 
Vista boot reference? and is it a good idea?

I don't knoe what a fish is.

---

### Post by Quackers on 2011-02-20
:-) it's a thing that swims in the sea and I eat them :-)

It won't do any harm to leave the non-working item in the grub menu. You can remove it if you want to, have a look at this guide. The item in the first line (grub customizer) may help, but I haven't used it to be honest. The older methods are described further down.

[http://ubuntuforums.org/showthread.php?t=1287602](http://ubuntuforums.org/showthread.php?t=1287602)

---

