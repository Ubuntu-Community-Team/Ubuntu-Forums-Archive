---
title: "Partitioning Issue?"
date: 2006-06-20
forum: General Help
---

### Post by medw1974 on 2006-06-20
I deleted an NTFS partition holding my backup data using qtparted and then created a new ext3 partition to replace it, I have mounted this new partition OK, however it has a folder in it called lost+found which seems to take up just over 1 GIG but which I have no permission to access.

Any idea what this is and how I can get rid of it?

---

### Post by vigleik on 2006-06-20
[QUOTE=medw1974]I deleted an NTFS partition holding my backup data using qtparted and then created a new ext3 partition to replace it, I have mounted this new partition OK, however it has a folder in it called lost+found which seems to take up just over 1 GIG but which I have no permission to access.

Any idea what this is and how I can get rid of it?[/QUOTE]

I don't think that folder takes up 1GB. As far as I know, every ext3 partition (and many other types of partitions?) has a lost+found folder. Don't worry about it. The partition table is what's taking up the space, and there's no way you can avoid that.

Vigleik

---

### Post by medw1974 on 2006-06-21
Thanks for that Vigleik,

I just had a look and yes my main partition also has a lost+found folder.

---

