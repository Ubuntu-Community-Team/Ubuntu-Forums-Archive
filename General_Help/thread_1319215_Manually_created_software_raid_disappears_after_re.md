---
title: "Manually created software raid disappears after reboot"
date: 2009-11-08
forum: General Help
---

### Post by VMOS on 2009-11-08
I've already got two raid devices, md0 (for boot) and md1 (for everything else). Now I had this setup working perfectly with 9.04 but I had to do a fresh install of 9.10 and for various complicated reasons I chose not to create the third raid device during initial installation, so here I am trying to do it now
The two drives are identical and have identical partioning, just as in my previous setup. The drives and partioning are also identical to the other two drives which contain md1, which I created during install and is working perfectly

First I do this
**sudo mdadm --create --auto=yes /dev/md3 --level=1 --raid-devices=2 /dev/sdc3 /dev/sde3**

[B]mdadm: /dev/sdc3 appears to contain an ext2fs file system
    size=389600344K  mtime=Thu Jan  1 01:00:00 1970
mdadm: /dev/sde3 appears to contain an ext2fs file system
    size=389600344K  mtime=Thu Jan  1 01:00:00 1970
Continue creating array? y
mdadm: array /dev/md3 started.[/B]

that creates ok, no errors
I've tried it with and without the following two lines (makes no difference)
[B] e2fsck /dev/md3
 resize2fs /dev/md3[/B]

then I do this
**sudo mkfs.ext4 /dev/md3**
that formats the drive ok, again no errors

then I do this
** sudo mount -t auto /dev/md3 /store**

and that mounts it, works fine, all good.
then I **vi /etc/fstab** and add the line
**/dev/md3 /store ext4 rw,errors=remount-ro 0 0**

I've also tried with and without this step (makes no difference)
[B]dpkg-reconfigure mdadm
[/B]
then I reboot. When it starts up, the folder /store is still there but md3 isn't mounted, /etc/mtab doesn't show it, nor does df -h, so I try this

**sudo mount -t auto /dev/md3 /store**
and get
**mount: special device /dev/md3 does not exist**

so I try this again
**sudo mdadm --create --auto=yes /dev/md3 --level=1 --raid-devices=2 /dev/sdc3 /dev/sde3**
and get
[B]mdadm: /dev/sdc3 appears to contain an ext2fs file system
    size=389600256K  mtime=Sun Nov  8 13:39:41 2009
mdadm: /dev/sdc3 appears to be part of a raid array:
    level=raid1 devices=2 ctime=Sun Nov  8 10:43:33 2009
mdadm: Cannot open /dev/sde3: Device or resource busy
mdadm: create aborted
[/B]

hmm, lsof | grep sdc doesn't show it being in use. I've been through this cycle half a dozen times and I can't do anything with the drives until I boot from a livecd and run gparted and format them

any ideas?

---

### Post by laluz on 2009-11-08
if your array is already created the command to get it back running is mdadm --assemble , not create.
What does cat /proc/mdstat tell you?

---

### Post by VMOS on 2009-11-08
I'm not sure about the asemble syntax
**sudo mdadm --assemble /dev/md3**
gives me
**mdadm: /dev/md3 not identified in config file**

and **sudo mdadm --assemble --scan** doesn't give any output

But **cat /proc/mdstat** gives 
```

md_d3 : inactive sdc3[0](S)
      389600256 blocks

md1 : active raid1 sdb3[1] sda3[0]
      389600256 blocks [2/2] [UU]

md0 : active raid1 sde1[3] sdb1[1] sda1[0] sdc1[2]
      128384 blocks [4/4] [UUUU]
```

so I **sudo mount -t extfs4 /dev/md_d3 /store**
and it mounts ok, I then adjsuted /etc/fstab to suit, rebooted and it's not working again and I can't mount it.

```
$ sudo mount -t auto /dev/md_d3 /store
mount: you must specify the filesystem type
$ sudo mount -t ext4 /dev/md_d3 /store
mount: wrong fs type, bad option, bad superblock on /dev/md_d3,
       missing codepage or helper program, or other error
       (could this be the IDE device where you in fact use
       ide-scsi so that sr0 or sda or so is needed?)
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

$ sudo mkfs.ext4 /dev/md_d3/
mke2fs 1.41.9 (22-Aug-2009)
Could not stat /dev/md_d3/ --- Not a directory
```

if I then **$ sudo mdadm --assemble --scan**
I get [B]mdadm: /dev/md/3 has been started with 1 drive (out of 2).
[/B]
but I still can't mount it as md_d3, although **cat /proc/mdstat** now gives
```
md3 : active raid1 sdc3[0]
      389600256 blocks [2/1] [U_]

md_d3 : inactive sde3[1](S)
      389600256 blocks

md1 : active raid1 sdb3[1] sda3[0]
      389600256 blocks [2/2] [UU]

md0 : active raid1 sdb1[1] sde1[3] sdc1[2] sda1[0]
      128384 blocks [4/4] [UUUU]
```
and if I **sudo mount -t ext4 /dev/md3 /store** it works then

Ok, this is good progress, I don't have to rebuild the thing from scratch every time, but any ideas how I might have it attach itself on bootup?

---

### Post by VMOS on 2009-11-08
figured it out, do this
sudo mdadm --detail --scan

and that gives
ARRAY /dev/md0 level=raid1 num-devices=4 metadata=00.90 UUID=56a0cc07:7d66690f:743149e1:e02949c4
ARRAY /dev/md1 level=raid1 num-devices=2 metadata=00.90 UUID=0054022f:c6e0bb5b:ae760f5d:7b2f316a
ARRAY /dev/md3 level=raid1 num-devices=2 metadata=00.90 spares=1 UUID=fcc49e72:8d14cbe9:a10944d4:2bf14585

I added the last line into /etc/mdadm/mdadm.conf and bingo the drive is still there after reboot.

It's a bit odd as many of the guides I've seen say that mdadm.conf shouldn't be used

Anywya, thanks for your help

---

