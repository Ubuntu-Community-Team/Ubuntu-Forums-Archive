---
title: "Multiboot &amp; partitions - I've gone and made a mess"
date: 2011-12-22
forum: General Help
---

### Post by sunfromhere on 2011-12-22
The story: The first thing I installed was Ubuntu. Naturally, I thought about partitioning 1 second and let the installer take care of it. Now, 2 months later, I want to multiboot.

1. Fedora: You know how Fedora installer gives you 5 options for partitions? Well, the only one that didn't say "not enough space on disk" was the shrink option. So I did that. Fedora installation successful, turning most of the disk into LVM.

2. CentOS: this OS gives the same 5 partitioning options as Fedora when installing, however the "shrink" option in this case also gave "not enough space on disk" error. 

Now, I did read lots of threads on this topic here, but I read them now, not before any installations. I tend to make a mess first and then fix my mess later :)

This is the current state (fdisk -l):

```
/dev/sda1   *        2048    14526463     7262208   83  Linux
/dev/sda2       968921086   976771071     3924993    5  Extended
Partition 2 does not start on physical sector boundary.
/dev/sda3        14526464    15550463      512000   83  Linux
/dev/sda4        15550464   968919039   476684288   8e  Linux LVM
/dev/sda5       968921088   976771071     3924992   82  Linux swap / Solaris
```

Basically, I made a mess.
The size of the hard disk is 500 GB.

Is there any way to fix this (repartition) and keep current installations or would it be easier just to start from scratch (plan partitioning ahead for each OS I want to install & install Fedora first)? 

Why did CentOS installation claim "not enough space on hard disk"? Why couldn't I repartition the 400GB (LVM) when in CentOS installer?

Thanks for your help.

---

### Post by zvacet on 2011-12-22
You can delete all partitions on extended ( I suppose Ubuntu is on sda1).Fedora gives you option for standard install and that is what you should do(if you don´t have special reason to install on LVM).

---

### Post by oldfred on 2011-12-22
I do not know for sure, but the standard partition tools (based on gparted) in the Ubuntu installer do not work on LVMs. In Ubuntu you have to use the alternative install to have the LVM tools to manage LVM partitions. I would expect if CentOS uses LVM it might have the LVM tools to resize partitions but since it is installing perhaps it does not expect to resize LVM to install.

You can resize the LVM before installing or totally reinstall.

lvm info:
[http://ubuntuforums.org/showthread.php?t=141900](http://ubuntuforums.org/showthread.php?t=141900)
Advantages/Disadvantages
[http://ubuntuforums.org/showthread.php?t=1586328](http://ubuntuforums.org/showthread.php?t=1586328)

---

### Post by zvacet on 2011-12-22
> I do not know for sure, but the standard partition tools (based on gparted) in the Ubuntu installer do not work on LVMs.

No,they don´t,but in Fedora you have options: standard,LVM and RAID.If someone want to add Fedora choosing standard way is way you should go.I don´t know what to do if you have one OS installed and you want second to install on LVM if that is what OP want.

---

### Post by sunfromhere on 2011-12-22
> **zvacet said:**
> No,they don´t,but in Fedora you have options: standard,LVM and RAID.If someone want to add Fedora choosing standard way is way you should go.I don´t know what to do if you have one OS installed and you want second to install on LVM if that is what OP want.

When I was installing Fedora, I worked under the assumption "if not sure-leave default", and the default was ticked LVM.

Looking at the whole thing from GParted, 450GB is marked as LVM and not supported by GParted. I could try and run GParted from live CD and try to repartition.

However, I'm still wondering why CentOS won't install (or shrink for that matter) on a LVM drive - it has LVM support and, as Fedora, offers you to partition your drive as LVM.

What would happen if I went to install CentOS, chose the option to "replace current Linux installation" and unticked the LVM? Which "current Linux installation" would it replace? Fedora or Ubuntu?

---

### Post by oldfred on 2011-12-22
That is why I always partition in advance, so I know for sure what is where. 

And even that did not work even as I created several partitions, and forgot which was the data and which was the system and installed to the data partition.:)
 Fortunately for me I had not used the data partition and just resized it and make the system partition larger for data. So I always label partitions when I create them and print the list from sudo blkid -c /dev/null that shows labels.

---

### Post by zvacet on 2011-12-23
@ [B][sunfromhere]("http://ubuntuforums.org/member.php?u=1411730")
[/B]
Because you are posting here I suppose you want Ubuntu to be first OS.If that is a case you may want to have separate home partition on witch your data/settings be stored.Read [http://www.ubuntugeek.com/how-to-create-a-separate-home-partition-in-ubuntu.html](http://www.ubuntugeek.com/how-to-create-a-separate-home-partition-in-ubuntu.html) .How big home will be depends on you.Since you want to multiboot you have to decide do you want just to try other distros or you want to use them for longer period of time.If you just want some space for try other distros you can leave 20GB and partition it as two partitions of 10Gb.It is enough for try any distro.Other then that you can leave ~2GB for swap and rest give to separate home.But this is just a thought.

---

### Post by sunfromhere on 2011-12-24
I removed Fedora and am currently creating a partitioning table, which should look like this (all are ext4):
20gb Ubuntu "/" - primary partition, dev/sda1
100gb "/home" - logical, all the rest logical too
4gb swap

and then
3x20gb for other 3 distros
1xremaining GB for whatever usage I need in future

The problem is: for 3x20GB 1xremainingGB I haven't specified a mount point, so GParted automatically labeled them as "/boot". Why and will this have any effect on my later usage for these 4 partitions (f.e. if I try to put Fedora "/" on one of these 20GB partitions, will I be able to?)?

---

### Post by oldfred on 2011-12-24
If it is just a label and not a mount then it is ok & I would just relabel using Disk Utility. But if it is a mount then you boot files are in the /boot partition. You can check fstab to see what is mounted and list UUIDs which also show labels.

Without the gksudo you cannot edit it:
gedit /etc/fstab
You need sudo for this to work:
sudo blkid

---

### Post by sunfromhere on 2011-12-24
I decided to leave them (3x20gb) as unused partitions, and then just designated them as "/" while installing each distro. It worked, so now I have triple-boot (Ubuntu, Fedora, CentOS). 

Now I just need to fix that CentOS-GRUB thing...

---

### Post by fantab on 2011-12-24
> **sunfromhere said:**
> I decided to leave them (3x20gb) as unused partitions, and then just designated them as "/" while installing each distro. It worked, so now I have triple-boot (Ubuntu, Fedora, CentOS). 

Now I just need to fix that CentOS-GRUB thing...

When you are multi-booting or dual-booting remember that ONLY one version of GRUB is all that is required. I am sure you know this, I had to repeat anyway.

The GRUB from Ubuntu is EASIER TO MANAGE than in Fedora or CentOS. If you have installed Ubuntu FIRST then **don't install GRUB from either of the other two distros**. After installing the other distro you have to log into Ubuntu and ***sudo update-grub***. Grub will find all the distros that are installed on the system.

---

### Post by sunfromhere on 2011-12-24
It is done!

Four OSes- Ubuntu, Fedora, CentOS, Debian, each on it's own partition, Ubuntu having a separate partition for /home, grub correctly showing all options (naturally I made a few mistakes here, but managed to correct them).

Thank you all for help! Now I have 4 Linuxes to mess up. :D

---

