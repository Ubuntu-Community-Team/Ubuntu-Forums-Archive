---
title: "Make HDDs have static /dev/sd*"
date: 2011-02-26
forum: General Help
---

### Post by cpressland on 2011-02-26
Hey Guys wassup?

I'm having a little trouble with a mdadm RAID array at the moment in which the four hard drives in the array change their /dev/sdb /dev/sdc /dev/sdd/ /dev/sde placement on every reboot.

How can I make all drives retain a static /dev/ location?

Thanks

Chris

---

### Post by gsgleason on 2011-02-26
That shouldn't be necessary.
In my mdadm.conf, I just do this:

DEVICE /dev/sd*

---

### Post by cpressland on 2011-02-26
So my array currently looks like this:

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

# This file was auto-generated on Thu, 24 Feb 2011 18:05:38 +0000
# by mkconf $Id$

ARRAY /dev/md0 level=raid5 num-devices=4 UUID=8906318d:50dc25cc:ef9b5c7a:c6693726
```

You're suggesting I change it to:

```
# mdadm.conf
#
# Please refer to mdadm.conf(5) for information about this file.
#

# by default, scan all partitions (/proc/partitions) for MD superblocks.
# alternatively, specify devices to scan, using wildcards if desired.
DEVICE /dev/sd*

# auto-create devices with Debian standard permissions
CREATE owner=root group=disk mode=0660 auto=yes

# automatically tag new arrays as belonging to the local system
HOMEHOST <system>

# instruct the monitoring daemon where to send mail alerts
MAILADDR root

# definitions of existing MD arrays

# This file was auto-generated on Thu, 24 Feb 2011 18:05:38 +0000
# by mkconf $Id$

ARRAY /dev/md0 level=raid5 num-devices=4 UUID=8906318d:50dc25cc:ef9b5c7a:c6693726
```

And this should prevent it from rebuilding on EVERY reboot?

---

### Post by gsgleason on 2011-02-26
Yes, and comment out any lines you're not using, like HOMEHOST

---

### Post by wiggly81 on 2011-02-26
i had a similar probelem  when trying to get a hard drive to mount on boot using fstab ( i know its not really the same but still might work )
instead of using 
```
DEVICE /dev/sd* 
```
can you use 
```
UUID=????????????????
```
you can get the uuids by typing 
```
sudo blkid
```
maybe im way of the mark i no nothing about raid config

---

### Post by psusi on 2011-02-26
The default setting of "partitions" will work just fine.  Mdadm does not care if the drives change order.

---

