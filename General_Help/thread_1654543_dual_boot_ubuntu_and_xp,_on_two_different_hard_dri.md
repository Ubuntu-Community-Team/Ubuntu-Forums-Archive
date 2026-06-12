---
title: "dual boot ubuntu and xp, on two different hard drives?"
date: 2010-12-28
forum: General Help
---

### Post by ohVaNiLLaGoRiLLa on 2010-12-28
I have just installed ubuntu 10.04 and when writing it to my d drive I disconnected my c drive(which has xp on it) so i could not accidentally overwrite it. But now I am having the issue of having the dual boot option appear when i start up my computer. Looking into this problem i found that upon install it is suppose to see that there is an xp drive and configure grub to dual boot to give the option of ubuntu or xp.  But since i removed my xp drive it did not see it.. how do i fix this so that it gives me the choice at start up to run either windows xp or ubuntu?

---

### Post by K.J. on 2010-12-28
Since each drive has it's own boot loader, one option is to select the startup disk at boot. For example, on the machine in front of me, if you hit F12 at boot, you have the choice of which hard drive to boot from.

The second option is to add XP to the grub boot loader:
Open your grub configuration and add:
```
title Windows
map (hd0) (hd1)
map (hd1) (hd0)
root (hd1,0)
chainloader +1
```
Then run "sudo update-grub"

---

### Post by ohVaNiLLaGoRiLLa on 2010-12-28
oh! alright. But how to i get to the grub to edit it D: i know.. im a no0b.

edit: never mind haha i got it. thanks!

---

