---
title: "Sharing Data between Winxp &amp; Ubuntu"
date: 2009-09-07
forum: General Help
---

### Post by sandman3838 on 2009-09-07
Hello

I have this program that I would like to use in both Winxp and Ubuntu.  The setup for the program suggests:

QUOTE:
Second Step: choose a place to store shared datas !
we need a a place (a partition) which both operation systems can see it and can write to it .
I suggest a FAT32 partition .
(well you can choose a linux partition too but you have to install some extra programs to make windows see your linux partitions) so let say we choose a FAT32 partition , the partition should be mounted in linux with read write permission.

My question is, if Linux and Winxp can both see NTFS why would I be using FAT32?

Also, if it comes down to it and I really do need a FAT32 Partition, is there an easy way to setup this with the needed read write permissions?

Thank you all for your help!

---

### Post by MTGap on 2009-09-07
Uh it be helpful to mention what program your using, but yeah NTFS should work well.

Is this between two different computers or just a dual boot? Just make a NTFS partition and save your files that you want to share there.

---

### Post by c9-3Rr0r on 2009-09-07
You don't need any program for that. Just make a fat32 or ntfs partition (i sugest you to use fat32 because sometimes there are some freaks with ntfs under linux thats i heard never happend to me), windows will see it by default. Under Ubuntu you will need to mount it with read write permission
```

sudo mount -o rw /dev/[you're partition] [place to mount eg. ~/share]

```

---

### Post by Windows Nerd on 2009-09-07
> **sandman3838 said:**
> My question is, if Linux and Winxp can both see NTFS why would I be using FAT32?

Also, if it comes down to it and I really do need a FAT32 Partition, is there an easy way to setup this with the needed read write permissions?

Thank you all for your help!
Linux and Windows can both read NFTS. It probably recommends Fat32 because:

-The program is outdated. 
-Fat32 may be more reliable with Linux, though that is my guess.

Most of the time you have read write permissions to the drive if your account is the default one and can elevate their privileges temporarily.

Scott

---

### Post by cariboo on 2009-09-07
The problem with fat32 is the 4Gb file size limit. I would go with NTFS.

---

### Post by sandman3838 on 2010-01-02
I went with the NTFS.  So far so good.

---

