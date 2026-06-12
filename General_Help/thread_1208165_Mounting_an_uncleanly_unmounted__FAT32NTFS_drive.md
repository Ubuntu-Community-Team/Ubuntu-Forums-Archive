---
title: "Mounting an uncleanly unmounted  FAT32/NTFS drive"
date: 2009-07-08
forum: General Help
---

### Post by Hacker3141 on 2009-07-08
Hello everyone. I just have to ask a hypothetical question here. I am going to try and get some data off a computer tomorrow. The CD drive is fried, and the Windows install is corrupt/not working. I know the drive works and the partition is working because they can boot to Windows, but it immediately crashes. This is only for data recovery, I am not going to try and rescue the Windows install. I plan to do so using Ubuntu on a separate, internal hard drive. I need to mount the windows partition to retrieve the data. Normally, this would not be a problem. I do know that Ubuntu will not mount the partition if it is not cleanly unmounted. My question is, how would I go about mounting the drive if it was not cleanly unmounted? Thank you for all your help, I know that this has been a rather lengthy post.

---

### Post by merlinus on 2009-07-08
Assuming the partition is sdb1:

```

sudo mkdir /media/disk
sudo mount -t ntfs /dev/sdb1 /media/disk -o force
```might do it.

---

### Post by synapsys on 2009-07-08
```
sudo mount -t ntfs-3g /dev/sdb1 /media/disk -o force
```

---

### Post by merlinus on 2009-07-08
Thanks for correcting my error.

---

### Post by Hacker3141 on 2009-07-08
Thank you guys!

---

### Post by synapsys on 2009-07-08
> **merlinus said:**
> Thanks for correcting my error.

I'm sure you'd do the same for me ;)

---

