---
title: "Why this /dev/mapper/sil_ajbhajceccfg automount?!?"
date: 2010-01-17
forum: General Help
---

### Post by Boushard on 2010-01-17
Hi guys,

since I reinstalled ubuntu for restoring my MyBookWorld NAS I have this damn partition or device that autoload on startup as a distinct drive but is the same drive as /dev/sda.  That device block me to format /dev/sda because is still mounted.

So how can I stop this thing to be automounted!?!?

Maybe this have already been discuss but I can't find it!!

---

### Post by Leppie on 2010-01-17
if it automounts, it's most probably in your fstab.

---

### Post by Boushard on 2010-01-17
> **Leppie said:**
> if it automounts, it's most probably in your fstab.

Can you explain a little bit more, I'm a noob in linux for this type of thing.

How can I tell to the OS to not look for this device on startup!?!  Or just delete it when I'm started to do what I have to do?!?

---

### Post by Leppie on 2010-01-17
if you have an entry for this partition in your fstab, it will be mounted at boot.
could you post your fstab:
```
cat /etc/fstab
```

---

### Post by Boushard on 2010-01-17
```
# cat /etc/fstab
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/host/ubuntu/disks/root.disk /               ext4    loop,errors=remount-ro 0       1
/host/ubuntu/disks/swap.disk none            swap    loop,sw         0       0
```

Looks like this!!

I have 2 HDD plug in the system, 1WD 500Gb, 1WD 640Gb green.  The first is the one I want to work on, and the second is the OS drive!!

---

### Post by Leppie on 2010-01-17
could you also post the output of the following command:
```
sudo fdisk -l
```

---

### Post by Boushard on 2010-01-31
After erase the disk an fill it with "0" with HDTune the f%$"/? dev/mapper still show at startup.

@Leppie

The fdisk -l comman output this

```
root@ubuntu:~# sudo fdisk -l

Disque /dev/sda: 500.1 Go, 500107862016 octets
255 têtes, 63 secteurs/piste, 60801 cylindres
Unités = cylindres de 16065 * 512 = 8225280 octets
Identifiant de disque : 0x00000000

Le disque /dev/sda ne contient pas une table de partition valide

Disque /dev/sdb: 640.1 Go, 640135028736 octets
255 têtes, 63 secteurs/piste, 77825 cylindres
Unités = cylindres de 16065 * 512 = 8225280 octets
Identifiant de disque : 0x0000f397

Périphérique Amorce  Début        Fin      Blocs     Id  Système
/dev/sdb1   *          13       77826   625027072    7  HPFS/NTFS

```

---

### Post by Leppie on 2010-01-31
i'm not 100% sure, but i think you still are loading the lvm kernel module.
try the following:
```
sudo umount /dev/mapper/sil_ajbhajceccfg
sudo rmmod dm-mod
```
this should unmount the volume and unload the kernel module.

if you do not require lvm access, remove the package from your install:
```
sudo apt-get purge lvm2
```

---

