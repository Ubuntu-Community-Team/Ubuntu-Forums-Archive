---
title: "Must hold control button for ubuntu netbook to load."
date: 2010-12-15
forum: General Help
---

### Post by Aldinger on 2010-12-15
Just installed Ubuntu 10.10 Netbook remix on Toshiba nb305.  Everything works fine but I must hold down control or nothing will load.  It will not boot unless I hold down control.  If I open a new application it won't start loading unless I hold control.  It is like everything is on pause unless I hold down the control button.

---

### Post by gnoel on 2011-01-16
Same thing is happening to me.  I have the 10.10 desktop version (not netbook) installed in a dual boot with Windows 7 on a Toshiba NB310.

The problem happens during boot (whether from hard drive or USB stick), also when running anything in Terminal.  The computer seems to enter sleep mode after 1-2 seconds of activity.  Holding down the control or shift key, or budging the cursor with the trackpad, is the only way to force the system to run.

I checked BIOS settings and played with the Wake on LAN and Wake on Keyboard settings to no apparent effect.

Any clues, please???

---

### Post by gnoel on 2011-01-16
Found Solution on another thread!

Open the terminal, now do this: 

1) sudo gedit /etc/default/grub
2) Change: GRUB_CMDLINE_LINUX_DEFAULT="splash nohz=off highres=off"
3) sudo update-grub (I don't know if I had to do this.)
4) restart computer

This is also the solution to the problem of the screen unable to wake from sleep mode.

---

### Post by kegsofduff on 2011-01-22
Thank you so much for this.  I just got an Acer 1551 and have been looking for a way to get the display to turn back on after waking from suspend. :)

---

