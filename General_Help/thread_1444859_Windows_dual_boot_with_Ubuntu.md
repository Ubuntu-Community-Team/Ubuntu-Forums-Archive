---
title: "Windows dual boot with Ubuntu"
date: 2010-04-01
forum: General Help
---

### Post by Tomween1 on 2010-04-01
Forum admin, please bump this if you feel it is in the wrong local:grin:
 
I recently tried loading Ubuntu onto a separate drive on my computer. All went well except for the boot process. Upon booting I no longer was brought to the normal dual boot screen, instead I now got what I beleive to be the Linux boot screen. From here I was able to still load windows, with a few more steps. What didn't like was the thought that Ubuntu took over. I did some research and figured I should reinstall it. I went to the Windows partition and formatted the section that had Ubuntu on it. Much to my surprise Ubuntu loaded itself on the same HDD as Windows 7. I formatted the section holding Ubuntu and restarted the system to this problem: ***grub loading error: unknown filesystem grub rescue*** So here I' stuck. The only ability I have is to get into bios and change my boot devive. I need help retrieving Windows.
 
Thank you, Tom

---

### Post by johngreth on 2010-04-01
If I understand what happened correctly, Grub is now looking for the stuff on how to boot on the Ubuntu partition that no longer exists. There is some way to use the live CD to fix this, but I don't know how to do that. What you could do is try installing Ubuntu on the other drive and let it find windows so it can boot Windows again.

---

### Post by oldfred on 2010-04-01
IF you are not immediately reinstalling Ubuntu you will have to reinstall the window boot loader. from windows CD - fixboot command in windows repair. More Instructions:

How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10)
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

From a Ubuntu  liveCD you can install a generic windows boot loader. (does not install lilo just uses it). Some linux based repair CDs include lilo.
Restore basic windows boot loader. sda = first drive.
sudo apt-get install lilo
sudo lilo -M /dev/sda mbr

---

### Post by Tomween1 on 2010-04-02
Thanks oldfred your link solved the problem

---

