---
title: "Mysterious system Reserved partition mounting"
date: 2012-09-15
forum: General Help
---

### Post by nyamina on 2012-09-15
I've just installed Windows 7 (only because Black Mesa is finally out! Roll on Steam for Ubuntu...), followed by Ubuntu 12.04, with the home folder on a separate partition.

The thing is, now a mysterious "system reserved" partition mounts automatically. Inside it are folders called "Boot", "System Volume Information" and then two files called "bootmgr" and "BOOTSECT.mgr". I suspect it's something from the the Windows 7 partition, but I would like to stop it automatically mounting in Ubuntu.

---

### Post by Epodx64 on 2012-09-15
Could you post the results from
```

dh -h

```
from a terminal and post them back here?

---

### Post by arsenic23 on 2012-09-15
Look at the contents of /etc/fstab

The partition should be listed here if it is mounting automatically. 
You can remove the line containing that partition or just add *noauto* into the options column of that line.

---

### Post by nyamina on 2012-09-15
> **Epodx64 said:**
> Could you post the results from
```

dh -h

```from a terminal and post them back here?
The result I got back was ```
The program 'dh' is currently not installed.  You can install it by typing:
sudo apt-get install debhelper
```.

> **arsenic23 said:**
> Look at the contents of /etc/fstab

The partition should be listed here if it is mounting automatically. 
You can remove the line containing that partition or just add *noauto* into the options column of that line.
I'm just going to try that now.

---

### Post by Epodx64 on 2012-09-15
opps i meant 
```

df -h

```
sorry

---

### Post by nyamina on 2012-09-15
Well it looks to be solved: I rebooted again, and it's not mounting anymore, I have no earthly idea why, but I guess it's solved. Must have been the ghost in the machine! Thanks anyway though :)

---

### Post by oldfred on 2012-09-15
That is the standard hidden 100MB Windows boot/repair partition. In Windows you do not normally see it. But it is the partition you use to boot from in Windows and the one that grub chain loads to to boot Windows.

You can hide that folder, either by permanent mounting and not showing it.

Hide mount 
```
UUID=200C11850C1156DE /mnt/SysRes ntfs defaults,noauto 0 0
```Hide windows mount with noauto: 777 is no permissions at all
```
/dev/sda2 /Windows/sda2 ntfs defaults,noauto,umask=777 0 0

```It may be sda1 or sda2 depending on whether the vendor recovery partition is first or last in partition table. 

#If you use UUID then you have to find UUIDs:
sudo blkid -c /dev/null -o list
#make a mount point for the hidden partition
sudo mkdir /mnt/SysRes
#or 
sudo mkdir /Windows/sda2
sudo cp /etc/fstab /etc/fstab.backup
gksu gedit /etc/fstab

---

### Post by nyamina on 2012-09-15
> **oldfred said:**
> That is the standard hidden 100MB Windows boot/repair partition. In Windows you do not normally see it. But it is the partition you use to boot from in Windows and the one that grub chain loads to to boot Windows.

You can hide that folder, either by permanent mounting and not showing it.

Hide mount 
```
UUID=200C11850C1156DE /mnt/SysRes ntfs defaults,noauto 0 0
```Hide windows mount with noauto: 777 is no permissions at all
```
/dev/sda2 /Windows/sda2 ntfs defaults,noauto,umask=777 0 0

```It may be sda1 or sda2 depending on whether the vendor recovery partition is first or last in partition table. 

#If you use UUID then you have to find UUIDs:
sudo blkid -c /dev/null -o list
#make a mount point for the hidden partition
sudo mkdir /mnt/SysRes
#or 
sudo mkdir /Windows/sda2
sudo cp /etc/fstab /etc/fstab.backup
gksu gedit /etc/fstab
Well it is still there in Nautilus, under "Devices" which is kind of annoying, so I still might try and hide it, but I also don't want to mess up my Windows partition, so if I do, I'll let you know how it goes. Thanks :)

---

