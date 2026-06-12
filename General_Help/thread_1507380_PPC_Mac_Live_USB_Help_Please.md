---
title: "PPC Mac Live USB Help Please"
date: 2010-06-11
forum: General Help
---

### Post by jasperyate on 2010-06-11
I'm trying to make a live USB of jaunty 9.04 on a PPC eMac as per [this thread]("http://ubuntuforums.org/showthread.php?t=780320").

I get to the point where I need to use the mac-fdisk "b" command to create the bootstrap partition as directed, and this is what i get (as expected):

```
Command (? for help): b
First block: 64
Command (? for help): p
/dev/sda3
         #                    type name                length   base    ( size )  system
/dev/sda31     Apple_partition_map Apple                   63 @ 1       ( 31.5k)  Partition map
/dev/sda32         Apple_Bootstrap bootstrap             1600 @ 64      (800.0k)  NewWorld bootblock
/dev/sda33              Apple_Free Extra              7628152 @ 1664    (  3.6G)  Free space

Block size=512, Number of Blocks=7629816
DeviceType=0x0, DeviceId=0x0

```but as soon I write the bootstrap to the disk, and then try to format the partition as directed, i get this:

```
 Command (? for help): w
Write partition map? [n/y]: y

Syncing disks.

Partition map written to disk. If any partitions on this disk 
were still in use by the system (see messages above), you will need 
to reboot in order to utilize the new partition map.

Command (? for help): q

root@ubuntu:~# hformat -l bootstrap /dev/sda32
hformat: /dev/sda32: error opening medium (No such file or directory)

```The drive is also unable to mount at all. I've tried restarting after the partition is written and trying again, no dice.

I'd appreciate any help, I'm more or less clueless and this has me completely stumped as to why the disk suddenly disappears after the boot partition is written to it. Cheers.

EDIT: I tried posting this on the PPC subforum but I guess that's private or something because it said i didn't have access to post, so i just came to general

---

