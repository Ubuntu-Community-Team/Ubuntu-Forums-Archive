---
title: "Booting to initramfs, can't mount ubuntu install partition"
date: 2010-07-16
forum: General Help
---

### Post by Jacksie on 2010-07-16
Hi there,

Running Ubuntu 10.04 with all suggested updates, had booted successfully several times in it's current state.

So I was just doing normal stuff (youtube etc), then ubuntu crashed (youtube  kept looping over the 0.5 seconds of audio that just played) and I had to hard-reset and now on boot I'm getting a whole bunch of mount errors (along the lines of not being able to mount -UID number- to root and other important spots) then an initramfs prompt. 

On my live-cd now, haven't tried booting from HDD again yet. 

Can't mount the partition that Ubuntu is installed on, gives me

```
Error mounting: mount: wrong fs type, bad option, bad superblock on  /dev/sda1,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so
```Usually (when it was running from the hdd) that partition is on sdb and my secondary hdd is sda. Will try booting without secondary.

This HDD is getting pretty old, so it wouldn't surprise me if it was at fault.

What could cause these errors? Any way to recover my data?

I was just getting it how I like too :(

EDIT: The mount errors I get:
```
mount: mounting /dev/disk/by-uid-{UID} on /root
failed: Invalid argument
mount: mounting /dev on /root/dev failed: No such file or directory
mount: mounting /sys on /root/sys failed: No such file or directory
mount: mounting /proc on /root/proc failed: No such file or directory
Target filesystem doesn't have /sbin/init.
No init found. Try passing init= bootarg.
```({UID} is a big UID number)

Obviously the last three mount errors are because the first one failed?

After them I get "BusyBox" built in shell message and the "(initramfs)" prompt thing.

Also, this does not seem to be the same as [http://ubuntuforums.org/showthread.php?t=1532775](http://ubuntuforums.org/showthread.php?t=1532775) or the links mentioned in the first reply.

EDIT: Thank you for the valuable contributions by all who posted :P. 

SOLUTION: run GParted from the live-cd, right click the partition and hit check, apply.

---

