---
title: "Getting 800cpi to stay with System settings?"
date: 2006-03-04
forum: General Help
---

### Post by e2k on 2006-03-04
Hi!
I've got kubuntu up and running, and am pretty pleased with it. I was especially impressed when I saw you can edit the counts per inch directly from System Settings -> Mouse -> MX500 Optical Mouse, I used to do this with logitech_applet, but this is way easier. The only problem is, that I can't get this setting to stay! Everytime I start my computer, it's back to 400cpi, and I have to manually put it to 800? What might be causing this, and how might I fix it? :-k 

(I have a feeling there's a rather easy solution to this :) )

---

### Post by z-vet on 2006-03-04
I have a very same problem with my Logitech Pilot. I found something that looks like a solution for this (just press "Help" in mouse configuration module), it includes a script to fix device's permissions on startup and more, but never got it to work (maybe, i'm too stupid or too lazy). e2k, maybe you can do it better than me? I never reboot my machine, so once i set 800cpi it stays there even on KDE restarts, but it would be nice to have this thing working as it needs to work.

---

### Post by e2k on 2006-03-04
[QUOTE=z-vet]I have a very same problem with my Logitech Pilot. I found something that looks like a solution for this (just press "Help" in mouse configuration module), it includes a script to fix device's permissions on startup and more, but never got it to work (maybe, i'm too stupid or too lazy). e2k, maybe you can do it better than me? I never reboot my machine, so once i set 800cpi it stays there even on KDE restarts, but it would be nice to have this thing working as it needs to work.[/QUOTE]Why didn't I think of pressing Help myself.. :D There seems to be a solution to this, I'll try to follow it and tell you how it went :)

---

### Post by e2k on 2006-03-04
Unfortunately I didn't succeed, I created the script and edited /etc/hotplug/usb/logitechmouse.usermap. But after a reboot I still had 400cpi and could not change to 800cpi from the System settings (the MX500 Optical Mouse tab was completely grey).. :cry:

---

