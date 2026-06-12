---
title: "partition mounting and fstab help needed please"
date: 2009-08-04
forum: General Help
---

### Post by ToFue on 2009-08-04
Hi-  I have three ext4 partitions that I want 'assigned' to three users as follows:

/dev/sda6  /home/karlos
/dev/sda7  /home/dominic
/dev/sda8  /home/jade

I can mount them fine with terminal, but I'm not too familiar with fstab and they don't mount when booting.. 
However, when mounted I don't want them showing up as an obvious mount in 'places' or nautilus, but to just *be* the directories...

I thought it may have been a permission issue so I did  >  sudo chown <user> /dev/sda*   


Here's what I have so far:

```

# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#

# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0

# / was on /dev/sda3 during installation
UUID=08e97966-a66c-4fca-9101-5ac994867e3b /               ext4    relatime,errors=remount-ro 0       1

# /home was on /dev/sda2 during installation
UUID=33897224-0e6e-45ad-a342-f59eb19e35c9 /home           ext4    relatime        0       2

# /home/karlos for user karlos on /dev/sda6
UUID=00bb64a1-cc06-45fa-9783-130d3c51de90	/home/karlos	ext4	realtime, auto, uid=1001, gid=1001	0	2	

# /home/dominic for user dominic on /dev/sda7
UUID=1ee933d2-19fa-4547-ab19-0a8f17134827	/home/dominic	ext4	realtime, auto, uid=1002, gid=1002	0	2

# /home/jade for user jade on /dev/sda8	
UUID=1855544c-e929-44db-82f3-ce8e0ae8b822	/home/jade	ext4	realtime, auto, uid=1003, gid=1003	0	2

# swap was on /dev/sda5 during installation
UUID=0bca2a4c-f0b6-49ab-b9b3-a767ec06e6ea none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

```

... and this:


```

tofue@familytoybox:~$ sudo ls /dev/disk/by-uuid -lah
total 0
drwxr-xr-x 2 root root 180 2009-08-03 22:57 .
drwxr-xr-x 6 root root 120 2009-08-03 22:57 ..
lrwxrwxrwx 1 root root  10 2009-08-03 22:57 00bb64a1-cc06-45fa-9783-130d3c51de90 -> ../../sda6
lrwxrwxrwx 1 root root  10 2009-08-03 22:57 08e97966-a66c-4fca-9101-5ac994867e3b -> ../../sda3
lrwxrwxrwx 1 root root  10 2009-08-03 22:57 0bca2a4c-f0b6-49ab-b9b3-a767ec06e6ea -> ../../sda5
lrwxrwxrwx 1 root root  10 2009-08-03 22:57 1855544c-e929-44db-82f3-ce8e0ae8b822 -> ../../sda8
lrwxrwxrwx 1 root root  10 2009-08-03 22:57 1ee933d2-19fa-4547-ab19-0a8f17134827 -> ../../sda7
lrwxrwxrwx 1 root root  10 2009-08-03 22:57 33897224-0e6e-45ad-a342-f59eb19e35c9 -> ../../sda2
lrwxrwxrwx 1 root root  10 2009-08-03 22:57 64D7-8F2F -> ../../sdb1


```

What am I doing wrong?  :confused:

Thanks in advance!

---

### Post by jocampo on 2009-08-04
Please take a look on this wiki: [https://help.ubuntu.com/community/AutomaticallyMountPartitions]("https://help.ubuntu.com/community/AutomaticallyMountPartitions")

---

