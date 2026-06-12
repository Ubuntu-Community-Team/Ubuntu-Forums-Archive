---
title: "grub boot menu instead of windows boot"
date: 2009-11-28
forum: General Help
---

### Post by phillychease on 2009-11-28
hi i have both windows xp and ubuntu 9.1 installed.
when i turn on my computer, it shows the windows boot menu and then i have to select ubuntu and then it will show the grub boot menu.
my question is how do i make the grub boot menu show first?
step by step instructions? im pretty noob at this. :D

---

### Post by phillychease on 2009-11-29
anyone?

---

### Post by Sin@Sin-Sacrifice on 2009-11-29
You have Windows boot loader on one hard drive and grub on another? You can install grub into the MBR of the first drive and it will ONLY be grub where you can still select either OS. A Google search for "install grub" will get the info for you. Same with LILO if you'd rather use it.

---

### Post by garvinrick4 on 2009-11-29
Did you have a Wubi install at one time and left the WUBI in the windows dos4grub.  bcdedit and see if there is one there with
a WUBI in it.  Easy to edit out if it is. That is a windows prompt
command of course.  bcdedit /delete { ID #        }    

Google the edit so I have the spacing right. But it does sound like
you have WUBI attached to your boot menu.

---

### Post by garvinrick4 on 2009-11-30
You can install Start-up Manager and change the boot order if that is what you are looking
for. 

sudo apt-get install startupmanager


That is command at Terminal or you can find it in system tools in Ubuntu software center.

Any which way you want but you can change boot order from there. 

If you did have a WUBI install previously or now let me know.

---

