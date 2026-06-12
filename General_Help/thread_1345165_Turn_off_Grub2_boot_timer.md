---
title: "Turn off Grub2 boot timer?"
date: 2009-12-03
forum: General Help
---

### Post by isee on 2009-12-03
Is it possible to turn off the boot timer in Grub2, or set it for more than 100 seconds?

In 9.04, i edited /boot/grub/menu.lst, but I don't see that file anymore.

Thanks!

---

### Post by rbc on 2009-12-03
Have a look here, under the section entitled Timed Display, although you'd probably do well to read the entire thing

[https://help.ubuntu.com/community/Grub2#Timed%20Display](https://help.ubuntu.com/community/Grub2#Timed%20Display)

---

### Post by isee on 2009-12-04
Thanks for your reply rbc.

I don't understand this line from the link, the end where it says "is has" needs an edit I think.
> The default entry is determined by the ***DEFAULT=*** setting in */etc/default/grub*; the first "menuentry" is has a value of "0" I can set Timeout in */etc/default/grub*, but if I put a # in front of it like I did for 9.04's Timeout in */menu.lst* it doesn't work the same, although it does have an effect.

I can't tell if it's related to the ***DEFAULT=*** setting being set to 0.  Where it says "The default entry" that is a little too ambigous for me.

---

### Post by wilee-nilee on 2009-12-04
Startup manager in synaptic will do what your looking for, but I have never seen anybody try to add 100 min I don't think your serious there now are you?

---

### Post by isee on 2009-12-04
Hi wilee-nilee

100 *Seconds *(not minutes) is the maximum time that can be set through Startup Manager.  The option to disable the Timer is not in the Startup Manager for Grub2,

I want to be able to reboot and leave my computer, maybe 2 min, maybe 20 min, without having a timer countdown and auto-boot.

I have this on my XP/9.04 dual-boot desktop which has origional Grub, like I said I edited /menu.lst with a #.  This disables the timer in Grub, but not Grub2.

---

### Post by wilee-nilee on 2009-12-04
> **isee said:**
> Hi wilee-nilee

100 *Seconds *(not minutes) is the maximum time that can be set through Startup Manager.  The option to disable the Timer is not in the Startup Manager for Grub2,

I want to be able to reboot and leave my computer, maybe 2 min, maybe 20 min, without having a timer countdown and auto-boot.

I have this on my XP/9.04 dual-boot desktop which has origional Grub, like I said I edited /menu.lst with a #.  This disables the timer in Grub, but not Grub2.

Sorry I miss read the 100 thangy, personally this sort of need doesn't apply to me. It should be available in some way for people who want to though without having to be a extreme geek to do it.

---

