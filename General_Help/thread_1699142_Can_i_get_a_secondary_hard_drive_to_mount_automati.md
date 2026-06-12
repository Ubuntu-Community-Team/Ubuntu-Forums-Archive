---
title: "Can i get a secondary hard drive to mount automatically on start up?"
date: 2011-03-03
forum: General Help
---

### Post by Macfunky on 2011-03-03
I have two hard drives in my computer, one for the operating system and the other solely for storage. They both have ext4 filesystems. Is there any way that i can have my storage hard drive to automatically mount on start up?

---

### Post by seawolf167 on 2011-03-03
Yup, you'll want to add an entry for it in /etc/fstab

See the link in my signature for more information on how to do this. I can help you if you post the output of 

```
sudo fdisk -l
```and tell me which partition you want to automount

---

### Post by TeoBigusGeekus on 2011-03-03
Mount your storage hd and post us the output of
```
mount
```
```
sudo fdisk -l
```
```
blkid
```
and the contents of your fstab file
```
gksu gedit /etc/fstab
```

---

### Post by Macfunky on 2011-03-03
> **seawolf167 said:**
> Yup, you'll want to add an entry for it in /etc/fstab

See the link in my signature for more information on how to do this. I can help you if you post the output of 

```
sudo fdisk -l
```and tell me which partition you want to automount

Output of sudo fdisk -l and i want to mount Disk /dev/sdb

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000d1f05

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       18663   149903360   83  Linux
/dev/sda2           18663       19458     6384641    5  Extended
/dev/sda5           18663       19458     6384640   82  Linux swap / Solaris

Disk /dev/sdb: 300.1 GB, 300069052416 bytes
255 heads, 63 sectors/track, 36481 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00053964

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       36482   293035008   83  Linux

---

### Post by seawolf167 on 2011-03-03
Sorry, forgot to ask for

```
blkid
```

to get the format type (the mount via. UUID is optional)

---

### Post by Macfunky on 2011-03-03
> **seawolf167 said:**
> Sorry, forgot to ask for

```
blkid
```

to get the format type (the mount via. UUID is optional)

Output -

/dev/sda5: UUID="bd87b84d-fda0-4aad-9ac0-33ca31b028ce" TYPE="swap" 
/dev/sdb1: UUID="9E96-E33D" TYPE="vfat"

---

### Post by seawolf167 on 2011-03-03
Add either of the below entries to /etc/fstab

```
sudo mkdir /mount/point/here
sudo gedit /etc/fstab
```where /mount/point/here is the name of the directory you want to mount your partition (i.e. /media/datadrive or /mnt/externaldrive)

```
# Entry for /dev/sdb1:
/dev/sdb1 /mount/point/here vfat defaults,user,dmask=027,fmask=137 0 0
```-----or-----

```
# Entry for /dev/sdb1:
UUID=9E96-E33D /mount/point/here vfat defaults,user,dmask=027,fmask=137 0 0
```

---

### Post by MrEgg on 2011-03-03
You are aware that your 2nd hard drive (sdb) is not ext4, but FAT, right? I'm just pointing this out because of what you described both your drives to be in your first post.

---

### Post by Macfunky on 2011-03-03
> **seawolf167 said:**
> Add either of the below entries to /etc/fstab

```
sudo mkdir /mount/point/here
sudo gedit /etc/fstab
```where /mount/point/here is the name of the directory you want to mount your partition (i.e. /media/datadrive or /mnt/externaldrive)

```
# Entry for /dev/sdb1:
/dev/sdb1 /mount/point/here vfat defaults,user,dmask=027,fmask=137 0 0
```-----or-----

```
# Entry for /dev/sdb1:
UUID=9E96-E33D /mount/point/here vfat defaults,user,dmask=027,fmask=137 0 0
```

Thanks for the help but i'm a bit confused. The 160gb hard drive has the OS on it and it's the 300gb i want to automount upon login. I could be wrong but i think if i were to add that, that it would be the 160gb hard drive? Just want to make sure before i go ahead and add it to fstab.

---

### Post by Macfunky on 2011-03-03
> **MrEgg said:**
> You are aware that your 2nd hard drive (sdb) is not ext4, but FAT, right? I'm just pointing this out because of what you described both your drives to be in your first post.

Yes i'm aware of that now :P

---

### Post by seawolf167 on 2011-03-03
> **Macfunky said:**
> 
**Disk /dev/sda: 160.0 GB**, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000d1f05

   Device Boot      Start         End      Blocks   Id  System
[B]/dev/sda1   *           1       18663   149903360   83  Linux
/dev/sda2           18663       19458     6384641    5  Extended
/dev/sda5           18663       19458     6384640   82  Linux swap / Solaris[/B]

**Disk /dev/sdb: 300.1 GB**, 300069052416 bytes
255 heads, 63 sectors/track, 36481 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00053964

   Device Boot      Start         End      Blocks   Id  System
**/dev/sdb1               1       36482   293035008   83  Linux**

From your previous post, your 160GB drive contains you Ubuntu file system, the 300GB drive contains the vfat filesystem. The fstab lines I gave you earlier

```
# Entry for /dev/sdb1:
UUID=9E96-E33D /mount/point/here vfat defaults,user,dmask=027,fmask=137 0 0
```is for your 300GB filesystem, i.e.

```
/dev/sdb1: UUID="9E96-E33D" TYPE="vfat"
```Notice that the UUIDs are the same. So the previous fstab entries will be ok to mount your 300GB filesystem

---

