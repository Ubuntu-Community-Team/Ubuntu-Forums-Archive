---
title: "Help! I've installed Ubuntu and I don't know how to boot into Windows again!"
date: 2012-08-20
forum: General Help
---

### Post by mmob18 on 2012-08-20
So I have all my stuff(Windows) installed onto Drive C. I installed Ubuntu onto Drive M. 

All my stuff is on Drive C, I can see it in Ubuntu. But I don't know how to boot into windows!

Please help! 

-mmob18

---

### Post by mkstallings1 on 2012-08-20
While in Ubuntu, open a terminal and type:

sudo update-grub

Reboot and see if windows shows up in your GRUB menu

---

### Post by Mark Phelps on 2012-08-20
> **mmob18 said:**
> So I have all my stuff(Windows) installed onto Drive C. I installed Ubuntu onto Drive M. 
Linux doesn't use drive letters for installation.  So, if you really did install into "Drive M", then you would have had to install from INSIDE Windows -- which then makes this a Wubi installation -- which does not use GRUB.

---

