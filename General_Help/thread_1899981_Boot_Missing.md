---
title: "Boot Missing?"
date: 2011-12-24
forum: General Help
---

### Post by Dallian on 2011-12-24
Hallo pple

I'm an Ubuntu user, nad it has worked just fine on my desktop but recently it doesn't boot, a black screen with some kind of verification and the text "(initframs)" [if i am not mistaken] waiting for some sort of command shows up instead. My dad told me that the boot is missing, the thing is, he doesn't know how to fix it. Any help would be great.

Thnx anywas pple, and happy new year =P

---

### Post by lisati on 2011-12-25
Quite possibly *not* a DE problem - the clue is the reference to "initramfs".....

*Thread moved to **General Help**.*

---

### Post by Rubi1200 on 2011-12-25
Hi and welcome to the forums Dallian :)

You need to boot the computer with a LiveCD/USB choosing to try not install.

Then follow the instructions in the link at the bottom of my post to run and post the results of the boot info script. 

It will hopefully tell us what is wrong and allow us to offer solutions.

---

### Post by West201 on 2011-12-25
As mentioned above you must use a live cd and run "sudo update-grub" in the terminal. If this doesn't work, post your grub.conf file so we can review it. /boot/grub/grub.conf

---

