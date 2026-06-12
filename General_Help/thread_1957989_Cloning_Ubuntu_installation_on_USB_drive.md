---
title: "Cloning Ubuntu installation on USB drive"
date: 2012-04-13
forum: General Help
---

### Post by chenxinghao on 2012-04-13
I installed Ubuntu 11.10 on to an 8GB USB 2.0 thumb drive early this week so I can boot my laptop with it. Now I found that with a few applications installed there is only less than 2GB space left on the USB thumb drive.
 
I want to move the Ubuntu installation to a 16GB USB thumb drive. But before I start for a fresh install, I like to know if there is a way to "clone" the Ubuntu setup on the 8GB USB drive to a 16GB one (to save time).
 
If so, how?
 
Thank you.

---

### Post by zero2xiii on 2012-04-13
Hay,

I have never done this before. But Boot from a LiveCD and use gparted to copy the partion from one to the other, and then resize the latter if needed. it MIGHT work, however you might need to re-do grub.

Cherz

---

### Post by chenxinghao on 2012-04-13
Thanks for the input.

I am a newbie and I have no clue about what you have suggested. They sound to me very complicated than doing a fresh install.

---

### Post by C.S.Cameron on 2012-04-13
Use dd then expand the partition using gparted.

If your 4GB drive is sda and your 8GB drive is sdb, then:

> dd if=/dev/sdb of=/dev/sdc

This will take a while and there is no progress meter.

---

### Post by chenxinghao on 2012-04-13
Thanks. I will give it a try this weekend.

Would dd also clone the (default) 1.5GB swap space on the new device as well?

---

### Post by C.S.Cameron on 2012-04-14
Dd will clone the drive exactly to the new drive, partitions, boot loaders, swap and all.

For more info on dd:

[http://www.linuxquestions.org/questions/linux-newbie-8/learn-the-dd-command-362506/](http://www.linuxquestions.org/questions/linux-newbie-8/learn-the-dd-command-362506/)

---

### Post by dragonfly41 on 2012-04-14
Don't forget clonezilla

---

### Post by chenxinghao on 2012-04-17
Well, it took a little more than 2 hours for 
 
sudo dd if=/dev/sda1 of=/dev/sdb1
 
to complete. But the problem is that the resulting 16GB USB thumb drive doesn't boot!

---

