---
title: "Grub fails to find stage 1"
date: 2009-08-04
forum: General Help
---

### Post by tiddlydum on 2009-08-04
I'm running a dual-boot dual-HDD system with XP on one disk and Ubuntu on another. I was recently running them both on the same disk. After removing Ubuntu from the XP disk and reinstalling it on the other, Grub broke. I opened the Ubuntu live CD to try to restore grub, but this keeps happening:
```

grub> find /boot/grub/stage1
find /boot/grub/stage1

Error 15: File not found

```
Also:
```

grub>root (hd0,1)
root (hd0,1)

Error 21: Selected disk does not exist.

```
This is being run from a Ubuntu 64 bit v9.04 live install disk, and both HDDs can be mounted.

---

### Post by lisati on 2009-08-04
Has the information [here]("http://ubuntuforums.org/showpost.php?p=6897654&postcount=3") changed, e.g. have you got rid of Windows 7?

---

### Post by tiddlydum on 2009-08-04
It isn't running Windows 7. It died when I changed the screen resolution, so Ubuntu is now sitting on top of it's grave. Also, the results of my fdisk -l:
```
Disk /dev/sda: 750.1 GB, 750156374016 bytes
255 heads, 63 sectors/track, 91201 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xf88fa528

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       89745   720876681   83  Linux
/dev/sda2           89746       91201    11695320    5  Extended
/dev/sda5           89746       91201    11695288+  82  Linux swap / Solaris

Disk /dev/sdb: 640.1 GB, 640135028736 bytes
255 heads, 63 sectors/track, 77825 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xe18ae18a

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       77825   625129281    7  HPFS/NTFS

```

---

### Post by dandnsmith on 2009-08-04
Your linux is now in (hd0,0) as far as grub is concerned - I don't know if that helps, or if your boot order in BIOS is messing things up.

---

