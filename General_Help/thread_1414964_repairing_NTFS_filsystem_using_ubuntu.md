---
title: "repairing NTFS filsystem using ubuntu"
date: 2010-02-24
forum: General Help
---

### Post by EPurpl3 on 2010-02-24
Hello,

I have run in a series of trouble with my dual boot system (windows and linux) but this time is really bad, i have destroyed my NTFS filesystem from my windows partition.
 I will start with the beginning, i had some viruses on windows xp and i have used the windows xp cd to try to repair the windows, didnt worked but that has destroyed the grub, i have reinstalled the grub but it could not find the linux ( i think i have done something wrong). 
I have used linux live cd to replace windows components from a backup i had for windows (i have opened that backup and saved its files using another computer) and the windows started to work but i could not use linux so i had to reinstall it. 
After i have choose the right partitions and user and country and keyboard layout, at the end (i have pressed advanced button), i have choose to install bootloader on the windows partition (/dev/sda1). i thought that would be something like installing grub on windows instead of linux but that was wrong, now linux works like a charm but i cant access the windows partition, i cant even mount it, disk mounter doesnt even sees the partition, only GParted can see it. If i use GParted to check and repair the filesystem it says:

> GParted 0.3.5

Libparted 1.7.1

   **Check and repair filesystem (ntfs) on /dev/sda1**  00:00    ( ERROR )             calibrate /dev/sda1  00:00    ( SUCCES )             [I]path: /dev/sda1
start: 63
end: 92164904
size: 92164842 (43.95 GiB)[/I]          check filesystem on /dev/sda1 for errors and (if possible) fix them  00:00    ( ERROR )             ***ntfsresize -P -i -f -v /dev/sda1***             [I]ntfsresize v2.0.0 (libntfs 10:0:0)
Failed to startup volume: Invalid argument.
ERROR(22): Opening '/dev/sda1' as NTFS failed: Invalid argument
The device '/dev/sda1' doesn't have a valid NTFS.
Maybe you selected the wrong partition? Or the whole disk instead of a
partition (e.g. /dev/hda, not /dev/hda1)? This error might also occur
if the disk was incorrectly repartitioned (see the ntfsresize FAQ).
[/I]             
========================================

So, is it any way to repair the NTFS filesystem which was destroyed by the install of the bootloader on that partition? I have attached /var/log/messages, maybe could be usefull. Please help, i have some very important things on that partition. 

Thanks.

---

