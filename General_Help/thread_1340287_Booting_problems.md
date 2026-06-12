---
title: "Booting problems"
date: 2009-11-28
forum: General Help
---

### Post by Montebest on 2009-11-28
I use GRUB to dual boot with windows Media center edition.
the screen that i choose what os to boot on has do ubuntu versions shown, the two ubuntu options read the same until the very last decimal of their version number (.15 and .14 respectively). i can boot to .14 fine. however if i boot to .15 it shows the white circle and then goes to a flashing full screen terminal. the screen flashes about twice a second and i can only provide input to the terminal when something is displayed, so as of yet i am unable to login. when i start from .15 recovery mode i get the same thing without the flashing screen or dodgey input, but i still cant start the x windows system.
HELP!!!!!!!!!!!!

---

### Post by Montebest on 2009-11-28
please help

---

### Post by DiscoStu570 on 2009-11-28
I'm having the same problem.  I don't have a dual installation or anything, so I don't think its related to that.  After yesterday's system updates, now I can't log in, I get the same blinking terminal screen as the OP.

Sad thing is I remember having had this problem when I originally upgraded to Karmic and I don't recall how I fixed it.

If anybody can step in with a solution it'd be much appreciated, as it would save my saturday afternoon.  Otherwise I'll post back if and when I remember how I solved this last time.

---

### Post by john newbuntu on 2009-11-29
If you can get into the .14 version, I think you should be fine.  Then try these from a terminal:
sudo apt-get update.
sudo apt-get install linux-image-2.6.31-15-generic

---

