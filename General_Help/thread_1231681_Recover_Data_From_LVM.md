---
title: "Recover Data From LVM"
date: 2009-08-04
forum: General Help
---

### Post by brianafischer on 2009-08-04
I have an old hard drive that is in the LVM2 structure.  I would like to find out what data is on this hard drive, but cannot mount it using the "mount -a" command.  I ran the following lvm tools and need some help.  Please let me know how I can recover/view the data on this drive, it would be greatly appreciated!

```
mythhd@mythhd:~$ sudo pvscan;sudo vgscan;sudo lvscan
[sudo] password for mythhd: 
  PV /dev/sdc2   VG VolGroup00   lvm2 [232.78 GB / 0    free]
  Total: 1 [232.78 GB] / in use: 1 [232.78 GB] / in no VG: 0 [0   ]
  Reading all physical volumes.  This may take a while...
  Found volume group "VolGroup00" using metadata type lvm2
  ACTIVE            '/dev/VolGroup00/LogVol00' [10.00 GB] inherit
  ACTIVE            '/dev/VolGroup00/LogVol01' [221.78 GB] inherit
  ACTIVE            '/dev/VolGroup00/LogVol02' [1.00 GB] inherit

```

---

### Post by Glyndwr on 2009-08-04
mount -a only mounts filesystems with entries in /etc/fstab.  Did you try mounting it from the command line ?

---

### Post by brianafischer on 2009-08-04
> **Glyndwr said:**
> mount -a only mounts filesystems with entries in /etc/fstab.  Did you try mounting it from the command line ?

That was it.  For some reason, I thought the fstab would detect LVM

```
mythhd@mythhd:/mnt$ sudo mkdir LogVol00
mythhd@mythhd:/mnt$ sudo mount /dev/VolGroup00/LogVol00 /mnt/LogVol00/
mythhd@mythhd:/mnt$ sudo mkdir LogVol01
mythhd@mythhd:/mnt$ sudo mount /dev/VolGroup00/LogVol01 /mnt/LogVol01/
mythhd@mythhd:/mnt$ sudo mkdir LogVol02
mythhd@mythhd:/mnt$ sudo mount /dev/VolGroup00/LogVol02 /mnt/LogVol02/
/dev/mapper/VolGroup00-LogVol02 looks like swapspace - not mounted
mount: you must specify the filesystem type

```

---

