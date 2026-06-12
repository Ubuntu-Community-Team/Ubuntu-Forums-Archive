---
title: "how to get a tty?"
date: 2010-07-17
forum: General Help
---

### Post by Duckslammer on 2010-07-17
Hi, after using xubuntu for years I decided to try ubuntu.  Today  Installed 10.04.

I can't seem to get a tty console.  Ctl-Alt-fkey  gets me a blank screen.  So does chvt.  If I kill gdm, I get a blank  screen, alt-fkey doesn't work, ctl-alt-fkey doesn't work, no way to  restart X so I have to power cycle.

This works properly in  xubuntu 10.04 but it didn't work in 9.04.

Looking in /dev the  devices are all there.  The tty 7, 8, and 9 files have perms 650 (though  8 and 9 don't work for me either) and tty files 1 through 6 have perms  600.  I tried changing the perms but no luck.

Is there something I  have to set up or enable?  Could this be a video driver problem?  Any  suggestions?

---

### Post by dino99 on 2010-07-17
into /etc/default/grub

remove vga=xxx if exist (sudo gedit /etc/default/grub)

then sudo update-grub

you might check the third level settings into keyboard config (system pref keyboard)

---

### Post by coldraven on 2010-07-17
It works for me in 10.04.on a Compaq 6715b laptop
Ctrl-Alt-F1 gives a tty login
Ctrl-Alt-F7 goes back to Gnome desktop.
Sorry I'm not able to offer any suggestions why yours doesn't :(

Re: Possible video driver problem. 10.04 definitely does not like some older Intel integrated chipsets and I don't think there is a fix other than installing a prior version. 8.04 for example.

---

### Post by digitalcitizenx on 2010-07-17
> **coldraven said:**
> It works for me in 10.04.on a Compaq 6715b laptop
Ctrl-Alt-F1 gives a tty login
Ctrl-Alt-F7 goes back to Gnome desktop.
Sorry I'm not able to offer any suggestions why yours doesn't :(

Same here.

Could be a corrupted upgrade or install.

Back up /home and reinstall 10.04.

Good luck.

---

### Post by Duckslammer on 2010-07-17
> **dino99 said:**
> into /etc/default/grub

remove vga=xxx if exist (sudo gedit /etc/default/grub)

then sudo update-grub

you might check the third level settings into keyboard config (system pref keyboard)

Ok, /etc/default/grub has the following (uncommented) lines:

GRUB_DEFAULT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""

I don't know what a third level setting is but there's nothing in the keyboard config to do with a tty.  I have a generic pc keyboard.

---

