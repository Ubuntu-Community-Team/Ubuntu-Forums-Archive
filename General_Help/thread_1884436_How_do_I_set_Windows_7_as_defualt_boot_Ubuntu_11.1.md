---
title: "How do I set Windows 7 as defualt boot? Ubuntu 11.10"
date: 2011-11-21
forum: General Help
---

### Post by Tomween1 on 2011-11-21
I just installed Ubuntu 11.10 and have read many different threads on how to make windows the default boot. It appears when I try "sudo gedit /boot/grub/menu.lst" (as stipulated in many of the posts)and then enter the password, it automatically jumps to a box labeled menu.lst (/boot/grub)-gedit. from here I am lost. What steps are next to make windows boot first

Furthermore, at boot Windows7 is 6th in the list.

---

### Post by drs305 on 2011-11-21
menu.lst is from Grub legacy, which is no longer used.

I'd recommend installing Grub Customizer, a GUI app that can perform a variety of Grub 2 menu tweaks.

If you want to edit the Grub 2 files manually to set Windows as the default, the file to edit is /etc/default/grub. But you will have to learn a bit about Grub 2 to determine the default value.

Both have links in my signature line: "Customizer" and "Tasks".

---

### Post by Mark Phelps on 2011-11-21
When you go to do the configuration in Grub-Customizer, you will notice that there are two kinds of boot entry selections -- one kind says something about "position".

To have Win7 selected by default, do not choose the "position" entry; instead, scroll down the entry list and choose the one that says "Window 7 Loader on (xxx...".  That way, it will stay the default when new entries are added to GRUB through updates.

---

### Post by Tomween1 on 2011-11-21
Thank you both. I will attempt these steps and report back.

---

### Post by Quatrix on 2011-11-21
If you primarily use Windows, you could also remove the GRUB boot loader, add GRUB/Ubuntu to the Windows boot menu, and use that instead.

---

### Post by Mark Phelps on 2011-11-21
> **Quatrix said:**
> If you primarily use Windows, you could also remove the GRUB boot loader, add GRUB/Ubuntu to the Windows boot menu, and use that instead.

AFAIK, you can't do this unless you also install something like EasyBCD -- because that installs a version of GRUB into a Window partition, thus then allowing you to boot Ubuntu.

Given that GRUB is already there and working, changing the default boot selection using a GUI will be the least risky approach.

---

### Post by digithal on 2011-11-21
I also recommend you to use **[Startup Manager]("http://ubuntuguide.org/wiki/Ubuntu:Oneiric#Use_Startup_Manager_to_change_Grub_settings")**, the GUI tool.
Install it with:
```
sudo apt-get install startupmanager
```
The second way is to [**manually edit**](http://ubuntuguide.org/wiki/Ubuntu:Oneiric#GRUB_boot_manager_settings) the GRUB config.

---

### Post by Mark Phelps on 2011-11-21
Don't use Startup Manager.  It won't work with recent GRUB 2 versions.

Instead, use Grub-Customizer.  Link is below:

[http://ubuntuforums.org/showthread.php?t=1664134]("http://ubuntuforums.org/showthread.php?t=1664134")

---

### Post by Tomween1 on 2011-11-21
> **Mark Phelps said:**
> When you go to do the configuration in Grub-Customizer, you will notice that there are two kinds of boot entry selections -- one kind says something about "position".

To have Win7 selected by default, do not choose the "position" entry; instead, scroll down the entry list and choose the one that says "Window 7 Loader on (xxx...".  That way, it will stay the default when new entries are added to GRUB through updates.Mark, well it took me a while (work) but I have installed GC.... That's as far as I can get.... Don't understand the next steps.

BTW, though I want to solve 1 issue at a time, I've now found an issue that has started after installing GC - shut down only geta as far as Ubunuy shut down splash screen. I then have to hard shut down:confused:


EDIT: Well after a second and third reboot EVERYTHING is working. I'm confused though, all I did was install Grub-Customizer. Now it boots into Windows. I'm not complaining. I just don't understand why without having done any other steps.

---

### Post by drs305 on 2011-11-22
> **Tomween1 said:**
> EDIT: Well after a second and third reboot EVERYTHING is working. I'm confused though, all I did was install Grub-Customizer. Now it boots into Windows. I'm not complaining. I just don't understand why without having done any other steps.

It's possible that an automatic update occurred at some point. Some updates, such as an update to the kernel or to the Grub package itself, force an update of the boot files. Perhaps that is what happened.

In any case, I'm glad everything is now working.  :-)

---

### Post by Tomween1 on 2011-11-23
Thank you all.

Next step is to theme it to look and feel like OSX:D

---

