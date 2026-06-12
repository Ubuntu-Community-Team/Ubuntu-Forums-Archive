---
title: "more fat32 partitions"
date: 2006-03-04
forum: General Help
---

### Post by vatch23 on 2006-03-04
Hi, Ihave 3 harddrives in my pc, the first with Kubuntu is  linuxpartitioned ofcourse.
The second and the third aare fat32 partitions.
I have added them in fstab and they are recognized and well, but I can only write to the second one, why???
fstab read :# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdd        /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
/dev/hdb1       /home/vatch23/80g vfat  umask=000  0  0
/dev/hdd1     /home/vatch23/40g vfat  umask=000 0 0

Since I switch cables between the two cd players or the third harddrive (hdd1), they are both in there.
Please help me, so I can write to hdb1 too.
greetings

---

### Post by incubus on 2006-03-04
Have you tried connecting only your main hard drive and the problematic one?

Also, can you write using sudo?

incubus

---

### Post by vatch23 on 2006-03-04
No icannot write to it even if i disconnect the other one, and no I cannot sudo cp anything to it : read-only filesystem i am told by the terminal.

---

### Post by Jucato on 2006-03-04
probably because you have 2 /dev/hdd entries in the fstab
- /dev/hdd , which is the cd/dvd drive
- /dev/hdd1,  which you are setting to be the 3rd hard disk.

---

### Post by vatch23 on 2006-03-04
Yes, thats what i was thinking too, but how can i change this then since i only have two ide connectord and 'sometimes' wants to use my cd instaed of the harddrive

---

### Post by Jucato on 2006-03-04
Hmm... that is tricky. I'm not really sure how to set fstab so that it automatically detects whether /hdd is a hard drive or a cd drive.

I guess the best way is to probably have both lines in your fstab, and comment out one or the other before restarting your system, depending on what you will be mounting on your next boot.

---

### Post by vatch23 on 2006-03-04
well, i have lready tried these options and no matter what i caal it , actually now i,ve switched so the one my systems see,s as read-only is called hdb1, and the other one hde1, but it doesnt matter I cant write to it.

---

### Post by Jucato on 2006-03-04
Hmm... I'm a bit stumped, too. I'm also not sure if Linux recognizes a "hde". Can you check who is the owner of the FAT32 drives? For reference, this is the entry for one of my own FAT32 partitions
```
/dev/hdb6       /media/shared     vfat    defaults,uid=1000,gid=1000        0       0
```

Btw, maybe you would receive better help if you posted this in the Absolute Beginner Talk section, since it's a general Linux concern. I'm just not sure about the rules in posting the same topic in 2 places.

---

### Post by vatch23 on 2006-03-04
OK, I let this thread here and maybe someone else  knows, .
Now i,ve added rw to it in fstab and now I CAN write to it ,but now QParted says that 34 of the 80 gigs are used.
Also when i click on properties I am the owner but it also says that 34 gigs are used, 
Thats not true it is empty,though.
Stranger and stranger

---

### Post by incubus on 2006-03-04
I don't have much experience with FAT32 (actually just bad memories), but here's one reply that I posted to someone who also had a wrong-size problem.

[http://www.ubuntuforums.org/showthread.php?t=138292&highlight=fat32]("http://www.ubuntuforums.org/showthread.php?t=138292&highlight=fat32")

I don't know if those rules really apply in this case. Do you really need to use FAT32 in both HDs? I rarely use windows, but when I have to I use a program that reads reiserfs.

[http://p-nand-q.com/download/rfstool.html]("http://p-nand-q.com/download/rfstool.html")
[http://yareg.akucom.de/]("http://yareg.akucom.de/")

incubus

---

### Post by Jucato on 2006-03-04
Oh I completely missed that. FAT32 is limited to 32GB sizes only. anything higher than that has to be NTFS (eeek). At least, that's how it works under Windows, and they're the ones who made these. :D

---

### Post by incubus on 2006-03-04
Yep. And if that's correct, since hard drive size is getting cheaper, we're gonna see more and more of this problem.

I really wish we had something for windows that would fully read/write ext3 or reiserfs (I'm not a big fan of trying to implement writing NTFS, because it's proprietary).

Never tried this, but here's another one:
[http://rfsd.sourceforge.net/]("http://rfsd.sourceforge.net/")

incubus

EDIT: This one is new to me, I gotta give it a try. Seems to be very promising.
[http://www.fs-driver.org/]("http://www.fs-driver.org/")

---

### Post by incubus on 2006-03-04
vatch23,
Back to your issue, have you tried:
[http://www.ubuntuforums.org/showthread.php?t=139535]("http://www.ubuntuforums.org/showthread.php?t=139535")

incubus

---

