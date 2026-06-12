---
title: "Installed Grub on NTFS partition by error"
date: 2009-09-02
forum: General Help
---

### Post by intact on 2009-09-02
Hi,

I've just reinstalled ubuntu and by error i've choose to install grub on /sda4 that was a NTFS partition. Now i cant see any files in that partition. Ubuntu shows me as an unknown size NTFS partition, and windows shows as RAW partition when trying to run a chkdsk. 
The worst part, is that is my documents and music partition, almost 100 gb in pictures, music and documents...

How can I fix this?

Greets

---

### Post by intact on 2009-09-02
:(

---

### Post by ZaM0 on 2010-05-16
I've got exactly the same problem :(

---

### Post by koolblue3 on 2010-05-16
Hi,

Not sure if the OP needs help anymore, but have you tried mounting it manually? Try running: 
```

sudo mkdir /mnt/windows
sudo mount -t ntfs-3g /dev/sda4 /mnt/windows
ls /mnt/windows

```If you could, please post the output of "ls /mnt/windows" if the other commands ran successfully.

ZaMO these instructions should work for you just substitute /dev/sda4 with the location of your NTFS partition. To find it just run: ```
 sudo fdisk -l
```

---

