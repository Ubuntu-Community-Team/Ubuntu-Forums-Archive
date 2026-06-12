---
title: "GIMP no longer running?"
date: 2011-05-29
forum: General Help
---

### Post by ticktoast on 2011-05-29
For some reason, GIMP no longer runs. As in, I can't get it to open from the menu or the terminal. It's very likely that I tinkered with something that I shouldn't have, since I think some of the dependencies are missing, but I'm not sure.

Unfortunately, that's about all I can say. Any help would be greatly appreciated! 
(I've got family hounding me to touch up prom pictures. Ugh.)

---

### Post by flipper T on 2011-05-29
use synaptic package manager to re install

---

### Post by jerrrys on 2011-05-29
if that doesn't work, you can purge gimp.

 [http://ubuntuforums.org/showthread.php?t=1374158](http://ubuntuforums.org/showthread.php?t=1374158)

---

### Post by ticktoast on 2011-05-29
Ahh... no luck purging it.
And it was already downloaded from Synaptic. It reinstalled fine, but I can't get it to actually run. I can't get a window at all.

---

### Post by linuxinstalledfromhdd on 2011-05-29
You need to purge uninstall it from the command line.

---

### Post by dFlyer on 2011-05-29
move .gimp-2.6/ to .gimp-2.6.old and then restart program form the command line using gimp and report any errors it may report.

---

### Post by linuxinstalledfromhdd on 2011-05-29
What if you tried to add the Gimp PPA and upgraded it?  Wouldn't that fix it?

---

### Post by whoop on 2011-05-29
start gimp by typing "gimp" without the quotes into a terminal and see if you get info back on screen...

---

### Post by linuxinstalledfromhdd on 2011-05-29
Try this in terminal:  

Beware: It will install Gimp Painter completely over your old gimp (in case all else fails)

sudo add-apt-repository ppa:mizuno-as/gimp-painter
sudo apt-get update
sudo apt-get upgrade

---

