---
title: "how to mount lvm2 partitions"
date: 2011-02-07
forum: General Help
---

### Post by beopen on 2011-02-07
i have ubuntu installed on 2 hdd. one of my hdd is having a lvm. I am unable to acess the home partition created in this lvm from my other hdd.
in fact it is not shown at all inside the explorer window, the whole lvm block itself.
if u run disk utility that also does not show the lvm partitions as mounted. 
So what are the steps required to be done to access those LVM partition  from the other disk.

regards

---

### Post by anglican on 2011-02-08
> **beopen said:**
> i have ubuntu installed on 2 hdd. one of my hdd is having a lvm. I am unable to acess the home partition created in this lvm from my other hdd.
in fact it is not shown at all inside the explorer window, the whole lvm block itself.
if u run disk utility that also does not show the lvm partitions as mounted. 
So what are the steps required to be done to access those LVM partition  from the other disk.

regards
```
sudo vgscan --mknodes
sudo vgchange -ay
sudo lvscan
```which will give you a list of available devices to be used with the mount command:
```
sudo mkdir /mnt/<somename>
sudo mount /dev/VolGroup<xx>/LogVol<yy> /mnt/<somename>
```obviously, substitute appropriate vales for <xx>, <yy> and <somename>.

H

---

