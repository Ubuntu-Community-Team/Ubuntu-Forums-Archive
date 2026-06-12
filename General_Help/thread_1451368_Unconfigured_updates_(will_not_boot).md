---
title: "Unconfigured updates (will not boot)"
date: 2010-04-10
forum: General Help
---

### Post by Feelin_froggy8877 on 2010-04-10
I Installed Ubuntu 9.10 yesterday on a new machine. I started the update manager before I went to bed, (over 300mb's of updates) This morning the computer was unresponsive to get the monitor to come out of sleep. Was forced to power down. I imagine it was at a point of configuring one of the first updates. Now when I try to boot this is what I get......

udevadm trigger is not permitted while udev is unconfigured.
udevadm settle is not permitted while udev is unconfigured.
svgalib: cannot open /dev/mem.
gave up waiting for root device. common problems:
 -boot args (cat /proc/cmdline)
  -check rootdelay= (did the system wait long enough?)
  -check root= (did the system wait for the right device?)
 -missing moduals (cat /proc/moduals; ls /dev)
alert! /devdisk/by-uuid/ad41c29c-06fc-489b-9767-94ca0c637857 does not exist. dropping to a shell!


busybox v1.13.3 (ubuntu 1:1.13.3-1ubuntu7) built in shell (ash)
enter 'help' for a list of built in commands.

(initramfs)

Any help on how to go about configuring this would be great. thanx in advance.

---

### Post by ubunterooster on 2010-04-10
As it is a newly installed machine, it will likely be simpler to reinstall.

---

### Post by Feelin_froggy8877 on 2010-04-10
Thats what i was thinking, just had everything configured how I like it. Did a bit of searching and found a resolution. Just had to boot up the live cd, make a mount point for my ubuntu install. And chroot to that.


[HTML]mkdir /media/newroot/
mount /dev/hda2 /media/newroot/
chroot /media/newroot/
apt-get update
apt-get upgrade
[/HTML]

When I got to the apt-get update command, it told me I had to manually run 
apt-get dpkg --configure -l. There was actually To options in that command. I appoligize, I cannot remember the other.

Worked like a charm.

---

