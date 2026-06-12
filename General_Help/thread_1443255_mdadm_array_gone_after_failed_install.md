---
title: "mdadm array gone after failed install"
date: 2010-03-30
forum: General Help
---

### Post by redilyn on 2010-03-30
I tryed to install ubuntu 10.04 using the beta alternative install cd.

Everything went fine until the partitioning section.

I choose manual partitioning and all my existing partitions were detected correctly included my 2 mdadm raid0 arrays.

I choose md0 as my / partition and choose to format the partition

I choose md1 as my /home partition as choose to keep the data

When I choose to continue and write the changes to disk the install started to create an ext4 partition on md0, the installer then stopped with an error that the kernel could not reread the partition table.

I aborted the installation at this point.

Now I can not access either of my arrays.

I have booted a livecd and installed mdadm. When I checked /etc/mdadm/mdadm.conf my existing arrays were already listed.
```
# mdadm.conf
#
# Please refer to mdadm.conf(5) for information about this file.
#

# by default, scan all partitions (/proc/partitions) for MD superblocks.
# alternatively, specify devices to scan, using wildcards if desired.
DEVICE partitions

# auto-create devices with Debian standard permissions
CREATE owner=root group=disk mode=0660 auto=yes

# automatically tag new arrays as belonging to the local system
HOMEHOST <system>

# instruct the monitoring daemon where to send mail alerts
MAILADDR root

# definitions of existing MD arrays
ARRAY /dev/md0 level=raid0 num-devices=2 UUID=de9c42e9:211092f3:8bfd28c4:4ae3050e
ARRAY /dev/md1 level=raid0 num-devices=2 UUID=6560bfe4:457ae74d:a22b657e:8082cda3

# This file was auto-generated on Wed, 31 Mar 2010 00:52:39 +0000
# by mkconf $Id$
```

When I scan with mdadm it seems to read the md1 partitions correctly
```
ubuntu@ubuntu:~$ sudo mdadm --examine --scan /dev/sda7
ARRAY /dev/md1 level=raid0 num-devices=2 UUID=6560bfe4:457ae74d:a22b657e:8082cda3

```
```
ubuntu@ubuntu:~$ sudo mdadm --examine --scan /dev/sdb2
ARRAY /dev/md1 level=raid0 num-devices=2 UUID=6560bfe4:457ae74d:a22b657e:8082cda3

```

However when I try to activate the arrays md1 fails.
```
ubuntu@ubuntu:~$ sudo mdadm --assemble --scan
mdadm: /dev/md0 has been started with 2 drives.
mdadm: failed to add 8:7 to /dev/md1: Device or resource busy
mdadm: /dev/md1 assembled from 1 drive - not enough to start the array.
```

```
ubuntu@ubuntu:~$ sudo mdadm -A /dev/sda7 /dev/sdb2 /dev/md1
mdadm: cannot open device /dev/sdb2: Device or resource busy
mdadm: /dev/sdb2 has no superblock - assembly aborted

```

Can someone help me, I have no idea what to do from here.

---

### Post by redilyn on 2010-03-31
*Bump*

Any ideas anyone, I really need this partition back asap. Right now I'm stuck on the livecd because I don't want to write anything to the drives till I get this fixed.

---

### Post by redilyn on 2010-04-01
Anyone?

Can someone atleast tell me if its alright to run fsck on sdb2 to try and correct the superblock?

---

### Post by redilyn on 2010-04-04
Solved. Turned out I had actually got the array to assemble and the problem was a messed up partition table.

Running fsck.ext4 solved the problem.

---

