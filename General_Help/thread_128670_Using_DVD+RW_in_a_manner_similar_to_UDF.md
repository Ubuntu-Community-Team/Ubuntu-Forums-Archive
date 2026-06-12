---
title: "Using DVD+RW in a manner similar to UDF?"
date: 2006-02-12
forum: General Help
---

### Post by Zeroangel on 2006-02-12
I am planning on backing up files on a partition and wish to also be able to copy files from other partitions on the fly whenever I feel like it, without having to format the DVD+RW every time I want to update or erase content on it.

Is there a utility, similar to a UDF utility that will let me do this, yet still preserve permissions? And failing that, does anyone have a linux UDF utility to recommend?

---

### Post by dcstar on 2006-02-12
[QUOTE=Zeroangel]I am planning on backing up files on a partition and wish to also be able to copy files from other partitions on the fly whenever I feel like it, without having to format the DVD+RW every time I want to update or erase content on it.

Is there a utility, similar to a UDF utility that will let me do this, yet still preserve permissions? And failing that, does anyone have a linux UDF utility to recommend?[/QUOTE]
I have UDF set up and mounting a CD-RW on boot up (DVD-RW not quite sorted out yet....), these links may be of assistance:

[http://ubuntuforums.org/showthread.php?t=23043&highlight=udftools](http://ubuntuforums.org/showthread.php?t=23043&highlight=udftools)
[http://www.raoul.shacknet.nu/2005/11/10/packet-writing-on-cdrw-and-dvdrw-media/](http://www.raoul.shacknet.nu/2005/11/10/packet-writing-on-cdrw-and-dvdrw-media/)

The second link's instructions needs to be slightly adapted for the Ubuntu environment.

One day I might get around to writing a HOWTO for UDF, but it may have to wait until Dapper comes out......

BTW, here is the /etc/init.d/mountudf file I use (which is run in rc2.d as one of the last things):

```
#! /bin/sh
#
# mountudf	Mount UDF CD/DWD RW (if already in the drive) on machine startup.
#
# Version:      1.0 07-12-2005 David Clayton
#

PATH=/sbin:/bin:/usr/sbin:/usr/bin

. /lib/lsb/init-functions

log_begin_msg "Mounting UDF RW ..."
mount /media/cdvdrw
log_end_msg $?

: exit 0
```

---

### Post by Zeroangel on 2006-02-12
Thank you very very much Dcstar!

I followed those guides and now my UDF is working almost flawlessly. However, I do have another concern. My DVD+RW can only hold ~520MB of data instead of the full 4.7GB. I think I might have failed to properly write the UDF filesystem to disc (the console just sat there doing nothing for ~25 minutes while it was claiming to write the UDF filesystem). 

The output of the second attempt was:
```
dave@dlinux:~$ sudo mkudffs --media-type=dvd --udfrev=0x0150 
 /dev/pktcdvd/pktcdvd0
start=0, blocks=16, type=RESERVED
start=16, blocks=3, type=VRS
start=19, blocks=237, type=USPACE
start=256, blocks=1, type=ANCHOR
start=257, blocks=16, type=PVDS
start=273, blocks=1, type=LVID
start=274, blocks=264141, type=PSPACE
start=264415, blocks=1, type=ANCHOR
start=264416, blocks=239, type=USPACE
start=264655, blocks=16, type=RVDS
start=264671, blocks=1, type=ANCHOR
dave@dlinux:~$

```
The same as the first time where the attempt to write the UDF filesystem stopped at exactly that point (and I wasn't returned to the input prompt) Is it possible for such a thing to happen where part of the disc becomes unreadable when writing the filesystem fails?

---

### Post by dcstar on 2006-02-19
[QUOTE=Zeroangel]Thank you very very much Dcstar!

I followed those guides and now my UDF is working almost flawlessly. However, I do have another concern. My DVD+RW can only hold ~520MB of data instead of the full 4.7GB. I think I might have failed to properly write the UDF filesystem to disc (the console just sat there doing nothing for ~25 minutes while it was claiming to write the UDF filesystem). 
.....
[/QUOTE]
You might try erasing the DVD using k3b (or another writing utility), and trying to UDF format it again.

I use the same command that you did, but I still haven't got DVD's working 100% myself.

---

