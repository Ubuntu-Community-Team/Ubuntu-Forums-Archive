---
title: "Automaticaly Mounting Drives (U8.04)"
date: 2009-07-05
forum: General Help
---

### Post by arjunajay on 2009-07-05
I'm using Ubuntu 8.04(hardy). It was installed in what was previously D: drive on my hraddrive.
How do I get ubuntu to mount C: as /media/disk and E: as /media/disk-1?
Because some times I use E: drive first and it gets labeled as 'disk' which screws up stuff like bookmarks and playlists.
Is there a way to write the path in some other way so that order in which the disks are first accessed doesn't matter?

---

### Post by DeMus on 2009-07-05
> **arjunajay said:**
> I'm using Ubuntu 8.04(hardy). It was installed in what was previously D: drive on my hraddrive.
How do I get ubuntu to mount C: as /media/disk and E: as /media/disk-1?
Because some times I use E: drive first and it gets labeled as 'disk' which screws up stuff like bookmarks and playlists.
Is there a way to write the path in some other way so that order in which the disks are first accessed doesn't matter?


Auto mount Windows disks
Fire up a terminal, to do this click Applications > Accessories > Terminal
Then type (or copy/paste) the following - 1 line at a time
```

sudo aptitude update
sudo aptitude install ntfs-config
```
Ok so when that returns you to user@pcname, that should be installed                 

Next, make sure you have NO drives mounted (they'll usually appear on your desktop). If you have disks mounted, right-click the icons (one by one) and choose unmount.
They also appear when opening Nautilus.
Then run the program from System > Administration > NTFS Configuration Tool

Enter your password when prompted - and choose the drives that you want to be automounted. Click Apply.

Now simply make sure that "Enable Write Support for Internal Drives" is checked and click OK.

---

### Post by arjunajay on 2009-07-06
Does it work for FAT partitions too?Mine are FAT.

---

### Post by taurus on 2009-07-06
Do you have the c drive (first internal harddrive) mounted automatically when you boot Ubuntu?  You can tell it where to mount, mount point, in /etc/fstab.

```
sudo fdisk -l
cat /etc/fstab
df -h
```

---

