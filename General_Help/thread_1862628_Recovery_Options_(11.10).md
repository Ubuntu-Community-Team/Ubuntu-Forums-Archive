---
title: "Recovery Options? (11.10)"
date: 2011-10-16
forum: General Help
---

### Post by cj_g0bl1n on 2011-10-16
I've been using 11.04 for a while and upgraded to 11.10.  I prefer the classic gnome desktop, so I installed it.  Later I decided to get rid of it, so I did this:
```
sudo apt-get remove gnome-panel
sudo apt-get remove gnome-session
sudo apt-get remove gnome-shell
```
When I shutdown my computer and came back to it a little later I noticed that I do not have any options to log in anymore (I get to the login screen, but when I click the gear to switch between unity and unity 2d there are no options).  When I type in my password and press enter I just come back to the login screen.  All my files are encrypted.  I would like to either fix the 11.10 install or get to my home folder so I can transfer them to an external hard drive and reinstall Ubuntu.  I'm more of a Windows user than a Linux user, but I've been using Ubuntu as my main computer for a few months now, so I have some experience in using it.  Can anyone help me out?  I have a big programming project due tomorrow that happens to be sitting on my encrypted desktop...  So I'd really like to just access the home folder as soon as possible!!!

---

### Post by hwttdz on 2011-10-16
Alt+ctrl+f2 should get you to a terminal from which you can install a desktop (one of the gnomes, xfce, enlightenment, kde, lxde....).

---

### Post by cj_g0bl1n on 2011-10-17
That's just what I needed!

Thanks!

---

### Post by fixerdave on 2011-10-17
Cntrl-alt-F1 (to F6) will bring up command-line consoles - Cntrl-Alt-F7 will switch back to the X-session.  A handy thing to know... saved me on my 11.10 install.

---

