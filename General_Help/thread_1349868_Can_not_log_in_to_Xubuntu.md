---
title: "Can not log in to Xubuntu"
date: 2009-12-08
forum: General Help
---

### Post by s1mp13m4n on 2009-12-08
Hello everyone.  I am using Xubuntu 9.10.  It will not log in.  Here is what happens:  I select my username and then type my password in the GUI.  I get the animation in the center of the blue login screen.  The screen goes black, then white, then goes back to the login screen.  What is going on? There is only one user on the system and it is used for surfing the Internet only.  Thank you for the help.

---

### Post by efflandt on 2009-12-08
What video card do you have?  I had an issue with Xubuntu 9.10 on an older computer (PIII 550) with older ATI video card.  It worked initially, but after the first set of updates, X stopped working and gui login kept recycling back to gui login.  I could log into an xterm if I picked that from dropdown list in gui login.  I discovered that installing xorg-driver-fglrx before doing any updates resolved my issue in that case.

When trying gnome in Ubuntu 9.10, it would not would seemingly crash even initially to a mostly white screen I think.  But the dropdown list in gui login offered an alternate **Failsafe GNOME** (instead of GNOME) that worked and allowed me to install xorg-driver-fglrx using Synaptic.  After that gnome worked.  However, some things are limited in Failsafe GNOME, for example I could not configure wireless, so I had to use a wireless bridge that could connect automatically using ethernet on the PC.

If you can get to xterm [or console (Alt-F2 or Ctrl-Alt-F2) and login], post the output of **sudo lspci -v** related to your video and someone may be able to help you.  If you want to save that to a file you could do **sudo lspci -v > lspci.txt** and use the live CD to copy that to usb memory or somewhere you can get at it if you do not know how to mount that from xterm/console.

---

### Post by s1mp13m4n on 2009-12-08
The computer is using intergrated Intel graphics the 865 chipset I believe.  I am a Linux newbie so I know little of the CLI and have seen but never used Xterm

---

### Post by s1mp13m4n on 2009-12-09
I booted from the cd and selected "fix broken packages" and that did not solve anything.  On the login screen I can select from two xfce sessions and one xterm session.  I know nothing of xterm.

---

### Post by PetteriP on 2009-12-10
Hi,
I just replied to this in another thread
> I had one of these today.
I could login to root desktop though.
In the .xsession-errors file there was an error stating something or other about the user rights of the .ICEauthority file. Right click on .ICEauthority and from the Permissions tab read and write rights to my user. That solved it.
Hope you get it solved, would be nice to know other solution to this - looks like many people are suffering from same but the fundamental problem seems to vary.

---

