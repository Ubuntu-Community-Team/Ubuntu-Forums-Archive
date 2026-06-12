---
title: "Using Ubuntu as a server?????"
date: 2010-09-12
forum: General Help
---

### Post by purvis on 2010-09-12
I had looked into and even began installing Ubuntu Server on a machine currently running W7-64. As the installation process proceeded it appeared it would not automatically set up dual boot on the machine, something I would like to have. As I began to search the web and this forum it looks like I may be better off installing a standard version of Ubuntu and add the necessary server add ins. Here is what I am wanting to accomplish:
-provide a central location for all computers to store and retrieve files
-provide a central location for all computers to back up configurations
-provide a central location for software installations
-compatibility across multiple platforms, Windows 7 64bit, Windows Vista 32 bit, Ubuntu 32 & 64 bit, Windows CE (U-Verse TV set top boxes), Wii, PS3
-ability for all systems to recognize media folders on server

My questions are:
-Can I do what I want using a standard version of Ubuntu?
-Would I be better off using Ubuntu Server?
-Should I use a 32 or 64 bit version?
-If I am using Ubuntu Server can I and how do I dual boot the machine?

---

### Post by Lukas666 on 2010-09-12
> **purvis said:**
> I had looked into and even began installing Ubuntu Server on a machine currently running W7-64. As the installation process proceeded it appeared it would not automatically set up dual boot on the machine, something I would like to have. As I began to search the web and this forum it looks like I may be better off installing a standard version of Ubuntu and add the necessary server add ins. Here is what I am wanting to accomplish:
-provide a central location for all computers to store and retrieve files
-provide a central location for all computers to back up configurations
-provide a central location for software installations
-compatibility across multiple platforms, Windows 7 64bit, Windows Vista 32 bit, Ubuntu 32 & 64 bit, Windows CE (U-Verse TV set top boxes), Wii, PS3
-ability for all systems to recognize media folders on server

My questions are:
1.Can I do what I want using a standard version of Ubuntu?
2.Would I be better off using Ubuntu Server?
3.Should I use a 32 or 64 bit version?
4.If I am using Ubuntu Server can I and how do I dual boot the machine?

1. Yes, with some extra packages.
2. Depends on how well you know Linux. If not so much then stick with the desktop version.
3. If your hardware supports 64bit then I say why not.
4. You would have to update GRUB after installing linux, not a big deal.

---

### Post by Nythain on 2010-09-12
> 
-Can I do what I want using a standard version of Ubuntu?

Yes. Anything you can do with server you can do with desktop after installing the right packages.
> 
-Would I be better off using Ubuntu Server?

If you are really new to Ubuntu, I'd actually recommend using a GUI (ie the Desktop version) until you familiarize yourself enough with the operating system, the command line, and the server tools you will be using.
> 
-Should I use a 32 or 64 bit version?

If you can 64, then 64
> 
-If I am using Ubuntu Server can I and how do I dual boot the machine?

It should add the windows install to GRUB if it detects a partition with Windows, or the Windows bootloader during installation. If you install windows after installing Ubuntu, then a simple fixing of GRUB should so the trick as mentioned already.

---

### Post by cgroza on 2010-09-12
If you run Ubuntu Server Edition you will save some resources because the regular Ubuntu uses extra resources for the Graphical User Interface.

---

