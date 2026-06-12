---
title: "Partition won't mount"
date: 2010-05-15
forum: General Help
---

### Post by LinuxPrevails on 2010-05-15
Hi, I just set up my dad's computer with Ubuntu about a week ago. (I've been using Ubuntu for several years now.) But his computer recently crashed (I have no idea what he did with it!). He needs some files that are on his main partition but when I try to mount his main partition from the Ubuntu live CD I get this message:

[FONT=Courier New][SIZE=1]Unable to mount 36 GB Filesystem

Error mounting: mount: wrong fs type, bad option, bad superblock on /dev/sda1,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so[/SIZE][/FONT]

What can I do to mount this partition and retrieve the needed files?

---

### Post by TeoBigusGeekus on 2010-05-15
Try to fsck it
```
fsck /dev/sda1
```

---

### Post by bananas4370 on 2010-05-15
> **LinuxPrevails said:**
> Hi, I just set up my dad's computer with Ubuntu about a week ago. (I've been using Ubuntu for several years now.) But his computer recently crashed (I have no idea what he did with it!). He needs some files that are on his main partition but when I try to mount his main partition from the Ubuntu live CD I get this message:

[FONT=Courier New][SIZE=1]Unable to mount 36 GB Filesystem

Error mounting: mount: wrong fs type, bad option, bad superblock on /dev/sda1,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so[/SIZE][/FONT]

What can I do to mount this partition and retrieve the needed files?

And what did the output of dmesg say? What files system is on this partition? What did you type to mount this partition?

---

### Post by LinuxPrevails on 2010-05-15
Thanks a lot, TeoBigusGeekus! It worked like a dream. My dad and I owe you one!

---

