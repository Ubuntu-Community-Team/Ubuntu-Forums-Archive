---
title: "Partition problem at install"
date: 2006-02-01
forum: General Help
---

### Post by meono on 2006-02-01
hi,

I am trying to install Ubuntu 5.10 to my laptop. I have 3 partitions, NTFS for winxp, FAT for both ubuntu and winxp, and Reiser partitions for ubuntu. 

actually I have ubuntu installed, but I need to get rid of it and install Ubuntu 5.10.

My problem is, during install, I can't see any of these partitions, in the "manually manage partitions" option.  I just see a 40GB hdd.

So, if someone know what the problem is or the solution(I prefer this one :))
it will help a lot...

---

### Post by Herman on 2006-02-01
> My problem is, during install, I can't see any of these partitions, in the "manually manage partitions" option. I just see a 40GB hdd. So after the Ubuntu Installer gets started and detects all your hardware and starts up the partitioner, you click 'manually edit partition table. Then you find that the Ubuntu partitioner is not able to read your partition table?
This could be a bad sign. Back up all you data!

What partitioner did you use to create the partition table?

Have you tried looking at your partitions with another partitioner like GParted or QTParted or some other kind to see what they say is there?

It also just could be a faulty .iso download, a scratch or smear on your install CD, or a poor quality burn. I recently had some experiences with bad CDs myself and I found out they can cause all kinds of unpredictable install problems things to occur. I had one that recognised my CD-ROM drive as a partitionable device as if it were another hard disk! It may have been caused by a scratch on the CD-ROM disk. It had me really puzzled for a while until I found the scratch and burned a new install disk. (Lol) :-D (Herman)

---

### Post by meono on 2006-02-02
I just burn another cd for ubuntu, and nothing changed.

Also I used Gparted and QTparted; neither showed anything about partitions, they just see a 40GB hda...

So, is there anyway I can fix partition table?

---

### Post by lamego on 2006-02-02
Are you sure you didn't deleted your partitions by accident ?
From the command line try: 
  sudo fdisk -l

If there are no partitions listed I guess you have deleted them...

There is a linux program which will try to guess deleted partitions, I am not sure it is included on the live CD:
The url for it is:
  [http://www.stud.uni-hannover.de/user/76201/gpart/](http://www.stud.uni-hannover.de/user/76201/gpart/)

---

### Post by meono on 2006-02-02
ok, this is what i get from "fdist -l"

Disk /dev/hda: 40.0 GB, 40007761920 bytes
16 heads, 63 sectors/track, 77520 cylinders
Units = cylinders of 1008 * 512 = 516096 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1       36870    18582448+   7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/hda2           36880       62070    12696075    b  W95 FAT32
Partition 2 does not end on cylinder boundary.
/dev/hda3           62061       64005      979965   82  Linux swap / Solaris
Partition 3 does not end on cylinder boundary.
/dev/hda4           64006       77520     6811560    5  Extended
Partition 4 does not end on cylinder boundary.
/dev/hda5           64006       69823     2931831   83  Linux
/dev/hda6           69823       72723     1461883+  83  Linux
/dev/hda7           72723       77520     2417751   83  Linux


there is an overlap in swap partition, and that is a problem i guess

---

### Post by meono on 2006-02-02
by the way, thank everyone for help...

I just reinstalled ubuntu, somebody helped me to remove the problem partition by fdisk during install, and now i am using the brand new ubuntu

thank again

---

### Post by Herman on 2006-02-02
> I just reinstalled ubuntu, somebody helped me to remove the problem partition by fdisk during install, and now i am using the brand new ubuntu
I'm glad everything turned out okay, I was worried about it but didn't know the solution. Thank you for letting us all know the problem is solved, it makes everyone feel better, and not only that, but *how* you solved it is very important as well. Thanks for sharing the information. It might help others in the future.
 You are a good Ubuntuist! :-D (Herman)

---

