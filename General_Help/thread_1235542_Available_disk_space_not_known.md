---
title: "Available disk space not known"
date: 2009-08-09
forum: General Help
---

### Post by Robbyx on 2009-08-09
Disk Usage Analyser says I have used 73GB of a partition.
Nautilus says I have 115.3GB free space on that partition.

Total=188GB

PC Man says the size of the partition is 299.2GB
Disk user analysis says it is 321.3GB in the tree display but in the devices list it says it is 299.2 with 115.3 available.

There are no hidden files or directories.

Should I  have 321-73=248GB available?

Could someone please tell me where to look for the difference between the 248 and 115. I would like to know what is taking up the space.

---

### Post by Narada on 2009-08-09
Are you sure you're looking at the same partitions? Which partition is it that you're looking at? The most reliable way I would recommend viewing partition free space is opening up a terminal and typing: 
```
df -h --total
```
If you have everything on your root partition, for example, you could be viewing your /var and / partitions and see two different sizes/capacities.

---

### Post by Robbyx on 2009-08-09
> **Narada said:**
> Are you sure you're looking at the same partitions? Which partition is it that you're looking at? The most reliable way I would recommend viewing partition free space is opening up a terminal and typing: 
```
df -h --total
```
If you have everything on your root partition, for example, you could be viewing your /var and / partitions and see two different sizes/capacities.

The drive I am looking at is sdb6

```
rob@rob-desktop:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sdb1              29G  6.1G   21G  23% /
varrun                1.8G  248K  1.8G   1% /var/run
udev                  1.8G  2.9M  1.8G   1% /dev
tmpfs                 1.8G  232K  1.8G   1% /dev/shm
/dev/sdb2              30G   25G  3.9G  87% /home
/dev/sdc1             233G   28G  206G  12% /media/mydocs
/dev/sdb6             300G  184G  116G  62% /media/video
/dev/sdb5             103G   66G   37G  65% /media/g

```

the total argument was rejected and it is not in the Man.

Assuming df is more accurate, it is showing 184 used instead of what Disk Usage Analyser reports as 73GB. Do you have a suggestion as to how to find out what is making up the 184?

---

### Post by michy99 on 2009-08-09
You might find some answers here:

[http://help.ubuntu.com/community/RecoverLostDiskSpace](http://help.ubuntu.com/community/RecoverLostDiskSpace)

---

### Post by blueridgedog on 2009-08-09
5% of the drive is reserved for root so the system can be operated/repaired in a disk full situation and this percentage is not shown in the amount used, but is factored in the amount available.

---

### Post by Robbyx on 2009-08-09
I have noticed that none of the file managers I use show the true total of the contents of a folder. This is the reason I am finding it hard to trace the cause of the difference. I use PCman in preference, Nautilus and Thunar if PCman does not help.

Is there a way of changing my file managers so they show the true amount of space taken up by a folder and its sub folders and files?

---

