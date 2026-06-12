---
title: "How do you use bzip2? it's not working"
date: 2012-01-06
forum: General Help
---

### Post by davethewave83 on 2012-01-06
I've googled around and can't find any decent examples of how I would sudo bzip2 my flash drive /media/flash to /home/david/Desktop/flash.bz2

I tried sudo bzip2 -crpv /media/flash > /home/david/Desktop/flash.bz2 but it says invalid flags for recursive, permissions etc

if you can give an example I'd appreciate it.

---

### Post by ajgreeny on 2012-01-06
I think you will need to burrow down one more step in the file system, as you will not be able to add the /media/flash folder to the bzip archive.

I also wonder why you have used **sudo**?  The files on most flash drives (fat32) will be owned by the current user so sudo should not be needed.

---

### Post by coffeecat on 2012-01-06
+1 on not using sudo, unless your flash drive is formatted with a Linux filesystem and your files are owned by root. If you use sudo, your flash.bz2 file will end up being owned by root.

Assuming you have a number of files and folders in /media/flash and you want to archive them recursively, you can bzip them with tar:

```

tar -cjvf /home/david/Desktop/flash.bz2 /media/flash
```

---

### Post by davethewave83 on 2012-01-06
> **ajgreeny said:**
> I think you will need to burrow down one more step in the file system, as you will not be able to add the /media/flash folder to the bzip archive.

I also wonder why you have used **sudo**?  The files on most flash drives (fat32) will be owned by the current user so sudo should not be needed.

Ah thanks, I don't know. I'm still learning :P I've been breaking and repairing linux repeatedly, customizing, breaking and fixing to learn. I don't learn well by reading so much as hands-on experience and help from others, so I appreciate the tips. 

my flash drive is a ext4 bootable ubunut installation though, with noatime to speed things up and lessen the writes, I thought about disabling journaling but I'd rather have the extra stability. That's why I have to use sudo and also why I'd like to maintain permissions, is because it is a bootable ubuntu ext4 drive

---

