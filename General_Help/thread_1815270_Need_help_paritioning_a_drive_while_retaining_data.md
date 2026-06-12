---
title: "Need help paritioning a drive while retaining data"
date: 2011-07-31
forum: General Help
---

### Post by distended on 2011-07-31
Hello,

I have an NTFS-formatted hard drive with data on it that I'd like to keep.  This hard drive is independent of my current Ubuntu install and has no other operating systems on it.  It's a 400 GB hd with about 300 GB worth of data on it.  

Is it possible to create say an 80 GB partition without disturbing the data already on the disk, and if so, what is the best way to do so?  Thanks in advance for any help.

---

### Post by dim_hyder on 2011-07-31
It's always best practice to backup data before partitioning - just in case the worst happens (I've skipped this step in the past and never had issues).

gparted will allow you to partition this drive.

to install go to the terminal and type

sudo apt-get install gparted

You will need to unmount the 400GB drive before re-partitioning

---

### Post by distended on 2011-08-01
Ah. Exactly what I was looking for.  Thanks a lot Dim!

---

