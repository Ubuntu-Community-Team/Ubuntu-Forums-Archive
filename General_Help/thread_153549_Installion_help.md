---
title: "Installion help"
date: 2006-04-01
forum: General Help
---

### Post by spacedz on 2006-04-01
Hello

My laptop powered down during the later stages of the installation, is there any way to continue on from where it left off? When I turn it on and select Ubuntu I end up at the command line and I've no idea what I should be doing there. I'd have thought Gnome would boot up by default, can I launch it from the command line? It's possible it was one of the things that didn't finish installing.

Much appreciated.

---

### Post by Ramses de Norre on 2006-04-01
You can launch gnome with ```
sudo /etc/init.d/gdm start
```
and type in your user passwd, but I have no idea about resuming the installation.

---

### Post by Sutekh on 2006-04-01
Had you got past the point where you installed GRUB and were told to remove the CD and reboot?

If so you can run
```
sudo apt-get install ubuntu-desktop
```This will install the default Ubuntu desktop (GNOME).

If the packages were downloaded but not installed you can run
```
sudo dpkg --configure -a
```to set them up.

Otherwise you may need to start again.

---

### Post by spacedz on 2006-04-01
Thanks guys, I did the "sudo dpkg --configure -a" command and then "sudo apt-get install ubuntu-desktop" and it's continuing to install. I assume this should install everything?

Normally I'd just start again but my laptop has overheating issues and the installation kept stopping in the same place. Need to take it apart and check the thermal grease.

---

### Post by Sutekh on 2006-04-01
Yep sounds like it should work out fine.  You will probably need to run
```
sudo /etc/init.d/gdm start
```when that's finished I don't know if the display manager will start automatically.

If you pull the heatsink of the CPU you should probably re-apply some thermal paste, while your there if the lappy is old.  If there is not a good contact between the heatsink and CPU, through the paste then you could have issues.

---

