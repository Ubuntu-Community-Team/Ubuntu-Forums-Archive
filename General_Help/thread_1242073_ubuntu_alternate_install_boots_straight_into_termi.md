---
title: "ubuntu alternate install boots straight into terminal"
date: 2009-08-16
forum: General Help
---

### Post by fcuk112 on 2009-08-16
i had some problems with installing win7 or ubuntu 9.04 regular installer (got errno5 errors) so i used the alternate installer. 

now the laptop boots straight to terminal (i do see the splash screen) and the home folder is empty.  how do i restore booting into the GUI?

thanks.

---

### Post by earthpigg on 2009-08-16
sudo apt-get install ubuntu-desktop

let us know if you encounter any issues.

---

### Post by fcuk112 on 2009-08-16
it says ubuntu-desktop is already the latest version.

if i do startx, then it says no such file or directory - unable to connect to X server.

---

### Post by earthpigg on 2009-08-16
sounds like something got borked during the install.

the easiest and quickest thing to do at this point is probably to do a fresh install and ensure your internet and power is reliable.

if the problem persists after doing a fresh install, try this out:

do a 'command line only install', then sudo apt-get install ubuntu-desktop.

---

### Post by wojox on 2009-08-16
What does the prompt at the boot menu say? You never got a boot screen?

---

### Post by earthpigg on 2009-08-16
he gets a boot screen, and then he gets the graphical ubuntu login window.... and then it shoots to the CLI.

O WAIT, im an idiot.

at the graphical login window, try going to options -> sessions -> GNOME and login.

see if that works.


sorry if you already started the fresh install! i feel like a moron for not thinking of that simple solution first.

---

### Post by fcuk112 on 2009-08-16
no i didn't get to the stage of the graphical login window, it went to CLI before the splash finished.

anyways, i tried your suggestion of reinstalling again and it works now! =)  now to get the sound back on my dv2000.

thanks for your help.

---

### Post by flat49head on 2009-08-16
If you cannot get a gui after fresh install...run lspci from a command line.
Look for a line that says VGA compatible controller: BLAH BLAH BLAH...(this being a description of the video hardware).
If the line is not there, or no description, your video hardware is not supported (probably same issue with Windoze7)

---

### Post by flat49head on 2009-08-16
Another thought...if the VGA line is there, Ubuntu Jaunty may not have a driver for it.
This is something I am battling with wireless controller BCM4318.  As I have no wireless hence my access is from another Linux box.  Same with my Canon printer...it sees it, however no driver to load.

---

### Post by fcuk112 on 2009-08-16
after my last install i got some segmentation faults and firefox closing on me, then ran memtest and saw lots of red.  so all these install woes can be traced back to faulty memory (funnily enough had this on one of my desktop PCs as well).  ordered some new ram so fingers crossed that should fix all my issues.  thanks again.

---

