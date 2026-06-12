---
title: "Dual Boot Startup Option?"
date: 2011-07-07
forum: General Help
---

### Post by iRide113 on 2011-07-07
So when I first installed  Ubuntu I got a dual boot option screen like this:

[IMG]http://www.instablogsimages.com/images/2011/02/10/uninstall-ubuntu-from-dual-boot-with-windows-7_DFb4g_25552.png[/IMG]

But after reformatting and reinstalling, I get a screen like this:

[IMG]http://dl.dropbox.com/u/21172955/2011-07-07%2019.32.40.jpg[/IMG]

Is there anyways to change it back to the first screen?

Just more appealing to me. I like the option of Windows 7 being the first option so I don't have to use the arrows to move it. I rather just let it boot up into Windows7 than Ubuntu.

Any ideas?

---

### Post by searchfgold6789 on 2011-07-07
It looks like in the first case, you used Wubi to install Ubuntu. Wubi just basically lets you use Ubuntu without doing a complete installation. It does not use a separate boot loader outside of Windows, like a full installation would. The second screen looks like you did a full installation of Ubuntu. To get a screen exactly like the first one, you would have to go back to using a Wubi installation.
If you just want the functionality you're speaking of, that is the ability to simply turn on the computer and have it boot to Windows, then open up a Terminal window and type ```
sudo gedit /etc/default/grub
```A new text file will come up, and on one of the lines you will see ```
GRUB_DEFAULT=0
```Edit it so it reads```
GRUB_DEFAULT=5
```Save and reboot. If you have any trouble, post back and we'll try to help you further.
 - search

---

### Post by iRide113 on 2011-07-07
> **searchfgold6789 said:**
> 
If you just want the functionality you're speaking of, that is the ability to simply turn on the computer and have it boot to Windows

If I run these codes, will I still get the option to boot into Windows and Ubuntu?

If I can't change the menu style, I would just want the default to be Windows, but still have the options to boot into Ubuntu.

---

### Post by etwill on 2011-07-08
i was having problems with the boot loader and found a program in the ubuntu software center called start up manager which allowed you to change  the boot up order

---

### Post by Theredbaron1834 on 2011-07-08
The problem is that the first one is a windows bootmgr, where as the second one is grub. I don't know of any way to install bootmgr from linux, or how to edit bootmgr from windows to boot linux off a ext3/4 drive. The only thing I could think is to reinstall bootmgr, boot up windows and try to find a way to edit it.

---

### Post by linuxman94 on 2011-07-08
To answer your question, yes, you will still have the option to boot ubuntu.  Do what search said, except for use the command```
gksudo gedit /etc/default/grub
```

Redbaron:  He doesn't need to mess with the windows boot manager because he's got a true dual boot, not wubi.

---

### Post by iRide113 on 2011-07-08
Edited to show 5, but still the default is not Windows, but rather Ubuntu.

---

### Post by searchfgold6789 on 2011-07-08
> **iRide113 said:**
> If I run these codes, will I still get the option to boot into Windows and Ubuntu?

If I can't change the menu style, I would just want the default to be Windows, but still have the options to boot into Ubuntu.
Yes, it would still be the same menu, but the default selection will be Windows and not Ubuntu.

---

### Post by iRide113 on 2011-07-08
> **searchfgold6789 said:**
> Yes, it would still be the same menu, but the default selection will be Windows and not Ubuntu.

Still got the problem after editing it.

---

### Post by nrundy on 2011-07-08
You can also install "Startup-Manager" from USC and get a GUI to make changes to the countdown and which OS starts by default.

Try installing Startup-Manager, this worked great for me.

---

