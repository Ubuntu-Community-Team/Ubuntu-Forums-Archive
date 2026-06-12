---
title: "Backing up Linux &amp; Windows Data"
date: 2010-06-18
forum: General Help
---

### Post by karthik.V.M. on 2010-06-18
Hi All,

I am using Ubuntu & Vista as dual boot. I bought a 1 TB WD external hard disk to backup both my linux & windows data. The hard disk is pre formated with NTFS. Hence linux file's permissions are changed when I save linux data (with ext3 FS) into external HD (with NTFS) and back it up. But the contents are ok. Also chmod or chown does not work on extenal HD as it is NTFS. 

1) Since I need to backup both my windows and linux data should I create separate partitions in external HD for linux and Windows? or is there a way to save linux files properly in NTFS itself?

2) If creating separate partitions is the only solution, what FS should I use for linux partition? whether ext3? or is there some FS specially for backups?

Please let me know your comments.

Thanks for your time,
Karthik

---

### Post by marshmallow1304 on 2010-06-18
AFAIK, the two main options are

1) Create separate partitions (one with NTFS and one with ext3 or ext4) and keep the backups separate.

2) Keep the drive as a single NTFS partition and put your Linux backups in tar archives, making sure to extract them with the -p flag to preserve permissions.

---

### Post by karthik.V.M. on 2010-06-21
Thanks a lot marshmallow 1304. I did not think of tar archives. So there is no separate file system specifically for backups right?

---

