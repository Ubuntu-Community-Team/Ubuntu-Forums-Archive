---
title: "How can I resize a NTFS partition"
date: 2010-04-18
forum: General Help
---

### Post by mjsilverstri on 2010-04-18
Hi,

I have installed ubuntu 9.10 on an external drive 'sdb'.  It has a NTFS partition, which is 600GB and I think it is also my 'boot'  partition. (when i looked at it in gparted, it has a 'boot' flag).

My question is how can I resize it so that i can create a ext4 partition?  I have tried win7, it said my partition is corrupted. But I am able to boot from it to Ubuntu 9.10.

And I have tried GParted, it does not let me 'new' or resize the ntfs partition.

Thank you for your help.

---

### Post by itiswhatitis on 2010-04-18
This topic should help you.

[http://ubuntuforums.org/showthread.php?t=96617](http://ubuntuforums.org/showthread.php?t=96617)

---

### Post by mikewhatever on 2010-04-18
You need to use Gparted from the live cd, because if you try resizing from the Ubuntu installation, the partition in question will be in use.

---

