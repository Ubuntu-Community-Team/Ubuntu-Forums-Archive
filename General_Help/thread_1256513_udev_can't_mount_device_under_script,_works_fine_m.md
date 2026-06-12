---
title: "udev can't mount device under script, works fine manually"
date: 2009-09-02
forum: General Help
---

### Post by austin987 on 2009-09-02
Udev itself is working fine...Long story short, need to write a script to automatically backup server to one of two different encrytped external hard drives. But, since you must walk before you crawl, starting out with a basic script:
#!/bin/bash
set -x

rootdrive="$1"
drive="${rootdrive}1"
mount="mount -t ext3 /dev/$drive /media/backup"
if [ -d "/media/backup" ]
then
	touch /tmp/test1
	$mount
else
	touch /tmp/test3
	mkdir -p /media/backup
	$mount
fi

The script is called from udev whenever the drive is mounted (detected by serial number). This works fine. When the script gets to $mount, however, it bombs out:
austin@austin-desktop:~$ cat /tmp/log.txt 
+ rootdrive=sdc
+ drive=sdc1
+ mount=mount -t ext3 /dev/sdc1 /media/backup
+ [ -d /media/backup ]
+ touch /tmp/test1
+ mount -t ext3 /dev/sdc1 /media/backup
mount: special device /dev/sdc1 does not exist

running 'mount -t ext3 /dev/sdc1 /media/backup' manually works fine, of course.

Anyone got an idea what's going on?

---

### Post by dcstar on 2009-09-03
> **austin987 said:**
> 
........
The script is called from udev whenever the drive is mounted (detected by serial number). This works fine. When the script gets to $mount, however, it bombs out:
austin@austin-desktop:~$ cat /tmp/log.txt 
+ rootdrive=sdc
+ drive=sdc1
+ mount=mount -t ext3 /dev/sdc1 /media/backup
+ [ -d /media/backup ]
+ touch /tmp/test1
+ mount -t ext3 /dev/sdc1 /media/backup
mount: special device /dev/sdc1 does not exist

running 'mount -t ext3 /dev/sdc1 /media/backup' manually works fine, of course.

Anyone got an idea what's going on?

[LIST=1]
[*]Are you sure the device is actually mounted and stable before the script runs?
[*]Run it manually with sudo and see what happens.
[/LIST]

---

### Post by austin987 on 2009-09-03
> **dcstar said:**
> [LIST=1]
[*]Are you sure the device is actually mounted and stable before the script runs?
[*]Run it manually with sudo and see what happens.
[/LIST]

The script is called by udev with the RUN parameter:
KERNEL=="sd[a-z]", ID_SERIAL="123456xyz", RUN="/usr/local/bin/backup"

Running the mount command as root works fine, it's only when run by udev (as root, of course), that it fails.

---

### Post by austin987 on 2009-09-03
Bump

---

### Post by austin987 on 2009-09-03
Found the problem. My reading of udev hadn't given me this info, so I made some bad assumptions. The script was run when the drive itself was recognized by udev. The script then added '1' to the device name (/dev/sd[a-z]). The problem is, udev adds the drive, runs any udev commands (the backup script, in this case), *THEN* adds the partitions as their own device. As a result, when the script ran, /dev/sdc existed, but not /dev/sdc1. Of course, when I ran it manually afterward, /dev/sdc1 existed then.

I've adjusted the udev rule accordingly:
DEVTYPE=="partition", ID_MODEL_ID=="3000", ID_SERIAL_SHORT=="123456xyz", ACTION=="add", OPTIONS+="last_rule", RUN="/usr/local/bin/backup %k"

which mounts /dev/sd*1 to /media/backup without a hitch.

---

