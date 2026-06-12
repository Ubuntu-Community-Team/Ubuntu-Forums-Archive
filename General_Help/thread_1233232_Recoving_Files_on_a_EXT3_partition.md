---
title: "Recoving Files on a EXT3 partition"
date: 2009-08-06
forum: General Help
---

### Post by Teutorix on 2009-08-06
I recently reinstalled windows and now i cannot access ubuntu in anyway, ive tried a few ext readers but to no avail.

So if you can help me to get my files or to access ubuntu again it would be much appreciated.

I think the problem is that installing windows changed my bootloader ( or whatever that GRUB thing is) to a microsoft one. I dont think my live cd can read my partition table either.

---

### Post by ajgreeny on 2009-08-06
I hope you didn't install windows over your ubuntu install!  Assuming you did not do that, you can get your grub back easily with the live CD.
[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

---

### Post by Teutorix on 2009-08-06
Oh poop thats what i did.

---

### Post by michy99 on 2009-08-06
Before you decide that Ubuntu is gone, boot a live cd and run this command in a terminal and post the result here:```
sudo fdisk -l
```

---

### Post by bronkeydain on 2009-08-06
If it is really important data you can probably try some raw recovery tools to recover the files you have not overwritten. These tools should be able to recover these files but often you lose the path and filename information (at least on FAT and NTFS). That is a bit of a problem if you have thousands of photo's for instance. It would give you a directory called JPG with inside file00001.jpg, file00002.jpg etc...

---

### Post by Teutorix on 2009-08-06
wait i still have the ubuntu partition intact if thats what  you mean

---

### Post by michy99 on 2009-08-06
In that case, follow the instructions on this page:

[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

---

### Post by Teutorix on 2009-08-06
False alarm

---

