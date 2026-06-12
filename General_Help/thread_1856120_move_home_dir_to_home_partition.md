---
title: "move /home dir to /home partition"
date: 2011-10-07
forum: General Help
---

### Post by ottosykora on 2011-10-07
I have now on one of my installs a free partition, I would like to transfer there my /home

OK, copied all so far, owner seems to be set ok, but how do I tell my ubuntu 11.04 about it?

---

### Post by matt_symes on 2011-10-07
Hi

You need to edit your /etc/fstab to point to your new home partition.

There are loads of tutorials on the net.

Here is but one....

[http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)

Kind regards

---

### Post by Frogs Hair on 2011-10-07
There may be something helpful at the link . [http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)

---

### Post by ottosykora on 2011-10-08
OK, have tried both the from psychocat and the other one, but none of them works, or it is all that much confusing .

I have the for home proposed partition partition set up.
It is called sda11
my root and home is on partition sda13
copied the content of /home to the new partition

However the system still takes the 'local' home for use.

I tried the copy , but nothing hapends.

find . -depth -print0 | cpio --null --sparse -pvd /new/
gives only errors out, while the one

sudo rsync -axS --exclude='/*/.gvfs' /home/. /media/home/.

does not do anything at all.

my fstab I modified to:

```
fstab              [BM--] 64 L:[  1+11  12/ 14] *(680 / 682b) 0010 0x00A
# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/sda13      /               ext3    relatime,errors=remount-ro 0       1
/dev/sda15      none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/sda11      /home           ext3     defaults       0      2

```

---

### Post by matt_symes on 2011-10-08
Hi

> fstab              [BM--] 64 L:[  1+11  12/ 14] *(680 / 682b) 0010 0x00A 
# /etc/fstab: static file system information. 
# 
# Use 'vol_id --uuid' to print the universally unique identifier for a 
# device; this may be used with UUID= as a more robust way to name devices 
# that works even if disks are added and removed. See fstab(5).What version of Ubuntu are you using ? Was it installed fresh or upgraded ?

Open a terminal and type

```
mount
```Copy and paste the results back here.

Did you mount it with

```
sudo mount /dev/sda13
```Kind regards

---

### Post by ottosykora on 2011-10-09
the system is updated , I think was done with 8.10 first.
It does not use UUID, just simple /des/sda11 etc.
In fact, the vol_id does not exist on my system apparently.

I have tried all those instrction, but nothing did work. Particularly the strange copy command which I did not understand really, did nothing at all.

Finally:

added the /dev/sda11 as home to the fstab

copied the contents of the home folder to the /dev/sda11 with MC (commander) and rebooted.

Then booted to life media (use parted magic CD for that) and renamed the old home folder on the root partition and moved it away for backup to other backup partition.

all works now

I can not so far understand the extremely complex procedure for this operation when it is in fact rather straight forward.

OK, in recent installed system we may need the UUID , but this is about all.

---

