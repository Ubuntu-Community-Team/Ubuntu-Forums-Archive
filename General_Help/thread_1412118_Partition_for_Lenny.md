---
title: "Partition for Lenny"
date: 2010-02-20
forum: General Help
---

### Post by Hman242 on 2010-02-20
I'm trying to partition my HDD for Debian 5(Lenny). I have no idea how partitioning is done. I also don't know how I would go about installing Lenny on that partition(I have an idea though). Could anyone help me out here?

---

### Post by mwcrowley on 2010-02-20
Is this a new install or are you adding it to a hard drive that already has Ubuntu installed.
gparted will help you shrink a partition and create space for installing. Lenny  But you really need to understand what you are doing because you have the power to hose your current installation.  
Back up your data first and then start mucking around.

---

### Post by x33a on 2010-02-20
As mwcrowley said :D

Give gparted live a try, though.

[http://www.linux.com/archive/feed/53924](http://www.linux.com/archive/feed/53924)

---

### Post by Hman242 on 2010-02-20
Sorry for not replying guys, but I had been doing stuff. I've been meaning to post this also...

 I'm using Gparted and I can't seem to unmount my main partition. I'm not surprised, but how can I edit my main partition then? I need to edit it as it takes up all the room in my HDD and without making it smaller I can't make a new partition because there is no room to. Any ideas?
EDIT: A LiveCD would do that. I probably should have done some looking around the web before posting.

---

### Post by Hman242 on 2010-02-21
I've got my partition set up, but how do I install Debian on that specific partition?

---

### Post by x33a on 2010-02-21
Just point debian's installer to the partition.

---

### Post by RedSquirrel on 2010-02-21
> **Hman242 said:**
> I've got my partition set up, but how do I install Debian on that specific partition?
When you get to the step in the installer where you do the partitioning, you can select "Manual" partitioning. This will allow you to specify which partition you want the installer to use for your new Debian system.

---

### Post by Hman242 on 2010-02-21
Install went fine, but now GRUB doesn't recognize Ubuntu that's on my other partition. Can you tell me how to fix that?
EDIT: If it helps, it seems like Lenny has installed Grub Legacy and before this I has GRUB2.

---

### Post by x33a on 2010-02-21
simple solution:
try supergrubdisc.

otherwise: manually edit the grub configuration file and add ubuntu's location.

---

### Post by Hman242 on 2010-02-21
After posting my last post I decided to reinstall Ubuntu on the partition that had Debian on it since I didn't like it anyway to get back GRUB2. I didn't know how to edit it, and even though I've solved my problem, could you tell me how? I would like to know if I do this again in case I actually like the new OS I try.

---

### Post by x33a on 2010-02-22
> **Hman242 said:**
> After posting my last post I decided to reinstall Ubuntu on the partition that had Debian on it since I didn't like it anyway to get back GRUB2. I didn't know how to edit it, and even though I've solved my problem, could you tell me how? I would like to know if I do this again in case I actually like the new OS I try.

Grub legacy howto:

[https://help.ubuntu.com/community/GrubHowto](https://help.ubuntu.com/community/GrubHowto)

---

