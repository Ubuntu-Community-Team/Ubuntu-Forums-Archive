---
title: "Error Mounting External HD (need help desperately))"
date: 2011-11-19
forum: General Help
---

### Post by stamoulohta on 2011-11-19
Hey guys,

I have a WD myPassport external drive and I wanted to transfer some big (and very expensive) video files with it. I formatted it with Disk Utility and I selected the "Don't partition" option. Then I formatted the volume creating a FAT fs. Copied the needed files in it and permanently erased them from where I got them (very very stupit!) Then I booted in Windows (also very stupid) because I needed to create some other (Windows) file to the disk. Windows didn't recognize my disk so I went and Assigned a drive letter to it (without formatting it).

Now Windows asks me to format the disk whenever I try to access it and Ubuntu states in terminal: ```
mount: can't find /dev/sdb1 in /etc/fstab or /etc/mtab
``` and in GUI "Error mounting volume - An error occured while performing an operation on *MY_VOLUME* (Partition 1 of WD MY Passport 070B) Filesystem driver not installed. Details: Error mounting: mount: wrong fs type, bad option, bad superblock on /dev/sdb1,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so"

dmesg | tail:```
FAT: bogus number of reserved sectors
[   21.035764] VFS: Can't find a valid FAT filesystem on dev sdb1.
[   21.185984] UDF-fs: Partition marked readonly; forcing readonly mount
[   21.217442] UDF-fs INFO UDF: Mounting volume 'WD SmartWare', timestamp 2009/11/14 02:34 (1078)
[   21.293525] hda-intel: IRQ timing workaround is activated for card #1. Suggest a bigger bdl_pos_adj.
[   21.997113] EXT4-fs (sdc1): re-mounted. Opts: errors=remount-ro,commit=0
[   26.870307] eth0: no IPv6 routers present
[   48.698292] lo: Disabled Privacy Extensions
[ 1188.575210] FAT: bogus number of reserved sectors
[ 1188.575216] VFS: Can't find a valid FAT filesystem on dev sdb1.
[ 2617.601216] FAT: bogus number of reserved sectors
[ 2617.601221] VFS: Can't find a valid FAT filesystem on dev sdb1.
[ 2691.909953] FAT: bogus number of reserved sectors
[ 2691.909958] VFS: Can't find a valid FAT filesystem on dev sdb1.
[ 2808.905826] FAT: bogus number of reserved sectors
[ 2808.905832] VFS: Can't find a valid FAT filesystem on dev sdb1.
[ 3002.537775] FAT: bogus number of reserved sectors
[ 3002.537780] VFS: Can't find a valid FAT filesystem on dev sdb1.
[ 3018.398099] FAT: bogus number of reserved sectors
[ 3018.398104] VFS: Can't find a valid FAT filesystem on dev sdb1.

```

Please Help me not to loose those files. This is the only priority.

I thank you in advance for your time and I hope a solution can be found.

George.

---

### Post by stamoulohta on 2011-11-19
Found it myself and thought I should post.

So, the magic command is:```
sudo dosfsck -r /dev/sdb

```( for vfat filesystems )

Cheers.

---

### Post by Sidewinder1 on 2011-11-19
Glad you solved your problem! :)
Please mark your thread as "solved."
Thanks, 
Side

---

