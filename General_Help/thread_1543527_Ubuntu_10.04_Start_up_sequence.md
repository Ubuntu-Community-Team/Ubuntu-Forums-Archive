---
title: "Ubuntu 10.04 Start up sequence"
date: 2010-08-01
forum: General Help
---

### Post by richardhp on 2010-08-01
Hi,

I'd like to know what happens in between me selecting which kernel to boot from the Grub2 menu, and me ending up in Gnome looking at the desktop GUI.

For instance, when does the X server start, when is gnome started, in what order do these things happen and how can i have control over this process? The main appeal of linux to me is being able to choose which window manager, which desktop environment etc are used but I cannot seem to find out how to configure these things.

I've been googling extensively and looking in books, the forums, ubuntu community and documentation but this information does not seem to be out there.

---

### Post by AlphaLexman on 2010-08-01
the command 'dmesg' will report everything the kernel does.

---

### Post by ajgreeny on 2010-08-01
After choosing your kernel in grub, the kernel is booted and the boot sequence continues from there.  What happens can be seen in the dmesg output, but if you want an image of what is going on install **bootchart** and after each boot there will be a graphic showing what happened in /var/log/bootchart which may help you.  A lot of info about you bootup is also available in /var/log/syslog

If you have set the machine to autologin without you entering your username ans password, you will be missing out on some of the options available.

The x-server starts after your password is entered, and the DE you choose is then started after that.  You can change the DE you use, assuming you have more than one installed, at the login screen,where bottom left there is a drop-down button (drop-up, I suppose as it's at the bottom), where you can choose GNOME, Failsafe gnome, xterm, and any others available.  The window manager can be changed later if you want with the command **compiz --replace** or **metacity --replace** in the Alt+F2 Run dialog, depending on which WMs are installed.

---

### Post by richardhp on 2010-08-01
thanks that's awesome

---

