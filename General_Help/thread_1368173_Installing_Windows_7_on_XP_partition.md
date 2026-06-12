---
title: "Installing Windows 7 on XP partition"
date: 2009-12-30
forum: General Help
---

### Post by lmoreira on 2009-12-30
Hi All,
Although I am now using Ubuntu for 90% of my time, I still have the need to use windows once in a while for work and such. Until now I had XP but someone just gave me windows7 and I would like to install it in the XP partition. what is the best way to do it?
Thanks
      Luis

---

### Post by Mark Phelps on 2009-12-30
You would do better going to a Windows 7 forum with Win7 questions ...

Suggest contacting sevenforums.com -- they have lots of forums and tutorials available.

---

### Post by lmoreira on 2009-12-30
Hi,
My question as very little to do with windows7! I have a dual boot system with Ubuntu as my main OS, on the second partition I have XP. I want to install windows7 on the XP partition, which is pretty strait forward but what I would like to know is how do I deal with GRUB, I do not want to damage the startup for my Ubuntu. I came from XP originally Hence when I installed Ubuntu for the first time GRUB was installed and coming up at startup automatically. I don't care much for the XP partition but I don't want to damage the Ubuntu part.   
I do realise this is to basic for people like you that deal with Ubuntu all the time but for me this is a worry.
Best Regards
              Luis

---

### Post by wilee-nilee on 2009-12-30
If you just install the W7 in the XP partition it will only boot to W7 you have to use a hardy live CD to reinstall grub, there are instructions all through the forums on how to do this.

The W7 install may also make 2 partitions a 100mb boot partition and the main running partition so you want to make sure you have the space and ability to have a additional partition besides the XP alone. 

If it was me since I use the latest Ubuntu/Linux OS, I would save everything from the hardy and XP you want and do a fresh install of W7 first using the custom install into a preset ntfs partition, built with gparted from a live Ubuntu CD, then install whatever Ubuntu you want and maybe a separate home partition for file sharing between the 2 OS.

---

### Post by lmoreira on 2010-01-01
Hi wilee-nilee,
Thanks for your help, I manage to find a very good tutorial on the forum and I now have Ubuntu and windows7 running.
Best Regards
            Luis

---

