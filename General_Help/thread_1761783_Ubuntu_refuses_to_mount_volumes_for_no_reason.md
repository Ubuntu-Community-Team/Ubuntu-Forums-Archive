---
title: "Ubuntu refuses to mount volumes for no reason"
date: 2011-05-18
forum: General Help
---

### Post by stn21 on 2011-05-18
Hi,

this is all wrong:

# cd /root
# mkdir ./mnt

# mount /dev/sda7 ./mnt
mount: /dev/sda7 is already mounted or mnt is in use
# umount /dev/sda7
umount: /dev/sda7 is not mounted
# umount ./mnt
umount: ./mnt is not mounted

so /dev/sda7 ist NOT mounted and ./mnt is NOT in use.
So why does ubuntu refuse to mount ???

THX
stn


additional info:
* /dev/sda7 is a completely normal ext4-volume
* ./mnt is a very normal subfolder of /root
* neither mnt nor /dev/sda7 are "in use" . lsof | fgrep "sda7" and lsof|fgrep "mnt" show nothing

---

### Post by TeoBigusGeekus on 2011-05-19
Try creating a mount point in a different folder, not in /root.

---

### Post by stn21 on 2011-05-22
Much later [IMG]http://media.cdn.ubuntu-de.org/wiki/attachments/08/28/evil.png[/IMG]


Mystery partially solved. The following worked for 2 out of 3 Disks. The third one is still unavailable.



The system can actually "use" partitions without showing them in mount, lsof, blkid etc


This happens if the partition was previously part of a raid. Per default mdadm automatically scans all existing partitions and apparently locks any "raid-suspects", even if they are not actually used in a raid.



To solve that:



* edit /etc/mdadm/mdadm.conf

* remove/comment these lines:

```

# by default, scan all partitions (/proc/partitions) for MD superblocks. 
# alternatively, specify devices to scan, using wildcards if desired. 
# DEVICE partitions

```[FONT=monospace]
It may be helpful to delete lines from the block

[/FONT]```
# definitions of existing MD arrays
```Then reboot.

stn

---

### Post by stn21 on 2011-05-22
This happens on one specific computer with ubuntu 10.10.

The same disks mount fine on several other computers one with Debian Squeeze, others with ubuntu 10.10.

So what is the problem here ??

---

