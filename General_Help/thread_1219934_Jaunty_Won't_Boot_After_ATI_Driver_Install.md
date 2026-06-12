---
title: "Jaunty Won't Boot After ATI Driver Install"
date: 2009-07-22
forum: General Help
---

### Post by RetroX on 2009-07-22
My graphics were working, fine but I figured I should install the official ATI drivers (Catalyst Control Center) anyways.  So, I did, it asked for a restart, and now it won't boot!

My Card: ATI Radeon 9000

When it boots, it shows the default Ubuntu splash, and then when it gets to file checking it switches to displaying text on the screen.  Then, when it goes to load the FireGL drivers, it freezes the screen with what I'm assuming is a random graphics dump, since it shows part of my desktop background with some noise and an inverted version of the Ubuntu splash.  It flashes twice, and then completely freezes.  It doesn't even show up with a terminal; it just freezes and prevents me from starting.  Is there a way to activate a terminal so I can uninstall the drivers and make it work again?  Or is there a way I can fix it from the live CD?  I'd prefer not to have to reinstall.

---

### Post by irv on 2009-07-22
When the bootup starts the grub, you can press the [Esc] key and go to the second option, Recovery mode. you can get to a menu where you can run a fix on your video. I think it is [Ctl] C or something like that. It will tell you on the terminal screen.

---

### Post by Soulfinger on 2009-08-04
I'm a brand new Ubuntu user and had exactly the same problem you describe today.

To fix I hit escape at boot up and dropped to command prompt

Then removed all fglrx drivers by typing:

**apt-get remove fglrx***

once removed I used **shutdown -r now** to restart and Ubuntu booted to desktop normally

---

### Post by features on 2009-08-04
Yup, the flgrx drivers are now incompatible with your card.  The last fglrx driver that was compatible (Catalyst 9.03) is incompatible with Ubuntu 9.04.

Your best bet is to use the open source ati drivers which should work quite well with you card.

---

