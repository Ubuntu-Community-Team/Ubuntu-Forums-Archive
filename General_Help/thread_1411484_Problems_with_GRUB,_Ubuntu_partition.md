---
title: "Problems with GRUB, Ubuntu partition"
date: 2010-02-20
forum: General Help
---

### Post by lalilulelo on 2010-02-20
So recently I tried to install Windows XP on a computer that had Ubuntu on it, not knowing that this would wipe out GRUB along with the ability to boot to Ubuntu. So first I tried Super Grub Disk (and Auto Super Grub Disk after that), but it froze at stage5. Then I tried this guide:

[http://gadgetmix.com/index/how-to-restrore-grub-bootloader-in-ubuntu-9-10-standard-and-netbook-remix/](http://gadgetmix.com/index/how-to-restrore-grub-bootloader-in-ubuntu-9-10-standard-and-netbook-remix/)

and I got nothing but a SH: Grub> prompt. Then I tried this guide:

[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

and it gave me an "Error 22: No such partition" message after trying to install grub to stage 1 and 2. Now when I try to boot I get the word "GRUB" printed over and over again. Great. One thing that I noticed is that when I loaded the LiveCD and tried to mount the partition with Ubuntu installed on it (so I could look at the files), it told me "Unable to mount 40 GB Extended - Message did not receive a reply (timeout by message bus)." This seems to tell me that there may be something wrong with this partition, though I can't imagine what. What is going on with my computer? How do I get it to boot from GRUB again?

---

### Post by oshunluvr on 2010-02-20
Have you tried booting to the livecd and selecting "Repair..."???

---

### Post by lalilulelo on 2010-02-20
I don't see a "Repair" option anywhere. Where is it?

---

### Post by lalilulelo on 2010-03-14
Bump. Any help?

---

### Post by oldfred on 2010-03-14
Your two links are to different versions of grub. New installs of Karmic now use grub2 (1.97beta4), everything prior was grub legacy (0.97), and Lucid will be grub2(1.98).

What version of Ubuntu do you have and if Karmic is it an upgrade or clean install?

How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10)
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

---

