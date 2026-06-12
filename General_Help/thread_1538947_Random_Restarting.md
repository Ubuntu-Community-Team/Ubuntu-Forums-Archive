---
title: "Random Restarting"
date: 2010-07-25
forum: General Help
---

### Post by amanisdude on 2010-07-25
Hi all,

I am new to both Ubuntu and Linux.  I installed Ubuntu 9.10 on my computer about two months ago, and I've recently upgraded to 10.04.  However, ever since the first install, I've had this issue with my computer "randomly" restarting.  

I'm not really 100% sure on what causes it, but I notice that it tends to occur when I have a lot of applications running (although my computer will sometimes restart when I'm asleep and NO user apps are running at all.)

I also noticed some time ago that, despite my swappiness being set to 60, Ubuntu hardly sends any data to the swap file.  (I use a swap file on the same partition as my Ubuntu install instead of a dedicated swap partition.)  It is possible that Ubuntu has some problem swapping.

Here is my fstab:

```
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda1 during installation
UUID=0cc73aa0-e434-4c00-9ff8-61e366b1c5b8 /               ext4    errors=remoun$
/mnt/1024Mb.swap        none    swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/mapper/cryptswap1 none swap sw 0 0
```

As you can see, my swap file is 1GB and is located at /mnt/1024Mb.swap.  In making this file, I followed the instructions on [Ubuntu's Swap FAQ]("https://help.ubuntu.com/community/SwapFaq").

Any insight into this problem would be greatly appreciated.  And, again, I'm new to Linux, so so please forgive my ignorance.

-AmanIsDude

---

### Post by amanisdude on 2010-07-27
Any clue, anyone?

I've even tried upping my swappiness value with [FONT="Courier New"]sudo sysctl vm.swappiness=100[/FONT], and my compy still doesn't swap.

I've also tried removing and reformatting my 1024Mb.swap file as per the instructions on the [Community Swap FAQ]("https://help.ubuntu.com/community/SwapFaq") to no avail.  I do use my computer for very memory-intensive tasks, so any help or insight would be appreciated.  Thanks!

~AmanIsDude

---

### Post by P4man on 2010-07-27
That it doesnt swap (unless needed) is a feature, not a bug. If you have enough ram there is no point in swapping. Windows does this no matter how much ram you have, causing so much unneeded disk activity.  ubuntu does not. 

This is not your problem.

Spontaneous rebooting is nasty though. And usually caused by a hardware error. I would first check your system temperatures to make sure its not overheating; then check your RAM. Grub boot menu gives you access to memtest86, let it run for several hours at least and see if it reports errors. Last thing to check is your powersupply. In the bios see if your voltages are good and stable; although thats still no guarantee for a good PSU.

---

### Post by schuelaw on 2010-10-20
I'm seeing this behavior on all of my new dell 64-bit 10.04 installs (15 computer mathlab) and on one dell 64-bit classroom computer.  I'd love to hear some ideas.  The classroom computer is a dell, but different model.  I doubt a hardware problem.

---

### Post by amanisdude on 2010-10-20
With regard to my problem, it did turn out to be mostly a hardware problem.  Specifically, I found my computer restarting when the CPU temp reached about 52°C.  I changed the thermal compound, and my PC's performance improved quit a bit.

The problem isn't totally solved, however.  Sometimes if I come back after having left for a long duration, I find myself staring at a fresh login screen.

You may want to check if overheating is not an issue.  Using lm-sensors and the GNOME Sensors Applet works pretty well, in my opinion (if you're using GNOME).  It is a well-known fact that Xorg hogs more processing power than a hungry alpha-male gorilla.  

Also, if there are any similarities between the circumstances of each restart (CPU usage, swap file/partition usage, running applications), it may be wise to post them here.  (Using the GNOME System Monitor applet is good for the former two.)

---

### Post by Jebtrix on 2010-10-20
Did you try disabling all power saving settings/screen saver? Maybe try running without acpi enabled?

---

### Post by HermanAB on 2010-10-20
Howdy,

There are multiple people complaining about random reboots with 10.10.  If you have time to debug it, please do and file your bug reports carefully.

If not, then you should probably look into switching to another distribution until other users and developers figure it out and Ubuntu stabilizes.

---

