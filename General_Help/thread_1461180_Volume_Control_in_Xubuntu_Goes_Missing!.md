---
title: "Volume Control in Xubuntu Goes Missing!"
date: 2010-04-23
forum: General Help
---

### Post by Spaceman9 on 2010-04-23
I'm using Xubuntu 9.10 and somehow, for some reason I know not what, the volume control on the panel disappeared. Does anyone know how I can get it back? 

I tryed adding it with Add To Panel but that doesn't work. Thanks for any help.

---

### Post by ScarySquirrel on 2010-04-23
Use synaptic to search/install a program called "volwheel" which replaces the volume wheel in xfce, or enter the following code in your terminal. 
```
sudo apt-get install volwheel
```

Run it from your programs menu or by typing the following in a terminal: 
```
volwheel
```

Ya I know it's a hack fix but **** it, if you need something right away, this will work.

---

### Post by Spaceman9 on 2010-04-23
Thanks for the help ScarySquirrel but I tryed the terminal and Synaptic and volwheel is conspicuous by it's absence. Perhaps it's no longer in the repos.

---

### Post by Spaceman9 on 2010-04-24
I ran xfce-volumed in the terminal and got this:

creative@creative-desktop:~$ xfce-volumed
xfce-volumed: command not found
creative@creative-desktop:~$

---

### Post by ScarySquirrel on 2010-04-24
Perhapz try installing. 
```
sudo apt-get install xfce-volued
```

---

### Post by Spaceman9 on 2010-04-24
that isn't working either. The only thing close to that is:

Volume management daemon for Xfce 4

Xfce4-volumed is responsible for making the volume up/down and mute keys of the
keyboard work automatically, and uses the Xfce 4 mixer's defined card and track
for chosing which track to act on. It also provides volume change / mute toggle
notifications if the notification server used supports x-canonical-icon-only
and x-canonical-synchronous notifications.

Canonical does not provide updates for xfce4-volumed. Some updates may be provided by the Ubuntu community.

---

### Post by Yellow Pasque on 2010-04-24
There was a typo in the command (missing 'm'). Anyway, the volume daemon is for the volume keys on your keyboard and such.

Try running this in a terminal:
```
xfce4-mixer
```

---

### Post by Spaceman9 on 2010-04-24
Ok, I got this:

creative@creative-desktop:~$ xfce4-mixer
Could not initialize GStreamer: Error re-scanning registry , child terminated by signal
creative@creative-desktop:~$


I also ran this "sudo apt-get install xfce4-volumed" and got this:

creative@creative-desktop:~$ sudo apt-get install xfce4-volumed
[sudo] password for creative: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
xfce4-volumed is already the newest version.
The following packages were automatically installed and are no longer required:
  linux-headers-2.6.31-14 linux-headers-2.6.31-14-generic
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
creative@creative-desktop:~$

---

