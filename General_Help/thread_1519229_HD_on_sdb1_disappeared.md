---
title: "HD on sdb1 disappeared?"
date: 2010-06-27
forum: General Help
---

### Post by revered on 2010-06-27
I am using Ubuntu 10.04 on a primary HD an I have a secondary HD connected too, this second this gets recognized by ubuntu on sdb1 and if I click it on the places menu it gets mounted to /media/somefolder, on fdisk -l I see both HDs with their partitions.

I am trying to use that second HD for a virtual machine, but when I try to do something with sdb1 like creating a .vmdk out of it, most of the times sdb1 disappear, fdisk -l doesn't show any other hd than the main, anyone knows what could he causing this?

My /etc/fstab doesn't show anything for the secondary hd, only for /proc, /swap and /ext4, the secondary is ntfs.

---

### Post by dcstar on 2010-06-28
> **revered said:**
> I am using Ubuntu 10.04 on a primary HD an I have a secondary HD connected too, this second this gets recognized by ubuntu on sdb1 and if I click it on the places menu it gets mounted to /media/somefolder, on fdisk -l I see both HDs with their partitions.

I am trying to use that second HD for a virtual machine, but when I try to do something with sdb1 like creating a .vmdk out of it, most of the times sdb1 disappear, fdisk -l doesn't show any other hd than the main, anyone knows what could he causing this?

My /etc/fstab doesn't show anything for the secondary hd, only for /proc, /swap and /ext4, **the secondary is ntfs**.

You **cannot** use non-Linux filesystems for things that require full Linux filesystem support.

Format it as a Linux filesystem and things will probably work correctly.

---

