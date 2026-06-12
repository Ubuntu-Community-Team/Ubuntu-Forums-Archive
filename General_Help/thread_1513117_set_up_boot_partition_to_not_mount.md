---
title: "set up boot partition to not mount"
date: 2010-06-19
forum: General Help
---

### Post by COKEDUDE on 2010-06-19
I was reading this about setting up boot partition to not mount automatically. 
[http://www.gentoo.org/doc/en/handbook/handbook-x86.xml?part=1&chap=8](http://www.gentoo.org/doc/en/handbook/handbook-x86.xml?part=1&chap=8)
> Some users don't want their /boot partition to be mounted automatically to improve their system's security. Those people should substitute defaults with noauto. This does mean that you need to manually mount this partition every time you want to use it.

Add the rules that match your partitioning scheme and append rules for your CD-ROM drive(s), and of course, if you have other partitions or drives, for those too.

Now use the example below to create your /etc/fstab: 

Could anyone explain how to set up a boot partition please.

---

### Post by wilee-nilee on 2010-06-19
Works until somebody boots a live cd.

---

### Post by jerome1232 on 2010-06-19
You would have to have a separate boot partition to do that, and if this is the same computer as the one that I was helping with in another thread, you don't have that.

---

### Post by COKEDUDE on 2010-06-22
> **jerome1232 said:**
> You would have to have a separate boot partition to do that, and if this is the same computer as the one that I was helping with in another thread, you don't have that.

It is :). Could you explain how to set it up please. I forgot to ask that in my first post.

---

### Post by Mark Phelps on 2010-06-22
> **COKEDUDE said:**
> I was reading this about setting up boot partition to not mount automatically. 

You do realize that once someone gets physical access to your machine, all this work will have been for nothing!  Depending on how much time they have, they could either boot from a variety of boot CDs/USBs, or simply remove the hard drive.

It's going to be a LOT of work and, at the end of the day, will not really provide much added security.

---

### Post by COKEDUDE on 2010-06-24
> **Mark Phelps said:**
> You do realize that once someone gets physical access to your machine, all this work will have been for nothing!  Depending on how much time they have, they could either boot from a variety of boot CDs/USBs, or simply remove the hard drive.

It's going to be a LOT of work and, at the end of the day, will not really provide much added security.

Alright that makes sense. Thats the reason I use the encryption feature whenever I install Linux. I think it does a pretty good job.

---

