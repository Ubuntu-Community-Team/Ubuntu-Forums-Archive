---
title: "Lost space on Hard Drive"
date: 2009-08-22
forum: General Help
---

### Post by Robbyx on 2009-08-22
gparted says total 299gb with 176gb used. It is a reiserfs partition.

All my file managers say the total of the files in the partition is 69gb.

There appears to be 100gb missing.

I used gparted as as a live cd and had it check and repair the partition. No new space has been freed.

Please, how do I recover the missing space?

---

### Post by scouser73 on 2009-08-22
Have you any unallocated space on the drive?

---

### Post by Robbyx on 2009-08-22
> **scouser73 said:**
> Have you any unallocated space on the drive?

The figures  I quoted are for a partition not a complete drive. In the context of a partition is it possible to have unallocated space?

---

### Post by michy99 on 2009-08-22
What do you get for```
df -h
```Also, check this out:
[https://help.ubuntu.com/community/RecoverLostDiskSpace](https://help.ubuntu.com/community/RecoverLostDiskSpace)

---

### Post by heatblazer on 2009-08-22
What is the drive? Is it, Seagate 11th serial?

---

### Post by Robbyx on 2009-08-22
> **michy99 said:**
> What do you get for```
df -h
```
This is the resulc. The partition I am concerned about is sdb6

```
Filesystem            Size  Used Avail Use% Mounted on
/dev/sdb1              29G  6.1G   21G  23% /
tmpfs                 1.8G     0  1.8G   0% /lib/init/rw
varrun                1.8G  244K  1.8G   1% /var/run
varlock               1.8G     0  1.8G   0% /var/lock
udev                  1.8G  2.9M  1.8G   1% /dev
tmpfs                 1.8G  220K  1.8G   1% /dev/shm
lrm                   1.8G  2.2M  1.8G   1% /lib/modules/2.6.27-14-generic/volatile
/dev/sdb2              30G   25G  3.7G  88% /home
/dev/sdc1             233G   28G  206G  12% /media/mydocs
/dev/sdb5             103G   66G   37G  65% /media/g
/dev/sdb6             300G  175G  125G  59% /media/video
rob@rob-desktop:~$ 


```

---

### Post by Robbyx on 2009-08-22
It seems that simple backup's data directories can not be seen in their true size by any of my file managers in tree view.  They actually contain very large files but somehow that is not being picked up by the file managers when they display folder sizes. Even KDirStat is not displaying the full size. 

The following picked up the files over 2gb and yet they are showing in the file managers as 256 bytes.

```
rob@rob-desktop:/media/video$ sudo  find  /media/video/ -size +2G 
/media/video/My Documents.7z
/media/video/simple backup/2009-06-19_08.31.01.289687.rob-desktop.ful/files.tgz
/media/video/simple backup/2009-08-21_08.03.07.450257.rob-desktop.ful/files.tgz
/media/video/simple backup/2009-07-28_08.20.05.252686.rob-desktop.ful/files.tgz
/media/video/simple backup/2009-08-13_08.13.55.998579.rob-desktop.ful/files.tgz
/media/video/simple backup/2009-08-05_08.43.51.993971.rob-desktop.ful/files.tgz
/media/video/simple backup/2009-07-21_08.25.03.962384.rob-desktop.ful/files.tgz
/media/video/Compress backup of My docs/Full
rob@rob-desktop:/media/video$ 

```

---

