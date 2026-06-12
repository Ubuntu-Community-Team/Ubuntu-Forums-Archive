---
title: "External Hard Drive won't mount, something to do with superblocks?"
date: 2009-08-29
forum: General Help
---

### Post by nigh3252 on 2009-08-29
Hi!  I'm new to Ubuntu and I'm having a problem with my external hard drive.  I'm using ubuntu 8.10, and I haven't had any problems with the hard drive until yesterday, when I tried to make my XP partition see it (I'm dual booting ubuntu/xp).  I think I messed up some kind of superblock?  I've been looking around to try to find an answer, but nothing has worked.  Can anyone help me out?  Is there any more info I should provide?

Thanks

**I FOUND THE FIX:**  I used a program called TestDisk and it solved the problem.

---

### Post by scouser73 on 2009-08-29
Please follow the instructions set out in this tutorial for mounting drives: [[COLOR="Red"]**Mount Hard Drives**[/COLOR]]("https://help.ubuntu.com/community/Mount/").

---

### Post by nigh3252 on 2009-08-29
I tried to follow the mount instructions, and it just said this:  (I know from my previous tries that the drive is sdc1, and I already made /media/sdc1 to put it in, and I did dmesg when it told me to)


ryan@ryan-laptop:~$ sudo mount /dev/sdc1 /media/sdc1 -t vfat
mount: wrong fs type, bad option, bad superblock on /dev/sdc1,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

ryan@ryan-laptop:~$ dmesg | tail
[   39.976533] NET: Registered protocol family 10
[   39.977364] lo: Disabled Privacy Extensions
[   50.116078] eth0: no IPv6 routers present
[   50.956044] eth1: no IPv6 routers present
[   80.712796] ieee80211_crypt: registered algorithm 'TKIP'
[ 1115.119328] FAT: utf8 is not a recommended IO charset for FAT filesystems, filesystem will be case sensitive!
[ 1115.120623] FAT: bogus number of reserved sectors
[ 1115.120633] VFS: Can't find a valid FAT filesystem on dev sdc1.
[14744.497523] FAT: bogus number of reserved sectors
[14744.497538] VFS: Can't find a valid FAT filesystem on dev sdc1.


So what does that mean?

---

