---
title: "testdisk and recovering a lost partition"
date: 2010-04-29
forum: General Help
---

### Post by Homayoon on 2010-04-29
I'm not sure exactly how, but somehow one of my partitions was corrupted yesterday (GParted showed it as unallocated space). I tried using testdisk. It found the lost partition, so I happily let it rewrite the partition table.

The lost partition did return, but then I found out another partition has disappeared (the one most important to me) and in its place there is an empty NTFS partition and an empty ext3 one (the original was an ext4, the two new partitions seem to be those that were merged to form the ext4 partition). I tried testdisk again. When I run "testdisk /dev/sda" and choose "Analyse" the incorrect partition table is detected.

I tried running "testdisk /dev/sda5" (sda5 is the NTFS partition) and it finds a partition labeled "magic" which is the name of the lost partion but testdisk cannot recover it. I get this:

```

TestDisk 6.11, Data Recovery Utility, April 2009
Christophe GRENIER <grenier@cgsecurity.org>
http://www.cgsecurity.org

Disk /dev/sda5 - 47 GB / 44 GiB - CHS 5823 255 63

The harddisk (47 GB / 44 GiB) seems too small! (< 75 GB / 70 GiB)
Check the harddisk size: HD jumpers settings, BIOS detection...

The following partition can't be recovered:
     Partition               Start        End    Size in sectors
  Linux                    0   1  1  9137 234 56  146800640 [magic]










[ Continue ]
EXT4 Large file Sparse superblock, 75 GB / 70 GiB



```

I tried deleting the second partition and moving the one after it so that there is 75GB available but it didn't help. Does anyone have a suggestion as to how I can fix this. I have lost worth of a year of my work. The worst thing that could ever happen to me!

---

### Post by dino99 on 2010-04-29
it's the hard reallity when user dont make regular backup, now you will know what to do if your work have any value for you.

Recovering is not an easy task and never tell if we can succeed. As you seem to have already the good tools, i only suggest partedmagic and hope the best to you.

---

### Post by bumanie on 2010-04-29
You may have to try photorec to recover from the raw hard drive - but it will recover any deleted and not over-written files. So you will then have a lot of sorting to do. Despite its name, photorec recovers 100+ different file types, so you can choose what file type you want it to look for, that reduces the amount you have to sort through. Photorec is part of the testdisk package - read cgsecurity website for details. There is also a recovery program called magic rescue -it may work. Also as it is ntfs you are worried about there is a program called recuva that deals with ntfs data loss.

---

### Post by Homayoon on 2010-04-29
Thanks for your replies. A friend of mine just suggested using a recovery disk he had (it was called the Ultimate Boot Disc, if I'm not mistaken). Among the tools it had was testdisk and without much hope I decided to give it a go for another time. It detected a list of partitions among which was the one I was hoping to recover. So after some sorting out, I finally got my data back. You can't imagine how relieved I am.

And about making backups, yes, I've heard of those! I swear I'm going to make backups from now on!

---

### Post by jason coale on 2010-10-17
> **Homayoon said:**
> Thanks for your replies. A friend of mine just suggested using a recovery disk he had (it was called the Ultimate Boot Disc, if I'm not mistaken). Among the tools it had was testdisk and without much hope I decided to give it a go for another time. It detected a list of partitions among which was the one I was hoping to recover. So after some sorting out, I finally got my data back. You can't imagine how relieved I am.

And about making backups, yes, I've heard of those! I swear I'm going to make backups from now on!

I too have 'the following partition can't be recovered' issue using testdisk. Can you elaborate on what you did when you used Testdisk again that fixed your issue? I'm in a live cd and can't boot into either of my 2 OS's on the drive- Win/Lose **7** or ubuntu lucid.




TestDisk 6.11, Data Recovery Utility, April 2009
Christophe GRENIER <grenier@cgsecurity.org>
[http://www.cgsecurity.org](http://www.cgsecurity.org)

Disk /dev/sda - 250 GB / 232 GiB - CHS 30402 255 63

The harddisk (250 GB / 232 GiB) seems too small! (< 263 GB / 245 GiB)
Check the harddisk size: HD jumpers settings, BIOS detection...

The following partition can't be recovered:
     Partition               Start        End    Size in sectors
  Linux                28346   0  1 31992 254 56   58589048










[ Continue ]
EXT4 Large file Sparse superblock Recover, 29 GB / 27 GiB

---

### Post by jcampen on 2010-10-31
I'm having the same problem, so we would appreciate it if you reciprocated the help and time many others gave to you and at least explain how you managed to recover the portions.

---

