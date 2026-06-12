---
title: "Stale NFS file handle"
date: 2009-10-22
forum: General Help
---

### Post by glendavee on 2009-10-22
I'm trying to delete a folder from a usb drive. I get the following error message 
 "Could not remove '/media/usb-pen4gb/.Trash-1000/files/rdiff-backup-data/increments/home/david/.cxoffice/Unsupported/dosdevices': Stale NFS file handle"
I've also tried via terminal using rm -rf but get same result. I need to get rid of these files as I want to use the drive as destination for File Backup Manager.  How can I get rid of these files?

---

### Post by alphaniner on 2009-10-22
Are you able to unmount the usb drive?  If so, then re-mount it and you should be able to delete the folder.

But the error is weird, NFS is Network File System...

---

### Post by glendavee on 2009-10-22
unmounting and remounting the drive makes no difference. The drive originally did have NFS ex windows files, but I reformated and changed file system to ext3 using mkfs.ext3

---

### Post by alphaniner on 2009-10-22
NTFS is the Windows filesystem.
NFS is different.  It's the Linux/Unix filesystem for sharing over network.

Unless you have some sort of NFS sharing set up, I dunno what to tell you.  Sorry.

---

