---
title: "Ubuntu splash screen freezes"
date: 2010-03-05
forum: General Help
---

### Post by gazz1982 on 2010-03-05
Hi I am running Ubuntu karmic with Gnome desktop

I rebooted it as a package (GRASS GIS) wouldn't open properly, the splash screeen appeared but it appears to freeze and does not get to the login screen. I have tried to boot in safe mode but pressing ESC at grub doesn't work and Ctrl+Alt+F1 also fails to invoke anything.  I can connect remotely via ssh. I have tried to remove Gnome desktop so I can just go straight to commandline but it still brings up the splash screen, I removed desktop using sudo apt-get remove gnome-desktop it said it did.

So why did this happen, last night I logged in via ssh and x-win server started a screen and did some work, the x-win server I lost my internet connection so putty aborted, this morning I couldnt connect to the screen so I did screen -wipe then rebooted as another package kept exiting.

any help much appreciated, this has happend at a vital time during my PhD and I need ubuntu back asap! In the meanwhile I am working via ssh with a slow internet connection so not ideal!

Gary

---

### Post by gazz1982 on 2010-03-05
I managed to get it to boot to command line 
when i type startx I am left with a blank screen and nothing happens

---

