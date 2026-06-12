---
title: "Ubuntu VGA mode not supported?"
date: 2011-07-19
forum: General Help
---

### Post by dhinesh123 on 2011-07-19
I have sucessfully installed ubuntu 11.04 (32-bit).. When rebooting system my monitor says **VGA mode not supported  **? 

how can i get out of this?

---

### Post by nicedreamer on 2011-07-19
> **dhinesh123 said:**
> I have sucessfully installed ubuntu 11.04 (32-bit).. When rebooting system my monitor says **VGA mode not supported  **? 

how can i get out of this?

Edit file /boot/grub/grub.cfg ,drop vga=791 or some other number.

---

### Post by dhinesh123 on 2011-07-19
> **nicedreamer said:**
> Edit file /boot/grub/grub.cfg ,drop vga=791 or some other number.

i have installed no other operating system?
  so  whic key i need to press to enter grup menu to edit this file?

---

### Post by Mark Phelps on 2011-07-19
You have to open gedit in root mode with the filename, as in "gksudo gedit /boot/grub/grub.cfg".  But that's not the problem.

The problem is that it's a BAD idea to edit grub.cfg -- it even has text in there telling you NOT to edit it.  This file is GENERATED automatically and, whenever you do a kernel update, it gets completely overwritten.

The file you SHOULD edit is /etc/default/grub -- to remove the "vga=xxx" entry.  It's attempting to force a display mode that, apparently, is not supported.

When done editing that file, enter "sudo update-grub" in the terminal.  That will regenerate the grub.cfg file.

---

### Post by samigina on 2011-07-19
Ey Mark, the OP seems like cant boot to the system, hes stuck with the VGA problem.

I guess you can see the grub loading. If not, try holding the SHIFT key while booting, it may show you the grub menu, there you can edit a menu entry typing "e", there simply remove the vga=xxx that Mark suggested, also you can try adding "nomodeset" at the end of the line.

---

### Post by Mark Phelps on 2011-07-19
OK ... then if you can't actually boot into Ubuntu, you can do the following:
1) Boot from an Ubuntu LiveCD
2) Select the Try mode, not Install
3) Wait a LONG time for the desktop to (eventually) appear
4) Click on the "home" icon in the left side and select the entry for the Ubuntu partition. That will cause that partition to be mounted.
5) Open a terminal, enter "sudo -i", supply the password.

Since you're only trying to debug the problem, it is OK to make interim changes ... so edit grub.cfg and do the changes.

Reboot.  See if you now are able to get past the vga mode error.

---

