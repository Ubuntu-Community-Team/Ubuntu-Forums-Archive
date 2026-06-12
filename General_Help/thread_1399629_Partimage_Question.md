---
title: "Partimage Question"
date: 2010-02-05
forum: General Help
---

### Post by Jae99 on 2010-02-05
I tried the following tutorial on how to backup my Ubuntu drive w

[https://help.ubuntu.com/community/DriveImaging](https://help.ubuntu.com/community/DriveImaging)

I installed partimage without issue but when I went to use it I cept getting the following error

     /dev/sda1 partition was mounted.
     Partition Image can't work on mounted
     partitions. Please unmount it before.
     You can do it with "umount /"

I'm not sure what to make of this. I only have one drive so how would I unmount it? Any help would be greatly appreciated.

---

### Post by dcstar on 2010-02-06
> **Jae99 said:**
> I tried the following tutorial on how to backup my Ubuntu drive w

[https://help.ubuntu.com/community/DriveImaging](https://help.ubuntu.com/community/DriveImaging)

I installed partimage without issue but when I went to use it I cept getting the following error

     /dev/sda1 partition was mounted.
     Partition Image can't work on mounted
     partitions. Please unmount it before.
     You can do it with "umount /"

I'm not sure what to make of this. I only have one drive so how would I unmount it? Any help would be greatly appreciated.

You cannot use that utility on a mounted partition, you have to boot up to another OS (on your system or a CD) to access that partition.

---

### Post by Jae99 on 2010-02-06
So could i run the ubuntu cd on the box and then execute partimage? Also thanks for the quick response.

---

