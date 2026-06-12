---
title: "File Recovery After Partition and Linux Install"
date: 2010-02-24
forum: General Help
---

### Post by DanPiazza on 2010-02-24
Hi, I'm really new to Linux, so please forgive my ignorance.

I recently wiped my laptop clean of its Windows installation and installed Karmic Koala 9.10.

My problem is that when I transferred the files I wanted to keep to my external HD, I forgot my pictures folder.

My friend told me I could use something called Photorec to still recover these files from my HD, but I don't want to mess around if I don't know what I'm doing.

Any advice? Thanks!

---

### Post by darolu on 2010-02-24
These links may help you:

[https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery)
[http://www.xs4all.nl/~carlo17/howto/undelete_ext3.html](http://www.xs4all.nl/~carlo17/howto/undelete_ext3.html)

Don't be too optimistic though, it is quite possible that you won't be able to recover those files, if any files (from installation or generated after install) got written over HD sectors were your files used to be, they are lost for good.

---

### Post by DanPiazza on 2010-02-24
> **darolu said:**
> These links may help you:

[https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery)
[http://www.xs4all.nl/~carlo17/howto/undelete_ext3.html](http://www.xs4all.nl/~carlo17/howto/undelete_ext3.html)

Don't be too optimistic though, it is quite possible that you won't be able to recover those files, if any files (from installation or generated after install) got written over HD sectors were your files used to be, they are lost for good.

Thanks for the link. I had your opinion too, but my friend seems optimistic that i really didn't do enough to delete it for good. He said that unless I used a program that deletes a file on a certain level, it can usually be recovered. He's the IT director for an entire school too, so I'm hoping he knows what he's talking about.

---

### Post by Mark Phelps on 2010-02-24
> **DanPiazza said:**
> He said that unless I used a program that deletes a file on a certain level, it can usually be recovered.

Guess that depends on how you define "usually" ...

The program your IT Director was most probably referring to was one of a myriad of apps that really "wipe" the drive -- by overwriting it with zeroes and ones.  When that is done, SW used to recover files simply won't work anymore.

Given the right hardware (read that, law enforcement ...) files can still be recovered to some extent based on latent, trace magnetism present on the drive.  

You can have much the same done if you send the physical drive to a data recovery service and pay them a fortune.

But, in the world of PCs, erasing files, or erasing partitions, makes the previously allocated space available for reuse.  Once that space is reused, SW is not going to be able to recover the original data.

---

### Post by DanPiazza on 2010-02-24
> **Mark Phelps said:**
> Guess that depends on how you define "usually" ...

The program your IT Director was most probably referring to was one of a myriad of apps that really "wipe" the drive -- by overwriting it with zeroes and ones.  When that is done, SW used to recover files simply won't work anymore.

Given the right hardware (read that, law enforcement ...) files can still be recovered to some extent based on latent, trace magnetism present on the drive.  

You can have much the same done if you send the physical drive to a data recovery service and pay them a fortune.

But, in the world of PCs, erasing files, or erasing partitions, makes the previously allocated space available for reuse.  Once that space is reused, SW is not going to be able to recover the original data.

Thanks for the response. I guess I'll give these ideas a shot, but I wont have my hopes up. The good news is that the data isn't crucial, but it would be nice to have back.

---

### Post by pmorton on 2010-02-24
You've overwritten your hard drive, so the chances of significant recovery are really pretty slim. You could try the foremost file recovery utility on the drive. I've found it a lifesaver in other circumstances.

First, make a binary copy of the partition to work on, rather than the drive itself, writing it to an external drive at least as big as the partition you're copying. If you have more than one partition, make a copy of each.

For example, supposing your root partition is /dev/sda1 and your external drive is mounted as say /media/MyExtUSBdrive.

```
dd if=/dev/sda1 bs=4096 of=/media/MyExtUSBdrive/backup.file 
```

Then install foremost:

```
sudo apt-get install foremost
```

```
man foremost
```

will give you the usage. Foremost will recover a good range of well-known file types. I assume you'll want the '-t jpg' option for your photos. You'd best save the output onto a directory in your external drive, in case you want to try something else on your actual drive without making matters worse. 

I have my doubts about how many, if any, of the photos you'll get back this way.  Data carvers like Foremost are at their most successful if you've only just deleted some files and powered down the drive immediately before it gets spattered with new data.  The Ext2 file system was more forgiving, but Ext3 (I don't know about Ext4) takes no prisoners for mistakes of that kind. Believe me, I've made them - delete means delete. The golden rule in Linux is to always have a backup (no different from Windows, really, which has it's own - arguably considerably worse - vulnerabilities, that aren't  in your control).

I have a bit of a beef in this department with distros like Ubuntu which purport to be suitable for newbies and Windows converts. I can't imagine it would too difficult  to give you the option of being asked to confirm before being allowed to delete certain directory trees, or is that too nannyish?

---

### Post by DanPiazza on 2010-02-25
> **pmorton said:**
> You've overwritten your hard drive, so the chances of significant recovery are really pretty slim. You could try the foremost file recovery utility on the drive. I've found it a lifesaver in other circumstances.

First, make a binary copy of the partition to work on, rather than the drive itself, writing it to an external drive at least as big as the partition you're copying. If you have more than one partition, make a copy of each.

For example, supposing your root partition is /dev/sda1 and your external drive is mounted as say /media/MyExtUSBdrive.

```
dd if=/dev/sda1 bs=4096 of=/media/MyExtUSBdrive/backup.file 
```

Then install foremost:

```
sudo apt-get install foremost
```

```
man foremost
```

will give you the usage. Foremost will recover a good range of well-known file types. I assume you'll want the '-t jpg' option for your photos. You'd best save the output onto a directory in your external drive, in case you want to try something else on your actual drive without making matters worse. 

I have my doubts about how many, if any, of the photos you'll get back this way.  Data carvers like Foremost are at their most successful if you've only just deleted some files and powered down the drive immediately before it gets spattered with new data.  The Ext2 file system was more forgiving, but Ext3 (I don't know about Ext4) takes no prisoners for mistakes of that kind. Believe me, I've made them - delete means delete. The golden rule in Linux is to always have a backup (no different from Windows, really, which has it's own - arguably considerably worse - vulnerabilities, that aren't  in your control).

I have a bit of a beef in this department with distros like Ubuntu which purport to be suitable for newbies and Windows converts. I can't imagine it would too difficult  to give you the option of being asked to confirm before being allowed to delete certain directory trees, or is that too nannyish?

Thanks for the detailed response. I'm not too bad with computers, but I'm terrible with Linux. Could you please explain to me creating a binary copy? Other than that I should be able to follow this just fine. Luckily I got all my important files when I partitioned my computer, it's just disappointing to lose some pictures that only I had.

---

### Post by rbc on 2010-02-25
The dd command that pmorton suggested will create the binary/bit-for-bit copy. In other words, it goes through every 0 and 1 on the partition, and using the example pmorton gave, writes it to one big file called backup.file. pmorton further suggests (correctly so) running foremost against the backup.file instead of the partition itself, thereby reducing the risk of further damage

---

### Post by DanPiazza on 2010-02-25
> **rbc said:**
> The dd command that pmorton suggested will create the binary/bit-for-bit copy. In other words, it goes through every 0 and 1 on the partition, and using the example pmorton gave, writes it to one big file called backup.file. pmorton further suggests (correctly so) running foremost against the backup.file instead of the partition itself, thereby reducing the risk of further damage

Unfortunately I don't have an external available for a few days. How quickly do I need to do this before my data is even more likely to be missing forever?

---

### Post by rbc on 2010-02-26
If it were me, I wouldn't be using the hard drive at all, but that's your call

---

