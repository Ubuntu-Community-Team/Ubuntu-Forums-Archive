---
title: "My Ubuntu computer instead of starting up is showing the cursor being busy......?"
date: 2009-08-25
forum: General Help
---

### Post by princeayo on 2009-08-25
I was fiddling around with my pc and to be honest, I do not remember what I clicked on during the process, but I remember accessing something from right clicking on the desktop as I was trying to rearrange my stuff on it. I wasn't successful in the end.

After switching it off and back on, instead of it starting up as normal what I see is the cursor showing as busy, which funny enough is working when I move it around with my mouse. It is as if it is doing something but I have left the pc on for almost 24 hours and no change. It shows at almost at the very beginning as a small circle and dots running round in it. This is even before I have the opportunity to log into my account on the pc. 

Could anyone please advise me on what I can do. I only see a blank dark screen, with my cursor seemingly working away in the middle of it.

Please help

---

### Post by hwttdz on 2009-08-28
I might suggest booting into a recovery mode from the grub menu.  That would get you a prompt and you could see what's going on.  dmesg would be a good place to start looking for errors.  

Possibly putting in the live cd and getting a prompt that say and see if you can update/upgrade or dpkg --configure -a

---

### Post by P4man on 2009-08-28
when you get that busy cursor, press control alt F1. Does it bring you to a terminal ? Can you log in there?

If so, as princeayo suggested, run "dmesg" to look for clues.
try "sudo dpkg --configure -a" to repair a broken upgrade

If control alt F1 doesnt work, run the same commands  in recovery mode: Press escape at the grub menu, select "recovery", then select a root shell.

BTW, you can't run those commands from a livecd without chroot, you would just apply them to the live session.

---

