---
title: "Need help to format external drive"
date: 2010-06-08
forum: General Help
---

### Post by germanix on 2010-06-08
I have an 500GB Iomega external drive connected to my iMac and used for the Mac Time Machine back-ups. I want to put a small partition on there that I can use to back-up my Ubuntu files which are on my laptop. I thought that I would be able to just copy the entire Home file on Ubuntu to this drive be drag and drop but this does not work. I get a notice to inform me that I do not have permission to create file there. I can however move files in the other direction (from the external drive to Ubuntu on the laptop. I assume this is because the external drive was formatted for Mac and I hope the problem will be solved if I could format a part of the drive in ext4 to accommodate the linux files. 
Problem is I am not to sure how to go about doing this, so some advice on how I should at best proceed will be appreciated.
Thank you

---

### Post by Backharlow on 2010-06-08
There are 3 filesytem formats OSX can use HFS, HFS+ and fat32. Fat32 is a messy, limited format but it is universal for usb stick drives. HFS is the main format. HFS+ is the main Mac format with journaling enabled. OSX likes you to use HFS+ for everything. I disable the journal for disks that I use for video editing, because the journal creates overhead. You can enable and disable the journal for any disk in Disk Utility, and doing so won't mess with you. Now, Ubuntu accesses Mac HFS(+) partitions using Fuze. Unfortunately, if the journal is enabled i.e. HFS+ Ubuntu can only read from the disk. So it is read-only. That is why you can copy from it but not to it. If there is no journal, (never existed or disabled), meaning it is just HFS, then Ubuntu can both read and write to it.

---

### Post by unmole on 2010-06-08
The reason you don't have write access is because you are not the owner. Do a 
```
 sudo chown -R username:username /path/to/external/partion
```

---

### Post by germanix on 2010-06-08
Hi Backharlow, thank you for this explanation. I have now checked the external drive and saw that it is actually formatted as FAT32. How does this change the situation?

Unmole, I tried your method any which way I could think but was not able to get it right. probably my own stupidness but I either could not get the path right or something else. Whatever path/method I used I always get "no such file or directory" I thank you for your help though.

---

### Post by yetiman64 on 2010-06-08
Hi germanix, To see where and how you're external fat32 formatted drive is being mounted try the command in terminal,
```
cat /etc/mtab | grep vfat
```

---

### Post by germanix on 2010-06-08
Thank you yetiman64, that helped to point me in the right direction. Now I can try the rest. If all else fails I guess I will just go and get one of these "memory stick pro duo`s" for my Sony laptop and use that for back-up of my files.
Thank you all once again for your help.

---

### Post by Backharlow on 2010-06-08
Wait... is the external drive plugged into the ubuntu machine directly, or is it plugged into the mac and being shared over a network?

---

### Post by germanix on 2010-06-08
It is directly plugged into the laptop when I try to do back-ups

---

