---
title: "Set Windows as Default OS when Dual Booting Ubuntu"
date: 2011-07-22
forum: General Help
---

### Post by DugMatt77 on 2011-07-22
Pretty much need help with setting windows as the default OS when dual booting ubuntu. Have gone into system settings on both windows and ubuntus and chosen the option to boot windows vista first, but it has not worked. Your help would be much appreciated. 

ps. am using windows vista and ubuntu 10.10

---

### Post by Mr. Shannon on 2011-07-22
First, when you installed Ubuntu it most likly overwrote the windows boot loader, so windows can't do anything about the boot order unless you restore the windows boot loader and then you will loose your ability to boot Ubuntu (at least in a normal setup).

Now that that's out of the way, what you want to do is install **startupmanager** in Ubuntu.  This application will give you an easy way to change the boot order of grub (the boot loader that Ubuntu uses).

NOTE: If you are using Wubi then I don't think the instructions above are what you want.

---

### Post by Quackers on 2011-07-22
Is this a wubi installation?

---

### Post by ig591 on 2011-07-22
Hope its O.K to burst into, I want to do the same so, How does one install startupmanager? (Not using wubi - Ubuntu 11.04 and Win7)

---

### Post by mastablasta on 2011-07-22
find it in software center or synaptic package manager. and then click install.

---

### Post by ig591 on 2011-07-22
> **mastablasta said:**
> find it in software center or synaptic package manager. and then click install.
Thank you

---

### Post by ig591 on 2011-07-23
Didn't work for me
Marked Win7 as default in **startupmanager.** 
Yet still Ubuntu appears first on the list at the grub menu and as such the
default one. What am I wrong about?

---

### Post by Mark Phelps on 2011-07-23
You're not wrong about anything.  If you've been doing regular updates, you're probably now running GRUB v1.99RC -- and startup-manager can NOT handle a menu generated with that GRUB version because it now has nested entries.

I've run into exactly the same problem.  So, I'll provide you the solution ...

1) Open a file manager, find /boot/grub/grub.cfg, double-click it to open it.  Scroll down to the Windows 7 entry.  Find the text that is something like "Windows 7 (loader) (on /dev/sdd1)".  That is text you will need to copy.
2) Enter the following in the terminal "gksudo gedit /etc/default/grub".  That's the default entries file for GRUB.  Find the line that has "GRUB_DEFAULT=".
3) Highlight and copy the Windows 7 text from the grub.cfg file to the Default line in the default/grub file.  That line should now be something like "GRUB_DEFAULT="Windows 7 (loader) (on /dev/sdd1)". Save the default file.
4) Close out the grub.cfg file -- make sure you do NOT save any changes to it.
5) Enter "sudo update-grub" That will regenerate the GRUB menu.  When you look at grub.cfg file now, you should see a line near the top something like the following: "set default="Windows 7 (loader) (on /dev/sdd1)"
6) Reboot.  The GRUB menu should now highlight the Windows 7 loader line.

Note that since you changed the defaults file, you should not have to change this again unless you add or remove physical drives from your system.

---

### Post by dirghrabadia on 2011-07-23
[http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)

---

