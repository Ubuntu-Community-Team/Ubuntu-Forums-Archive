---
title: "How to change the default OS when boot"
date: 2012-02-22
forum: General Help
---

### Post by fs_tigre on 2012-02-22
Hi,

I installed Ubuntu in my cosins computer but he want to have Windows is the primary OS not Ubuntu as is right now.  In other words right now when I turn the computer on it waits 10 seconds and if I dont scroll down to select Windows the computer boots on Ubuntu and he would like to be the other way, where it boots on Windows by default unless you  specify Ubuntu.

Is it possible to make Windows the default OS when booting?

Thanks

---

### Post by aura7 on 2012-02-22
Install StartupManager for Ubuntu
 
[https://help.ubuntu.com/community/StartUpManager](https://help.ubuntu.com/community/StartUpManager)
 
In this you can select the default operating system and time too...

---

### Post by rusljam on 2012-02-22
[Here]("https://help.ubuntu.com/community/Grub2") in section "Configuring Grub 2" you will have all explanations about how to change default menu entry in grub menu.

---

### Post by fs_tigre on 2012-02-22
Awesome! Thanks a lot for your help.

---

### Post by Mark Phelps on 2012-02-23
Unfortunately, startup-manager is likely NOT to work.  So, don't bother with it.

Instead, you should use GRUB-Customizer:

[http://ubuntuforums.org/showthread.php?t=1664134]("http://ubuntuforums.org/showthread.php?t=1664134")

---

