---
title: "help everything appears in 2s"
date: 2010-04-16
forum: General Help
---

### Post by elliotn on 2010-04-16
hey guys when i go to computer folder in my ubuntu i noticed that every drive appears twice, i got a 20 gig with windows 7, and a 160gig which was partition to 140 and the 20gig has ubuntu, but now all appear twice. What should i do to fix it

---

### Post by 2hot6ft2 on 2010-04-16
Unless you labeled the partitions it's showing each partition as the drive so clicking on one will open that partition and clicking on the other will open the other partition.
I labeled mine in GParted to tell which is which
System > Administration > GParted
select a partition and right click then select Label and label them
Here's mine with 3 partitions which are labeled. It's just 1 500 GB Hard Drive. If they weren't labeled it would just say 500 GB Hard Disk 3 times

P.S. You can't label them while they're mounted so it's best done from the livecd.

---

### Post by dtmbmw325i on 2010-04-16
I think what he may mean is the same problem I am trying to solve myself.  I have 3 hard drives, all labled (as you said), mounting with fstab.  The issue on my box seems that it mounts those drives fine but also shows them a second time like they are trying to be auto mounted like a usb drive.  With the icon set I use it shows one like an internal drive and the duplicated like a usb drive.  When you click on the duplicate drives they say they cannot be mounted because they are already mounted or in use... something to that affect.

I hope these are the same issues because they are really annoying.

---

### Post by elliotn on 2010-04-22
> **dtmbmw325i said:**
> I think what he may mean is the same problem I am trying to solve myself.  I have 3 hard drives, all labled (as you said), mounting with fstab.  The issue on my box seems that it mounts those drives fine but also shows them a second time like they are trying to be auto mounted like a usb drive.  With the icon set I use it shows one like an internal drive and the duplicated like a usb drive.  When you click on the duplicate drives they say they cannot be mounted because they are already mounted or in use... something to that affect.

I hope these are the same issues because they are really annoying.

yes thats  what i mean

---

### Post by john newbuntu on 2010-04-22
In this post, towards the end, you will find people suggesting unmounting and remounting the drives or perhaps even changing the UUID to the device name in /etc/fstab.  Wanna give it a shot?
\[http://ubuntuforums.org/archive/index.php/t-1375644.html](http://ubuntuforums.org/archive/index.php/t-1375644.html)

---

### Post by DawieS on 2010-04-22
If you are using 3 or more drives with a mixture of file systems (including NTFS), you are likely to run into mounting/unmounting problems with Karmic. For a solution that works with multiple drives/partitions, please see[_** this**_]("http://ubuntuforums.org/showthread.php?t=1429790") thread.

By the way, these problems have disappeared with Lucid. I am currently using 5 drives with multiple partitions, and have found 10.04beta2 requires no user intervention to correctly mount/unmount any drives/partitions.:smile::smile::smile:

---

### Post by dtmbmw325i on 2010-04-22
> **DawieS said:**
> If you are using 3 or more drives with a mixture of file systems (including NTFS), you are likely to run into mounting/unmounting problems with Karmic. For a solution that works with multiple drives/partitions, please see[_** this**_]("http://ubuntuforums.org/showthread.php?t=1429790") thread.

By the way, these problems have disappeared with Lucid. I am currently using 5 drives with multiple partitions, and have found 10.04beta2 requires no user intervention to correctly mount/unmount any drives/partitions.:smile::smile::smile:

I see in that one post you were going to look at how shares are handled.  I run a personal ftp server and also share files on my home network. I  was wondering what would happen when I try to attach to the share, before the icon was clicked to auto mount the file system.  I did remove everything from Fstab and the duplicates were gone.  I figure this thread can be committed as solved from my perspective but please do answer my questions if you figure something out.  Thank you much.

EDIT: I tried connecting to my ftp after I rebooted and I can not get to my share.  I am also curious if my backups (using simple backup) are also affected by this.

EDIT2: Everything is affected that uses the drive.

---

