---
title: "folder appears empty even though it isn't. I/O error on ls. screenshots included"
date: 2010-05-17
forum: General Help
---

### Post by chriskin on 2010-05-17
multiple issues started happening on a partition of mine. (probably whole installation and i haven't noticed since most of my files are on that partition)
the most important one is that a certain folder appears to be empty even though it isn't. (screenshot "issue1")

the second issue is that files that are no longer on on the root folder of the partition (for example, lynx5.jpg on the screenshot "issue2") appear to be there. on "issue2" screenshot, it's the lynx image and the Gr_trees folder.
removing them by deleting them doesn't work. moving there somewhere else makes them temporary gone - they reappear on reboot though.

(the screenshots seem to be automatically converted to jpg when uploaded, if there is a problem you can find them here as well:
[http://dl.dropbox.com/u/452182/issue1.png](http://dl.dropbox.com/u/452182/issue1.png)
[http://dl.dropbox.com/u/452182/issue2.png](http://dl.dropbox.com/u/452182/issue2.png)  )


edit : 
even though it's not the normal way to solve a problem : if reinstallation is _definitely_ going to solve the problem, i have nothing against it.

---

### Post by mikewhatever on 2010-05-17
Looks like a file system related problem. From the pictured, it looks like the partition in question is on an external device, and if that's the case, just unmount it and run a file system check.
Post the output of *sudo fdisk -l* if you need help with that.

---

### Post by jbrown96 on 2010-05-17
```
mount -l
``` would help as well

Edit: that's a lowercase L, not a one.

---

### Post by chriskin on 2010-05-18
> **mikewhatever said:**
> Looks like a file system related problem. From the pictured, it looks like the partition in question is on an external device, and if that's the case, just unmount it and run a file system check.
Post the output of *sudo fdisk -l* if you need help with that.



it's an internal partition, not an external one. 

```
Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0006be8b

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *       51878       60801    71682030    7  HPFS/NTFS
/dev/sda2           51623       51877     2048287+  82  Linux swap / Solaris
/dev/sda3           42699       51622    71681999+   5  Extended
--------------
/dev/sda4               1       42698   342971653+   7  HPFS/NTFS 
^^^^^^^^it's this one, sda4. ^^^^^^^^^
--------------
/dev/sda5           42699       51622    71681998+  83  Linux

Partition table entries are not in disk order

```

can you tell me what i am supposed to do next?

---

### Post by jerome1232 on 2010-05-18
Those particular files wouldn't happen to be compressed using the ntfs file system compression would they? I know there are certain issues when dealing with that.

Other than than that I would try running chkdsk on the thing from windows.

---

### Post by chriskin on 2010-05-18
> **jerome1232 said:**
> Those particular files wouldn't happen to be compressed using the ntfs file system compression would they? I know there are certain issues when dealing with that.

Other than than that I would try running chkdsk on the thing from windows.

it is ntfs, in a stupid attempt to make them available on windows (that i never boot to :S)

is there any way to salvage the files or are they "doomed"?

windows shows that everything is fine, files are missing there too though.

---

### Post by jerome1232 on 2010-05-18
I think you misunderstood me, ntfs supports compression and encryption at the file system level, ntfs-3g, the driver that allows linux to access ntfs volumes, doesn't fully support ntfs compression and encryption.

The solution to THAT problem is to decompress/decrypt the files/folders from Windows. 

If you are having issues in Windows as well than that is not your issue, your issue is with errors in the file system. Try running chkdsk, scan the disk for errors from within windows.

You might also want to run some smart tests on the drive imo to see if it is going out itself.

---

### Post by chriskin on 2010-05-18
> **jerome1232 said:**
> I think you misunderstood me, ntfs supports compression and encryption at the file system level, ntfs-3g, the driver that allows linux to access ntfs volumes, doesn't fully support ntfs compression and encryption.

The solution to THAT problem is to decompress/decrypt the files/folders from Windows. 

If you are having issues in Windows as well than that is not your issue, your issue is with errors in the file system. Try running chkdsk, scan the disk for errors from within windows.

You might also want to run some smart tests on the drive imo to see if it is going out itself.

5 check disks later, windows found an error and solved it. seems that my files are back , thanks :)

can explain your last sentence? the drive is really new (around 2-3 months) if you mean that it's dying.

---

