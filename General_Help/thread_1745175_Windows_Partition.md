---
title: "Windows Partition"
date: 2011-04-30
forum: General Help
---

### Post by Isader on 2011-04-30
Good evening, my name is ISA and am new to ubuntu and having a frustrating scenario. Maybe somebody can help me solve the issue. I used my entire hard drive to install ubuntu11.04. Installed beautifully with no error messages. I decided to allocate space for a windows partition. Then I proceeded to install windows7 and completed succesfully except that when I boot the machine it loads directly to windows and Im lost on how to access my Ubuntu OS. Thanks to all:P
:guitar:

---

### Post by rickfish99 on 2011-04-30
You can't install Windows on a Linux partition. You have to install Window7 first, which will wipe out your current Ubuntu installation, then install Ubuntu "alongside" windows. Then when you boot your computer Grub will appear and allow to choose either Windows or Ubuntu. If you have any critical information in Ubuntu now you will need to back it up on a different drive because you will lose it when you install Windows.
Hope this helps.

---

### Post by Isader on 2011-05-02
I really did not want to go through that process. I thoght that Windows had a GRUB feaure like Ubuntu does. But if installing windows first is my only choice I guess I'll do it. Thanks Very Much. I'll leave the thread open for suggestions. Is it better to use Virtual box than having 2 OSs side by side? There are programs that are only compatible with internet explorer. Please Help. :confused:

---

### Post by gandaran on 2011-05-02
use [rescatux]("http://www.supergrubdisk.org/category/download/rescatuxdownloads/") to fix grub, no need to reinstall any OS, or you can even use the ubuntu live-cd to restore grub.

---

### Post by oldfred on 2011-05-02
It is a known issue that windows installs its boot loader to the MBR. You just need to reinstall grub2's boot loader to the MBR. 

How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10)
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)
Reinstall grub2 - Short version & full chroot version
[https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202](https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202)


[http://www.supergrubdisk.org/](http://www.supergrubdisk.org/)

After rebooting into Ubuntu you need to run this to add windows to the grub menu.

```
sudo update-grub
```

---

