---
title: "rsync vs fat32?"
date: 2011-09-14
forum: General Help
---

### Post by dewdrop_world on 2011-09-14
I've been using rsync to back up files onto an external hard drive. This is working great for my Linux boot partition (ext3), but I have another fat32 partition that I use for sharing files between Linux and Windows. I had backed up the fat32 partition previously, but now, running rsync again, it's recopying every file. I know for sure that not every file changed :) but still, it's redundantly recopying.

Just wondering if anyone knows of any problems with rsync and fat32. If this is going to happen often, I'll have to find another incremental backup tool.

Thanks,
James

---

### Post by papibe on 2011-09-14
I think you are experiencing the [known problem]("ftp://ppp.samba.org/pub/unpacked/rsyncweb/daylight-savings.html") of DST and UTC time conversion of NTFS and FAT file systems.

rsync has an option to deal with that problem:
```
--modify-window=1
```
Start as the example (value 1) and check if that solve the problem. If not maybe a value of 2 may work better.

Hope it helps,
Regards.

---

### Post by oldfred on 2011-09-15
You also have issues of naming conventions. Windows partitions are not case sensitive. So in Windows Downloads & downloads are the same.

Also if copying Linux files you loose all permissions and ownership. If just data you can relatively easily reset, but system files may not be possible to correctly reset.

FAT also has a 4GB file limit. I was backing up large files and wondered why they always were 4GB. Files were just truncated.

Fat does not have a journel, so large FAT partition can take forever to run a chkdsk and may not recover where a NTFS or Linux partition will.

If for backing up Linux data and files use Linux formats. For shared data only with Windows use NTFS.

---

