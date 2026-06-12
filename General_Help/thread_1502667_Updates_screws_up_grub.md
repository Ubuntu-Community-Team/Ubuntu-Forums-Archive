---
title: "Updates screws up grub?"
date: 2010-06-05
forum: General Help
---

### Post by kcredden on 2010-06-05
Hey folks: Both my netbook and this machine needs an update (according to the update manager) Well 2 days ago, I let it update the netbook. Bad mistake. Long story short; it installed a new kernel, and monkeyed with GRUB (v1.5) and it wouldn't boot. It's that new grub thing, with the long cryptic numbers/letters string, instead of the more normal hd0, hd1 thing. I had no clue on how to restore it. 

How can I back up GRUB next time, let it update, then restore grub back the way it's suppose to work? I tried backing up the menu.lst file, but that didn't work. I backed up, and restored it, and the netbook still wouldn't boot. Got the very same error message. I had to do a partimage to bring back the old image of it. Also Grub-install will not work at all, from systemrescueCD. 

Is there some sort of up-to-date tutorial on Grub? I've had more problems with Grub than anything dealing with linux. Especially since anything happens to it, your virtually screwed. 

Help!

- Kc

---

### Post by mikewhatever on 2010-06-05
It's a pity you didn't post some info related to the problem before restoring from the backup. Generally speaking, when the kernel is updated, the new one gets added to the menu.lst and becomes the default one. Is that Hardy Heron we are talking about?
If something like that ever happens again, boot from a live cd and post the following info:

contents of menu.lst /etc/fstab
whatever error messages you get

---

