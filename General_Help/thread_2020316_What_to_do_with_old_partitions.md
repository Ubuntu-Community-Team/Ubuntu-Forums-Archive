---
title: "What to do with old partitions?"
date: 2012-07-08
forum: General Help
---

### Post by Lloydb39 on 2012-07-08
I had a hard drive formatted for ext filesystem. Made it external and used gparted to format the primary partition for NFTS. The old extended and swap partitions remain. I read the documentation but I'm still not sure. Should I delete them? I'm going to try to use the external drive on both my Ubuntu and Windows 7 desktops, probably. thanks. You guys always are helpful, and sometimes a lifesaver.

---

### Post by kimda on 2012-07-08
I would copy all data off the drive and in gparted remove all partitions and make one big partition and format as ntfs of ext3/4 if you use mainly Linux.

---

### Post by Lloydb39 on 2012-07-08
> **kimda said:**
> I would copy all data off the drive and in gparted remove all partitions and make one big partition and format as ntfs of ext3/4 if you use mainly Linux.
OK. Just out of curiosity, could I just format the drive NFTS from the Windows computer?

---

### Post by Rexilion on 2012-07-08
You can also format your drive with Ubuntu if you want NTFS.

> aptitude -s -R install gnome-disk-utility ntfs-3g ntfsprogs

Gnome-disk-utility is a format utility, similar to gparted actually.

Ntfs-3g is a very reliable FUSE module that is capable of handling NTFS in Linux (with robust writing capabilities).

Ntfsprogs is required to format drives with the NTFS filesystem.

---

### Post by kimda on 2012-07-08
Yes you can also do this from Windows, but via Ubuntu its also a trivial task. If you feel more comfortable in Windows I would do it in Windows. You can do partitioning and formatting in the diskmanager.

---

