---
title: "Help, new user"
date: 2010-06-24
forum: General Help
---

### Post by Zirts on 2010-06-24
Hi,

I installed Ubuntu on the same drive that i have my windows on, and now I lack of free space when I'm on Ubuntu. So my question is, how can I get more space without getting my self a new seperate drive and installing Ubuntu there. The windows "side" still has a bit of free memory so I would like to use it on Ubuntu if it's possible.


Also my sound is not working on Ubuntu somewhy, I have the latest version of Ubuntu and i allread tyred to istall some sort thing that someone sayd would help me but it didn't, so I'm still stuck with no sound...

---

### Post by arrange on 2010-06-24
Are you using Ububtu as a Windows application (*Wubi*) or have you installed Ubuntu on a separate partition (something like D: in Windows or */dev/sda2* in Ubuntu)?

---

### Post by Zirts on 2010-06-24
It's a seperate partition, /dev/sda1/

---

### Post by coolman98 on 2010-06-24
If you are new a new user you should probably ask in Absolute beginners section.

---

### Post by Zirts on 2010-06-24
Well as the post is allready in here than theres no point to make more topics or what?

---

### Post by arrange on 2010-06-24
You can boot into a LiveCD a use GParted to shrink the Windows partition and resize the Ubuntu one. If unsure, post a screenshot from GParted here.
Before doing this be sure to back up anything important you have on both partitions - resizing is generally a safe operation, but if you f.e. lose power in the middle...

---

### Post by Zirts on 2010-06-24
[IMG]http://ubuntuforums.org/attachment.php?attachmentid=161430&stc=1&d=1277399089[/IMG]

---

### Post by arrange on 2010-06-24
It looks like you're using *Wubi*, NOT a separate partition for Ubuntu.
Resizing a wubi virtual disk is a little complicated, but possible:
[https://wiki.ubuntu.com/WubiGuide#How%20do%20I%20resize%20the%20virtual%20disks?](https://wiki.ubuntu.com/WubiGuide#How%20do%20I%20resize%20the%20virtual%20disks?)

But, if you like Ubuntu, you should consider installing it on a separate partition.
[https://help.ubuntu.com/community/GraphicalInstall](https://help.ubuntu.com/community/GraphicalInstall)

---

