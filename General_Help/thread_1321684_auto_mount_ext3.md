---
title: "auto mount ext3"
date: 2009-11-10
forum: General Help
---

### Post by Steve60938 on 2009-11-10
i have a separate 40gb hd for my vmware image, I am giving this pc to someone else who i dont want to trouble explaning how to mount the disk everytime the pc comes up, I have seen alot of tutorials on auto mounting ntfs partitions\hd but none on a linux native file system

---

### Post by alphaniner on 2009-11-10
[How to fstab]("http://ubuntuforums.org/showthread.php?t=283131&highlight=fstab")

---

### Post by Steve60938 on 2009-11-10
thanks

---

### Post by hal8000 on 2009-11-10
> **Steve60938 said:**
> i have a separate 40gb hd for my vmware image, I am giving this pc to someone else who i dont want to trouble explaning how to mount the disk everytime the pc comes up, I have seen alot of tutorials on auto mounting ntfs partitions\hd but none on a linux native file system

All commands are taken from man mount and man fstab


For example
cat /etc/fstab
--snip--
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
/dev/sda14      /media/share    ext3    defaults    0 0

will mount automatically an ext3 filesystem on partition /dev/sda14


 The "defaults" options: contains the properties rw, suid,  dev,  exec,  auto,  nouser,  and  async.

This would automatically mount the file system, to unmount and mount as a normal user,  use
defaults,user

Hope that helps

---

