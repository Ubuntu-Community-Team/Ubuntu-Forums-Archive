---
title: "Windows xp beside Linux ubuntu On boot screen doesn't work"
date: 2010-12-03
forum: General Help
---

### Post by Wayne1987 on 2010-12-03
Yes, I've been trying to get Windows xp and Linux Ubuntu installed on my computer in the boot screen to pick from one but Linux ubuntu works but Windows xp won't even boot.

I just sets there 

_   <----- With a little line like that just blink for hours and nothing happens I end up just pulling the power plug to restart the system back into Linux because the side by side Install didn't work.

There was software, that should allow me to do this but I forgot what it was, software that would allow me to set Linux ubuntu in the boot screen .

any ideas?

---

### Post by galvatron408 on 2010-12-03
assuming that your XP isn't already hosed, you could run grub-mkconfig to generate a new grub config file.

It's a neat tool that automatically searches your partitions for bootable partitions and build a new menu for you. you'll need to replace your existing grub.cfg with the new output though.

---

### Post by Rubi1200 on 2010-12-03
Before attempting to reinstall or fix anything, I suggest you boot the computer with a LiveCD.

Then, click on the link at the bottom of my post and run the boot info script (instructions included).

Post the results back here please so we can see what is where; it will make offering solutions a lot easier.

Thanks.

---

### Post by Wayne1987 on 2010-12-03
Still trying to do Dual Booting, I'm downloading 
**Gnome Partition Editor**

The advice that was given first was wrong, being I must run as root and well I don't know how .

---

### Post by Wayne1987 on 2010-12-03
Didn't work...
pffft ..

---

