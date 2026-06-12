---
title: "mount windows drive"
date: 2010-05-22
forum: General Help
---

### Post by FM101 on 2010-05-22
Hello,
I am trying to see my windows drive from ubuntu.
I found this article:

[http://www.reallylinux.com/docs/toptip3.shtml](http://www.reallylinux.com/docs/toptip3.shtml)

However when I run
root@ubuntu:/home/laptop# mount -t vfat /dev/hda1 /mnt/win

I get this.
mount: special device /dev/hda1 does not exist

Is there something else I have to do?

Is there a better way of doing this?

thanks

---

### Post by spiky001 on 2010-05-22
If you go into places network is it listed in the side panel?

---

### Post by FM101 on 2010-05-22
How do you get to network on 10.04?

---

### Post by oldfred on 2010-05-22
IF you run 
```
sudo fdisk -l
```

You will see the drives are sda1, sda2 etc. They used to be hda for IDE and sda for SCSI (not sure about early SATA) but several years ago they consolidated the driver and all hard drives in Ubuntu are sda etc.

If you want to permanently mount it, you can add an entry to fstab,

Understanding fstab
[http://ubuntuforums.org/showthread.php?t=283131](http://ubuntuforums.org/showthread.php?t=283131)
Ownership and permissions of vfat / ntfs are set at the time of mounting. This is often a source of confusion.

[https://help.ubuntu.com/community/Mount/](https://help.ubuntu.com/community/Mount/)

---

### Post by spiky001 on 2010-05-22
top left inbetween Applications and Systems then go down to Network it should list your win drive in left side panel

---

### Post by FM101 on 2010-05-22
Thanks all
Got it to work.  not really sure how.
I installed mount manager and storage device manager.

---

