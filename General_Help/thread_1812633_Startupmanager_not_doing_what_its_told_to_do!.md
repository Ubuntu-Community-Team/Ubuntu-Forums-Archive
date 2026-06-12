---
title: "Startupmanager not doing what its told to do!"
date: 2011-07-26
forum: General Help
---

### Post by NoSuchDevice on 2011-07-26
Hey guys, 

So I got Ubuntu 11.04 today, and I used Startup Manager to change the default OS to Windows 7, and gave in two seconds wait time, however it still boots up in to Ubuntu, whats the problem here...?

I don't use Ubuntu very much so keep this something simple, so I can understand..:D

Thanks

---

### Post by Mark Phelps on 2011-07-26
I've used startup-manager for a while, and only recently discovered that it no longer works with the recent GRUB updates.

GRUB v1.99RC introduced nested kernel stanzas in the generated menu, and startup-manager apparently can not handle those properly.

One way to fix this (which is what I did) is to manually edit the GRUB files to force this, as follows:
1) Using a terminal and Gedit, open the /boot/grub/cfg file.  Look for the line containing something like "Windows 7 (loader) on ..."
2) Using another terminal, enter "gksudo gedit /etc/default/grub
3) Find the line that has "DEFAULT=" with a number
4) Copy the "Windows loader ..." text from the cfg file into the grub file.  Line should say something like "DEFAULT="Windows 7 (loader) ..."
5) Save the edited grub file
6) Enter "sudo update-grub"

The NEW Grub menu file will have an entry in the default area for Windows 7 now.

---

### Post by oldos2er on 2011-07-26
I'd recommend you use grub-customizer, [https://launchpad.net/grub-customizer](https://launchpad.net/grub-customizer)
Startupmanager has never been fully updated to work with grub2.

---

