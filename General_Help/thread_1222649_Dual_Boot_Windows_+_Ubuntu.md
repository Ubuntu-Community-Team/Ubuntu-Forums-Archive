---
title: "Dual Boot Windows + Ubuntu"
date: 2009-07-25
forum: General Help
---

### Post by LinuxLoverX2 on 2009-07-25
I have Windows Vista pre-installed on the harddrive and when I install Ubuntu on the same harddrive in another partition the grub loader doesn't show up on the next reboot instead, Windows Vista boot automaticly without the menu which let me choose which operation system to boot . what is the solution for this problem ? I want dual booting on startup

---

### Post by DeMus on 2009-07-25
> **LinuxLoverX2 said:**
> I have Windows Vista pre-installed on the harddrive and when I install Ubuntu on the same harddrive in another partition the grub loader doesn't show up on the next reboot instead, Windows Vista boot automaticly without the menu which let me choose which operation system to boot . what is the solution for this problem ? I want dual booting on startup

How did you install Ubuntu? Did you use Wubi, or just a normal install?
When it's the last, at the end of the installation, you can choose to install Grub. Also where to install it. Make sure you installed it on the MBR of the first hard disk you have. That way the Grub menu should load at boot.

---

### Post by LinuxLoverX2 on 2009-07-25
> **DeMus said:**
> How did you install Ubuntu? Did you use Wubi, or just a normal install?
When it's the last, at the end of the installation, you can choose to install Grub. Also where to install it. Make sure you installed it on the MBR of the first hard disk you have. That way the Grub menu should load at boot.

I installed Ubuntu with normal installation and about the end of installation I didn't press the button advanced and changed any thing there I guess I have used the defult settings , how do I know the first hard disk ? I have two hard disks and how to instal grub in MBR Explain please if you don't mind :P

---

### Post by merlinus on 2009-07-25
Look in bios for booting order of your hdds.  Generally you press an F key (or Escape or Del)  to enter setup right after startup.  Your system docs have this info, or google for computer model.

---

### Post by Quarkrad on 2009-07-25
I dual boot Ubuntu and XP - this is a great site that showed me how to do it.  This link is for dual booting Linux/Ubuntu and Vista when vista is loaded first.

[http://apcmag.com/how_to_dualboot_vista_with_linux_vista_installed_first.htm](http://apcmag.com/how_to_dualboot_vista_with_linux_vista_installed_first.htm)

Page 4 explains about setting up the boot loader.  Hopefully this will help.

---

