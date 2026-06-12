---
title: "Taskbars disappeared! Command window doesn't open!"
date: 2012-07-04
forum: General Help
---

### Post by avokailop on 2012-07-04
I just updated (my good old Toshiba Sattelite A100-153) to ubuntu version 12.04.
After normally using the computer and a standard reboot, I lost both x and y axis taskbars.
I thought it might be that somebody in my household changed some graphical settings, 
but also no command window opens with the usual hotkeys.

Please help!

---

### Post by dino99 on 2012-07-04
if you are using unity, into a terminal, run: unity --reset

otherwise:
for Gnome-Shell: gnome-shell --replace
for gnome-classic: gnome-panel --replace

for everything else:

sudo dpkg --configure -a

---

### Post by lolpenguin on 2012-07-04
For some reason or other, your X session crashed. If you can't read logs (hidden somewhere in /var/log that only root can read), then you need to provide more information. Get into a teletype Ctrl + Alt + F1 to use the command line.

---

### Post by avokailop on 2012-07-04
After resetting Unity settings, restarting in 2D mode helped. Found out my graphical card doesn't support 3D settings. Thanks guys!

---

