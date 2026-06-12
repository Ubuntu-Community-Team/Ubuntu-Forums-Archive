---
title: "HAL Internal Error!"
date: 2009-08-11
forum: General Help
---

### Post by bradley120 on 2009-08-11
I start up Ubuntu and then a message box pops up saying "Internal error!" "HAL failed to initialize!" Please help me! I'd love to use ubuntu but can't! By the way, my mouse AND my keyboard dont work when I try to do anything!

---

### Post by P4man on 2009-08-12
does that happen when you boot the live cd ?

---

### Post by aYs-Halo on 2009-08-27
sry for digging this one up, but i have the exact same problem here.

and to answer your question: it happens on regular boot. everytime. no clue what i've done (actually i cant remember doing anything but watching tv on this thing ...)

let me know if u need to know anything else..

---

### Post by P4man on 2009-08-27
Can you boot in recovery mode from grub?

---

### Post by aYs-Halo on 2009-08-27
Yes.
If i skip it, i'll get the hal error message again...

I have done the fsck, and grub thing; dpkg fails.

By the way, my remote control still does work (while my mouse and keyboard are not). if that helps.

---

So here is how i "solved" it:
I wanted to get all the "[fail]"s in the boot up cleared up, so i started with the first one occuring, which was
"cannot initialize /etc/mtab"

Google on that lead me to the following [https://answers.launchpad.net/ubuntu/+question/45581](https://answers.launchpad.net/ubuntu/+question/45581)
So i did "sudo touch /forcefsck" from recovery mode... 

On the next reboot "fsck died with exit status 1"...

and then everything worked again. Apparently (and hopefully) it just was some error on my hard disk. If not, you'll hear from me ;)

Oh and thanks very much anyways for giving me the clue with the recovery mode :) (serious)


regards, Halo

---

