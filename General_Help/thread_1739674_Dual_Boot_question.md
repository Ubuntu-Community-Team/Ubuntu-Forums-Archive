---
title: "Dual Boot question"
date: 2011-04-26
forum: General Help
---

### Post by vulcaninvt on 2011-04-26
I recently installed Ubuntu onto my Windows 7 machine. It is up and running and I am enjoying using it.

One thing I notice and hope someone here can steer me in the right direction. When I start up my computer I have the list of options to choose from, if I choose to boot into Win 7 I am the presented again with another boot menu from windows.  I would like to remove the Windows boot loader.

Can anyone assist?

Thanks!

---

### Post by Mark Phelps on 2011-04-26
From your description, it sounds like you installed Ubuntu inside Win7 using Wubi.  If that is the case, removing the Win7 boot loader will completely disable your access to Ubuntu.

To get a better look at your system, open a terminal in Ubuntu and enter "sudo fdisk -lu" (that's a lowercase L, not a one). That will list out your partitions.  If there are no Linux filesystem partitions, that will confirm a Wubi install.

---

### Post by Frogs Hair on 2011-04-26
With a Wubi installation , the Windows boot loader Will open first with Windows and Ubuntu option . After selecting Ubuntu Grub will open and offer the Ubuntu  boot options. [https://wiki.ubuntu.com/WubiGuide](https://wiki.ubuntu.com/WubiGuide)

---

### Post by vulcaninvt on 2011-04-26
I installed Ubuntu alongside Windows using a CD. I was not seeing the Windows boot loader. I think the issue occurred when I used a program to try and use windows as the boot loader and not the Ubuntu boot loader, I should have explained that in my first message.  

Thanks for any insight!

---

### Post by Mark Phelps on 2011-04-26
> **vulcaninvt said:**
> I installed Ubuntu alongside Windows using a CD.
OK -- non-Wubi install ...
>  I was not seeing the Windows boot loader.
Typical situation.  You have to then open a terminal in Ubuntu and enter "sudo update-grub".  This will regenerate the GRUB menu and add an entry for Windows.
>  I think the issue occurred when I used a program to try and use windows as the boot loader and not the Ubuntu boot loader, I should have explained that in my first message.
Guessing you used EasyBCD, right?

Basically, you can NOT get rid of the Windows boot loader.  Why? Because, if you do, Windows will not boot.

GRUB creates a menu system, with entries for other OSs, but when you select a Windows entry, it hands off control to the Windows boot loader in that partition.  If there is no such loader, the screen blinks and you are returned to the GRUB menu.

What I suggest you do is the following:
1) Go into Win7 and remove EasyBCD
2) Follow the directions in the link below to restore GRUB:

[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows]("https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows")

---

