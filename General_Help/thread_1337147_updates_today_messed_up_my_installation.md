---
title: "updates today messed up my installation"
date: 2009-11-25
forum: General Help
---

### Post by zero7404 on 2009-11-25
this morning i was greeted with updates from update manager. noticed there was a newer kernel, did the updates, then restarted.

after restart, the new login was not loading as X Server (the GUI login), instead it loaded in terminal mode, but was also flickering.

i reverted back to a previous image backup i did with clonezilla. i use Nvidia's 190.42, as opposed to the recommended version 185. perhaps this had cause the problem i experienced.

or perhaps one of the updates overwrote some settings that caused it.
regardless, i'll refrain from updating for the next few weeks.

---

### Post by juicehill on 2009-11-25
Although i do not get this flickering -- I too cannot boot into my linux install after this morning's updating.

I have this new .15 kernal showing in my grub, i have tried booting in .14 and .15 and .15 recovery mode. Everytime I attempt to boot, the system hangs at the first splash screen before the brown loading screen.  Irked only begins to explain how i feel.

In recovery mode it stops after detecting my usb devices, i'm not sure how to continue.

---

### Post by sdowney717 on 2009-11-25
same issue here, no gui with kernel 2.6.31-15, just a login prompt.
I am running nvidia 190 drivers

[https://bugs.launchpad.net/ubuntu/+bug/488148](https://bugs.launchpad.net/ubuntu/+bug/488148)

login and add to the bug list

---

### Post by zero7404 on 2009-11-25
clonezilla saved me the trouble of fixing this manually....<thankful>

---

### Post by zero7404 on 2009-11-25
i wonder if the devs know about this problem....or if anything has been done about it ? i like to keep my system updated, but am refraining here for verification that the updates have been corrected to avoid botching up the OS ?

---

### Post by zero7404 on 2009-11-28
bump....any updates on these updates ?

---

