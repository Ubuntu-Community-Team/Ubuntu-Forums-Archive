---
title: "Issues with assembling a previous array with a fresh install of Lucid"
date: 2010-04-30
forum: General Help
---

### Post by ezhangin on 2010-04-30
I have just completed a fresh install of Lucid and plugged in my previous RAID-5 after installing mdadm and importing my previous mdadm config file.  Upon reboot I had noticed the array was assembled out of the drives (!?) and not the partitions (such as sda1, sdb1, etc) and I have this weird /dev/md0p1 device.  If I stop the original /dev/md0 array and then tell it to assemble from the partitions it works fine (and the md0p1 devices goes away).  I have tried a vast number of changes to my config file but no matter what I do the same thing happens upon reboot.

This is my current config file:

```
# mdadm.conf
#
# Please refer to mdadm.conf(5) for information about this file.
#

# by default, scan all partitions (/proc/partitions) for MD superblocks.
# alternatively, specify devices to scan, using wildcards if desired.
#DEVICE partitions
DEVICE /dev/sd[abcd]1

# auto-create devices with Debian standard permissions
#CREATE owner=root group=disk mode=0660 auto=yes

# automatically tag new arrays as belonging to the local system
#HOMEHOST <system>

# instruct the monitoring daemon where to send mail alerts
MAILADDR XXXXXX@localhost

# definitions of existing MD arrays
ARRAY /dev/md0 UUID=5c73f61e:cd437a9c:5ed43ba4:23c39f97
```

Any ideas?

---

### Post by dino99 on 2010-04-30
found some issues and thread:

[http://ubuntuforums.org/showpost.php?p=8643812&postcount=40](http://ubuntuforums.org/showpost.php?p=8643812&postcount=40)
[http://weait.com/content/install-raid0-ubuntu-lucid-lynx](http://weait.com/content/install-raid0-ubuntu-lucid-lynx)

[https://bugs.launchpad.net/ubuntu/+source/dmraid/+bug/571967](https://bugs.launchpad.net/ubuntu/+source/dmraid/+bug/571967)

[https://bugs.launchpad.net/ubuntu/+source/partman-base/+bug/525425](https://bugs.launchpad.net/ubuntu/+source/partman-base/+bug/525425)

---

### Post by ezhangin on 2010-04-30
I appreciate your help but I am using mdadm and most of those posts cover dmraid.  I tried the one covering mdadm and no such luck; exact same outcome.

---

### Post by dino99 on 2010-04-30
sorry i'm not used with these issues, maybe you'll have more chance into network forum

---

### Post by ezhangin on 2010-04-30
Solved it!

Had to run 

```
mdadm --assemble /dev/md0 --update=homehost
```

and for good measure

```
update-initramfs -u
```

---

