---
title: "My linux OS isn't available after installing Windows XP &amp; Vista?!"
date: 2011-04-03
forum: General Help
---

### Post by jeremy28 on 2011-04-03
Hi all;
 
I've already had 3 OS's on my system:

Ubuntu 9.10 - Windows XP SP3 - Windows Vista
on my system.
 
My linux (ubuntu) was almost perfect for me (updated, well configured with many installed softwares...)
 
I have a 300 GB hard disk that was as below:
 
Win. XP on **C** drive (100 Gb)
Win. Vista on **D** drive (100 Gb)
And 100 Gb of unpartitioned space hosting ubuntu!
 
I decided to install Win. XP & Vista again **without** any change to ubuntu!
So that, I deleted and formatted C & D drives  to install new Win. XP & Vista.
But after that, I can't access to ubuntu and GRUB is vanished now!!
 
Apparently, Windows isn't able to identify all the OS's on system while installing,
So, the Windows boot manager looses my Linux OS!
 
Anyway currently, I have only XP & Vista on my system and don't know how should I revive my previous ubuntu?
 
Is there any method to access to linux OR I should install a new ubuntu AGAIN?!!
 
Please help, I'm confused!
 
Regards.

---

### Post by jag2010 on 2011-04-03
Your new install will have overwritten your boot settings.  I'm currently going through a similar problem, which I haven't quite resolved yet.  I don't think there will be any need to reinstall Ubuntu and no doubt someone more experienced will sort you out with a solution!

---

### Post by MichealH on 2011-04-03
Grub gets overridden when installing Windows, what you can do it look at this to help you:

[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

---

### Post by cbowman57 on 2011-04-03
This is handy tool for these situations.

Recatux
[http://www.supergrubdisk.org/2011/03/07/rescatux-0-25-released/]("http://www.supergrubdisk.org/2011/03/07/rescatux-0-25-released/")

Yes, it can be easily done from the command line from a LiveCD but this makes it extremely convenient.

---

### Post by techunit on 2011-04-03
Wow so many GRUB problems in one day. That must be three.

Head Over Here
[http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)
Subject Number 13

This will guide you in reinstalling GRUB so you can use Ubuntu again.
Good Luck.

---

