---
title: "Jaunty Locks the Laptop."
date: 2009-08-14
forum: General Help
---

### Post by Cygoku on 2009-08-14
I have a DELL Inspiron 6400, I am using Jaunty (been using Ubuntu since Gutsy), and this never happened before.  The system locks up from time to time for no apparent reason, even after a fresh update.  It also happened once during the installation of Jaunty while in LiveCD.  

Also, I have no sound.  I have to set every program to use OSS.  If a program doesn't let me choose the sound server to use, there will be no sound at all.  Such as Firefox or Emesene for example.  

Please help me !! :(

Cygoku

---

### Post by aethex on 2009-08-14
Sometimes, Ubuntu just isn't compatible with a computer's hardware. I had this experience with a new netbook running Jaunty. I had to configure lots of files, change plenty of options, and even download a tray application to get it to work 100%.

1. If you are able to change some hardware to something more compatible (replace the RAM or HDD - these were the causes of system lock-ups on my old laptop), then do so. Maybe borrow a friend's RAM to try it out before you buy :)

2. Is your kernel up-to-date? Old versions of the kernel and OS may also destabilize the machine.

3. Faulty drivers may disable some features or make the whole thing crash. Download the latest BIOS / firmware updates from DELL under Windows, and get up-to-date drivers for everything under Ubuntu, if you can (graphics, mainboard, sound). This is probably why your sould doesn't work.

If all else fails, some hardware just isn't compatible with Ubuntu. If an older version works, by all means use it, if it's still supported. Future releases of Ubuntu may also fix a lot of hardware problems. You'll miss out on some bleeding-edge features, but chances are that these won't hinder your Ubuntu experience.

---

### Post by Cygoku on 2009-08-15
Atleast, isn't there any way to force every app to use OSS sound server.  

Or, can I use the same mesa driver as Jaunty under Hardy ?? If yes, will it already be in the repo ?? 

Cygoku

---

