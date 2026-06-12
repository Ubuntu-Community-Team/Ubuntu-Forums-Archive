---
title: "ext3 Hard Disk"
date: 2010-04-11
forum: General Help
---

### Post by Tux118 on 2010-04-11
Alright, I have a 200 gig hard drive in my system. I sucsessfully formatted it as ext3, but whenever I try to put any files on it says I don't have permissions to re-create the file in the hard disk.

I am sure there is a simple solution to this, and I am sorry if I am being a noob, I have only been using ubuntu for two years. 

Thank You,

Tux118

---

### Post by Tux118 on 2010-04-11
I forgot to add, it is a Maxtor 6Y200P0.

---

### Post by drs305 on 2010-04-11
It's a permission issue, and how the permissions are assigned depends partly on the type of format you use.

For ext3, make yourself the owner of the mount point:
```
sudo chown -R yourusername: /media/yourmountpoint

```
Example:
sudo chown -R john: /media/myfiles
Most hard drives are mounted by settings in fstab. Here is an excellent guide on how to set up fstab:
[Understanding fstab]("http://ubuntuforums.org/showthread.php?&t=283131")

---

### Post by Tux118 on 2010-04-11
> **drs305 said:**
> It's a permission issue, and how the permissions are assigned depends partly on the type of format you use.

Most hard drives are mounted by settings in fstab. Here is an excellent guide on how to set up fstab:
[Understanding fstab]("http://ubuntuforums.org/showthread.php?&t=283131")

Alright, I will check out the tutorial, hopefully that can help me. I will try a chown on it first though.

Thank You!!!

---

### Post by Tux118 on 2010-04-11
Yep the chown worked. 

Thank you!

---

