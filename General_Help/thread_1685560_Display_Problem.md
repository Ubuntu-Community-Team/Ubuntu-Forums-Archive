---
title: "Display Problem"
date: 2011-02-10
forum: General Help
---

### Post by safeside on 2011-02-10
I am using ubuntu 10.10, my problem is with the display.  I had a functional installation, installed about a month ago.  I am using then and now an ATI radeon 3450 video card, with a samsung 23 in monitor.  Everything was acceptable, then I selected new hardware drivers, and then... the GUI does not load.  I receive a text login, a text password and then it appears I am still in the terminal mode.  I need some help to, get my display back, I can load liveCD but, I do not know what to do, to correct this.

Thanks

---

### Post by jerrrys on 2011-02-12
lets assume you have xorg backed up
pull up a terminal and enter

sudo dpkg-reconfigure xserver-xorg

---

### Post by safeside on 2011-02-12
I guess, I didn't have a back-up.  I ran the command and also via liveCD, nothing changed.  Can I copy from the liveCD?  I am trying to learn this OS and in so doing, I mess up a lot.

---

### Post by jerrrys on 2011-02-12
you say the GUI will not load

do a
sudo gdm

---

### Post by safeside on 2011-02-12
The grub2 loads, I also get the Ubuntu splash screen...then, I get text mode, with login and password.

I entered the command "sudo gdm".  The results were "gdm binary: 1505, failed to acquire org-gnome" plus "1505 could not acquire name: bailing out".

What have I done?

---

### Post by jerrrys on 2011-02-13
lets reset xorg
sudo dpkg-reconfigure -phigh xserver-xorg

---

### Post by safeside on 2011-02-13
I tried the commands to reset the display, both livecd and when it boots to text mode.  Neither seemed to change the display

Thanks for your help

---

### Post by jerrrys on 2011-02-13
sorry i couldn't

---

