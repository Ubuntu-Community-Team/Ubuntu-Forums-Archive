---
title: "Move /home after install..."
date: 2012-06-14
forum: General Help
---

### Post by ivanox1972 on 2012-06-14
Hi, all I have notebook with ssd and hard disc.
In past I have used dual boot, now I just want ubuntu.
So I have installed and health ubuntu on ssd and hard disc with few ntfs partitions, which now I want to convert.
i want to make one big ext4 partition on hd and move there /home. Is it possible- how to do this???
Also, in the moment I do not have swap partition, but I want to make one- how to do this?
thanks

---

### Post by Kira_Belka on 2012-06-14
hi here, certainly it's possible.
when you 'll "convert" partition to ext4 and copy all your data to new partition.
you can simply mount your new partition as "/home"(using fstab/mtab).
you can read about it [here]("http://beginlinux.com/blog/2009/12/editing-mount-points/")

---

### Post by mwinthrop on 2012-06-14
I recently used this web site ([https://help.ubuntu.com/community/Partitioning/Home/Moving](https://help.ubuntu.com/community/Partitioning/Home/Moving)) to move my /home to a new partition my hard drive.  It worked great for me.

---

