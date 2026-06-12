---
title: "How to fix &quot;Error removing file: Read-only file system&quot; with a"
date: 2010-05-31
forum: General Help
---

### Post by v0line on 2010-05-31
Was struggling with this for a little, no really clear answers around.

Anyways, edit /etc/mstab, kill the entire line with the faulty drive.

Unplug the drive/usb, restart, then do a

```
sudo fsck -r /dev/whatever
```

umount it, then remount and it should be fixed :guitar:

---

### Post by WorMzy on 2010-05-31
Do you mean fstab? mtab is a just list of known mounted devices, editing it won't make any difference. Editing fstab will, as that is the file that dictates where and how files are mounted.

Also, fsck can only check and repair (if necessary) Linux partitions, such as ext#. Don't use it on NTFS or FAT volumes.

---

