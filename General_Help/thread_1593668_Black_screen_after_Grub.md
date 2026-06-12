---
title: "Black screen after Grub"
date: 2010-10-11
forum: General Help
---

### Post by Me Mechant on 2010-10-11
Hi everyone,

I have been using ubuntu 10.04 64 bits for about 3 month and every time i got a problem i always found my answer on this forum, but this time i really dont know what to do.

Today i change my keyboard layout, so i want to test if everything is ok so i reboot my computer. When i try to reboot everything is as usual but the problem is that after grub....nothing only a black screen no matter what i do. I doubt the keyboard layout change something but who knows...

I really don't know what to do to fix this...

I run AMD phenom 940 X 4, 4 gig ram, Ati radeon HD 4870, 

I would appreciate if someone could assist me here !

Thank You

---

### Post by oldfred on 2010-10-11
I have not messed with xorg for ages but keyboard settings were in the xorg.conf file which also has video settings. I thought they essentially obsoleted xorg except for special cases.

Take a look at your /etc/xorg.conf from liveCD probably in /media/etc/xorg.conf so you do not get the one on the cd. See if you have a backup. if so try renaming it and change to run the backup file.

---

### Post by Me Mechant on 2010-10-11
Can i use the xorg file from my laptop? I try searching for it but i dont find it.

I have been able to boot the computer from a very old recovery mode in grub but my screen color is a mess but i'm able to use it, could i try changing the xorg file this way?

Thank You

---

### Post by Me Mechant on 2010-10-11
I boot the computer using the recovery mode and i put back the keyboard layout like he was before the crash. Everything is fine now !

Thanks All!

---

