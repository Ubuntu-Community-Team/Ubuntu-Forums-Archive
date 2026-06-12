---
title: "how to boot unbuntu by default?"
date: 2011-10-22
forum: General Help
---

### Post by addam303 on 2011-10-22
hi I want to make unbuntu my default boot, it keeps going to windows 7 64bit.. I also want to change the boot time to about 2-3 seconds

I also already tried the menu.lst command through terminal and it showed me a blank document. Please help. 

and is there a way to edit docx documents? what's the closest software to word?

---

### Post by addam303 on 2011-10-22
when typing the code (gksudo gedit /boot/grub/menu.lst) into terminal i get the following messages:
> (gksudo:8871): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(gksudo:8871): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(gksudo:8871): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(gksudo:8871): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

Then a menu.lst file opens but it's blank, as well as another blank document. when closing it, it asks if i want to save. I select no. then on the terminal I get the following messages:

> (gedit:8873): Gtk-WARNING **: Attempting to store changes into `/root/.local/share/recently-used.xbel', but failed: Failed to create file '/root/.local/share/recently-used.xbel.S4FW3V': No such file or directory

(gedit:8873): Gtk-WARNING **: Attempting to set the permissions of `/root/.local/share/recently-used.xbel', but failed: No such file or directory

---

### Post by ajgreeny on 2011-10-22
[LIST=1]
[*]What version of ubuntu are you using?
[*]How did you install ubuntu;  did you do it from a running Windows 7  with wubi?
[*]The file **/boot/grub/menu.lst** has not been used since ubuntu 9.10 when grub2 replaced legacy grub.  Now in grub2 the equivalent file is **/boot/grub/grub.cfg** which is a read-only file and not to be edited as menu.lst could be.  Changes to that are made by editing other configuration files,  **/etc/default/grub** or the files in **/etc/grub.d**
[*]The error messages you see are not too important so don't worry about them.
[*].docx files are easily opened by the versions of OpenOffice or LibreOffice, and also Abiword, all of which are now included in ubuntu's repos.
[/LIST]

---

### Post by utnubuuser on 2011-10-22
and an easy way to change your menu/booting preferences is with startupmanager

> sudo apt-get install startupmanager

then run it from top panel System>>Administration>>Startup Manager

---

### Post by bcbc on 2011-10-22
> **addam303 said:**
> hi I want to make unbuntu my default boot, it keeps going to windows 7 64bit.. I also want to change the boot time to about 2-3 seconds

I also already tried the menu.lst command through terminal and it showed me a blank document. Please help. 

and is there a way to edit docx documents? what's the closest software to word?
Don't make Ubuntu the default if you installed with Wubi (which you most likely did if it defaults to Windows). At least without being aware of some issues.

For whatever reason, the windows boot manager doesn't 'show up' when the timeout is low (I've heard reports that 5 seconds and less don't pop it). The default is set to 10 when you install with Wubi and you should leave it at that. 
If you do set Ubuntu as the default, and the boot manager doesn't show, then you can't boot windows (and you need a windows repair disk to fix it).

---

