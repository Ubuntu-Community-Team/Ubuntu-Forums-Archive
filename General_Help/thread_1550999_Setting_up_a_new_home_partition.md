---
title: "Setting up a new /home partition"
date: 2010-08-11
forum: General Help
---

### Post by Quackers on 2010-08-11
I am laying the groundwork to set up a separate /home partition as this seems the best way to safeguard all my settings and files from disaster.
I have read a number of howto's on the subject but they haven't used the same method - it seems to me.

Firstly I'm quite happy about the partitioning element of the process. I need to shrink my current Ubuntu partition and create a new one for my /home folder, after making a note of the uuid (as I will need that later).
 How big does the root partition need to be to accommodate any future updates/kernels etc? 
Is ext4 advisable for the new /home partition?

The process after partitioning seems somewhat complicated, from what I've been reading. Basically the process involves copying my existing /home folder to the new location, telling the OS to mount that new /home partition instead of the old /home, then deleting or renaming the old /home.
However, in practise it doesn't look that simple. There seem to be many terminal commands involved that I don't understand.
Some clarification would be very much appreciated.
Thanks

---

### Post by darolu on 2010-08-11
> **Quackers said:**
> How big does the root partition need to be to accommodate any future updates/kernels etc? 
Is ext4 advisable for the new /home partition?

...telling the OS to mount that new /home partition instead of the old /home, then deleting or renaming the old /home.

About your first question, it depends on how many applications do you have installed, how many kernels do you have, number of desktop environments, etc... IMHO a regular user uses between 4 and 6 GiB for root elements, meaning /bin, /usr, /lib, /etc, etc...; so my recommendation would be 8 - 10 GiB, in the system I'm using I assigned 19GiB to /, I'm barely using 6,2GiB and I do have a lot installed (only gnome though), so it seems I'm wasting ~12GiB...

Yes ext4 is good, offers important advantages over ext2 and ext3; some people recommend ext2 and other non-journal file system as you don't really need journaling for "storage"; but I think the advantages (like speed and ability to handle large files) of ext4 very well compensate the space and processing power (not much imo) journaling takes from your FS.

You tell the OS where your /home partition is by editing your /etc/fstab file, there are tons of links out there that tell you how to edit it; this one is a good one: [http://www.tuxfiles.org/linuxhelp/fstab.html](http://www.tuxfiles.org/linuxhelp/fstab.html) It's not complicated, don't worry.

---

### Post by Quackers on 2010-08-11
Thanks for the info Darolu.
I was thinking somewhere between 10 and 20GB for the root partition. Space isn't really a problem.
I just have the current kernel installed.
Do installed applications live in the root partition? Oops, I thought they would go with /home. It's not a problem as I don't have that many anyway.

---

### Post by Quackers on 2010-08-11
Wow, my fstab doesn't look like the one in the link you posted - and it's wrong too!

```
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sdb1 during installation
UUID=83742eeb-0983-4c0d-89ae-f94eaa1da86e /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=2d97c423-df43-48f4-b7c2-29e468f99319 none            swap    sw              0       0
```

The swap partition is now sdb2 - sda6 was formatted long ago.

---

### Post by darolu on 2010-08-12
> **Quackers said:**
> Thanks for the info Darolu.
I was thinking somewhere between 10 and 20GB for the root partition. Space isn't really a problem.
I just have the current kernel installed.
Do installed applications live in the root partition? Oops, I thought they would go with /home. It's not a problem as I don't have that many anyway.

10 to 20 GiB for / is more than enough imo so you shouldn't have any problem that way; so you can have a better idea of the space you need open a terminal an run:
```
:~$ df -h
```
Most applications are installed at /bin and /usr/sbin, some at /opt; which in an average configuration are within / (they can be on separate partitions), but it doesn't mean that all apps are or have to be installed in the root partition, some can run from your /home partition or any other one.

It's OK if your file doesn't look like the one in that link, actually it would be an incredible coincidence if yours or anyone's would :p if you are absolutely positive your swap partition is elsewhere you should edit your fstab file accordingly, to find what the UUID values are (it's strongly recommended to use UUIDs) run this on a terminal:
```
:~$ sudo blkid
```
You may need to activate your swap partition too, i.e.:
```
:~$ sudo swapon /dev/hdb2
```

---

### Post by Quackers on 2010-08-12
I'm currently using 8% of 102GB for Ubuntu partition.
I've run swapon for /dev/sdb2 and got uuid's
Thanks again :-)

---

### Post by Quackers on 2010-08-12
Would editing the fstab be

sudo gedit /etc/fstab

and literally delete the old uuid for swap and enter the new uuid?

---

### Post by Quackers on 2010-08-12
Ok, I've edited fstab with the new uuid for /dev/sdb2 and done the swapon.
It booted up :-) that's got to be a good sign :-)

---

