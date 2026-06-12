---
title: "ubuntu 10.04 installer not recognizing windows 7 partition"
date: 2010-06-10
forum: General Help
---

### Post by mevich on 2010-06-10
Hello,

I've previously installed ubuntu using wubi. But this is the first time I've tried installing it directly on the hard drive. I bought a new 320 gig hard disk and divided into 3 partitions of 50gig for windows 7, 30 gig for ubuntu and and the remaining for data. I installed windows 7 on the 50 gig partition. When I tried to install ubuntu using usb boot device, it says no operating system found and all my hard disk is muddled up and I can't see my partitions.

Now I go into live cd mode and see if I can mount my partitions and there I can see all the partitions. I formatted the 30 gig partition which was previously in NTFS to FAT32 and tried to install ubuntu directly from the live cd into the 30gig partition. But still the installer cannot see either my partitions nor my windows 7.

As of now I'm using VMplayer and running ubuntu on a virtual machine. But would really prefer to have it installed on the hard drive to derive its full power. Can anyone please help.

---

### Post by dcstar on 2010-06-10
> **mevich said:**
> Hello,

I've previously installed ubuntu using wubi. But this is the first time I've tried installing it directly on the hard drive. I bought a new 320 gig hard disk and divided into 3 partitions of 50gig for windows 7, 30 gig for ubuntu and and the remaining for data. I installed windows 7 on the 50 gig partition. When I tried to install ubuntu using usb boot device, it says no operating system found and all my hard disk is muddled up and I can't see my partitions.

Now I go into live cd mode and see if I can mount my partitions and there I can see all the partitions. I formatted the 30 gig partition which was previously in NTFS to FAT32 and tried to install ubuntu directly from the live cd into the 30gig partition. But still the installer cannot see either my partitions nor my windows 7.

As of now I'm using VMplayer and running ubuntu on a virtual machine. But would really prefer to have it installed on the hard drive to derive its full power. Can anyone please help.

Ubuntu does **not** install into Windows partitions, it installs into free space on a disk and tries to create free space if it does not exist.

Read one of the many installation HOWTOs.

---

### Post by mevich on 2010-06-10
Hello David,

Thanks for the reply. 

I've seen the tutorials to install ubuntu. In every one of them when windows 7 is installed it shows in the ubuntu installer. In my case it doesn't. Should I be worried about this?

Vikram.

---

