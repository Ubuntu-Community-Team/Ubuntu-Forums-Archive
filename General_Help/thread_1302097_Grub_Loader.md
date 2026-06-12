---
title: "Grub Loader"
date: 2009-10-26
forum: General Help
---

### Post by Howgil on 2009-10-26
I have been running Ubuntu 804.3 in a dual boot with Windows XP on a Dell desktop with no problems.  Recently a large number of updates were downloaded and installed.  Since then Windows XP no longer appears as an option on the Grub screen.  At the bottom of the box there is the line "Other Operating Systems:", but where there used to be "Windows XP" there is nothing.  I need to boot into Windows to recover some files.  Is there a way to do that?  Thanks.

---

### Post by arrrghhh on 2009-10-26
First, you can access all your WinXP files from Ubuntu - just an FYI.

Second, did you put that WinXP entry in your GRUB manually?  Or was it created for you when you installed GRUB?  I made the mistake of moving my Windows entry on my father's computer, as he wanted to pick Windows by default... however, I placed the entry inside the "automagic" section in the menu.lst, and in the next GRUB (well, actually kernel) update, the entry for Windows was removed... d'oh!

---

### Post by cwbar_1 on 2009-10-26
If you just want to recover files on the windows partition, Places > ??? GB Filesystem should allow you access to your files.   If you need to repair your Grub, then  "sudo update-grub"  in  Applications > Accessories > Terminal

---

