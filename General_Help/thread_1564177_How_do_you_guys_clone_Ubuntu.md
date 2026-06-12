---
title: "How do you guys clone Ubuntu?"
date: 2010-08-30
forum: General Help
---

### Post by listerdl on 2010-08-30
Hi, what program do you use to clone your machine?

I have had a look at clonezilla but it does seems a bit clunky - any other ideas?

Thanks

---

### Post by inameiname on 2010-08-30
I use Remastersys. I make one Remastersys custom disc and can throw it on several computers just like that. And all it requires is a simple couple clicks.

While it's not technically a cloner, as how it works is that it takes your computer, as tweaked and updated as you'd like, and makes a custom live disc, just as the one you get from Ubuntu.com and download to install in the first place. Plus, it's cool as it can work as a Live cd so you can check things out, or share them with others, without installing a thing.

[http://www.geekconnection.org/remastersys/ubuntu.html](http://www.geekconnection.org/remastersys/ubuntu.html)

---

### Post by zaphod777 on 2010-08-30
I am a big fan of clonezilla. While the interface will not win any awards it makes it up in performance. You can backup an image to a USB drive, do a disk to disk clone, or make a server to manage all of the images. 

It is also great for upgrading the HDD on a machine. I will put the new HDD in an external case and then clone the old one to the new one and then use an Ubuntu live CD with GPARTED to expand the partition. It even works great for Windows machines.

---

### Post by lmarmisa on 2010-08-30
I love clonezilla. It works great both cloning disks/partitions or saving/restoring images of disks/partitions.

---

### Post by listerdl on 2010-08-30
that sounds awesome thanks very much!!!

---

### Post by listerdl on 2010-08-30
> **lmarmisa said:**
> I love clonezilla. It works great both cloning disks/partitions or saving/restoring images of disks/partitions.

yeah i hear you - but i just find it difficult to use, or rather tricky to use....i have a dual boot so im sort of worried that i might screw it up.

i might re-try though, i think i should.

---

### Post by lmarmisa on 2010-08-30
Clonezilla works with Linux and Windows partitions too. So, try to save or clone the complete hard drive. I recommend you to select Beginner mode. Try to use the last stable Debian based version of Clonezilla. I prefer to run Clonezilla from a pen drive.

---

### Post by C.S.Cameron on 2010-08-30
I boot a Live USB and use ```
dd if=/dev/sda of=/dev/sdb
``` to clone sda to sdb.
It's simple but it works.

---

### Post by inameiname on 2010-08-30
Gee, I think I've lost in terms of Remastersys being a favorite in this thread. :P Hehe. Anyway, here is a good link to a recent poll on the top backup tools for Linux:

[http://www.webupd8.org/2010/05/best-linux-backup-tool-software.html](http://www.webupd8.org/2010/05/best-linux-backup-tool-software.html)

---

### Post by Sam on 2010-08-30
Be VERY careful when using dd as C.S.Cameron suggested. You can easily wipe your hard drive if you swap arguments/devices.

---

### Post by deserthowler on 2010-08-30
> **inameiname said:**
> Gee, I think I've lost in terms of Remastersys being a favorite in this thread. :P Hehe. Anyway, here is a good link to a recent poll on the top backup tools for Linux:
]

I like remastersys too.  Makes a nice live DVD.

Earl

---

### Post by inameiname on 2010-08-30
Cool. I'm not alone! :P Thank you, Earl! Hehe

---

### Post by cj.surrusco on 2010-08-30
> **C.S.Cameron said:**
> I boot a Live USB and use ```
dd if=/dev/sda of=/dev/sdb
``` to clone sda to sdb.
It's simple but it works.

I do the same. Definitely the easiest way. But it is also the easiest way to mess something up, so make sure you have the paths right.

---

