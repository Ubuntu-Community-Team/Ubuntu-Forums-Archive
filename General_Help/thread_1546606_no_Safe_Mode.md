---
title: "no Safe Mode?"
date: 2010-08-05
forum: General Help
---

### Post by Sduibek on 2010-08-05
Hi, i'm trying to reset the display resolution back to default as discussed here:
[http://ubuntuforums.org/showthread.php?t=674001](http://ubuntuforums.org/showthread.php?t=674001)
 
However I see absolutely no way to reach a "Safe Mode" from Xubuntu.
 
I can log in as an xterm session, but the command does nothing.
 
???:(

---

### Post by Rubi1200 on 2010-08-05
I think the person meant Recovery Mode which you should see as the second entry in your GRUB menu.

---

### Post by Sduibek on 2010-08-06
I don't have a GRUB menu :-/
 
When I boot up, it shows a black screen with white text (i.e. terminal commands loading the kernel i'd assume) briefly, then the Xubuntu logo briefly, then goes to the Login screen.
 
Here there is a drop-down for three session types, being Xfce, xTerm and the normal one, (xSession or something)

---

### Post by dacedos on 2010-11-05
Hi!

Could you start from Safe-mode?

I do not have grub either since I runs XUbuntu into a VirtualBox VM

---

### Post by philinux on 2010-11-05
> **Sduibek said:**
> Hi, i'm trying to reset the display resolution back to default as discussed here:
[http://ubuntuforums.org/showthread.php?t=674001](http://ubuntuforums.org/showthread.php?t=674001)
 
However I see absolutely no way to reach a "Safe Mode" from Xubuntu.
 
I can log in as an xterm session, but the command does nothing.
 
???:(

Immediately after the bios post hit the shift key to get the grub menu up.

You need to be quick.

---

### Post by azertyh on 2010-11-05
> **philinux said:**
> Immediately after the bios post hit the shift key to get the grub menu up.

You need to be quick.

nice to read that.

---

### Post by Jynks on 2010-11-07
> **philinux said:**
> Immediately after the bios post hit the shift key to get the grub menu up.

You need to be quick.

This dosn't seam to work... I get a text message saying "grub menu is loading" but it still boots directly into xubuntu...

I am trying to boot directly into the terminal.

---

### Post by Cheesehead on 2010-11-07
If you don't want to hose your GDM setup, it may be easier to simply wait for GDM to load, then CTRL+ALT+F2 or F3 or F4 etc. to access one of the existing TTYs.

If you do permanently want to get rid of GDM and go to a command-line-only system, another option is to simply uninstall everything that's not in the ubuntu-standard metapackage.

---

