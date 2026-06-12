---
title: "Gnome Panel disappear.. :("
date: 2011-10-09
forum: General Help
---

### Post by nerdyguy64 on 2011-10-09
Hey i dont know what happened, but both my gnome panels disappeared (im on classic), and the only way i can get them back is to put in the terminal: gnome-panel
but if i close the terminal so do my gnome panels.... is there anyway that i can get them to stay, and stay when i reboot and login back in... I saw people were deleting some files, but it also would delete chat accounts on the bars, etc. Any way to not do this, and plus didnt work for me.... im stuck... anyone know how to keep them from disappearing... thanks!

---

### Post by hollowsyndicate on 2011-10-09
make a gnome-panel command script in gedit and put it in /home/you/.config/autostart

---

### Post by nerdyguy64 on 2011-10-09
to make a command script do i just like put: gnome-panel
in a text file and save as ummm like a bat file? i know thats windows but im bite new here

oh and there is no autostart folder, got into the .config folder but no autostart

---

### Post by hollowsyndicate on 2011-10-09
> **nerdyguy64 said:**
> to make a command script do i just like put: gnome-panel
in a text file and save as ummm like a bat file? i know thats windows but im bite new here

hold on lol. lemme try it, i havent used ubuntu 4 a while.

---

### Post by nerdyguy64 on 2011-10-09
what do you use? just wondering...

And thanks!

---

### Post by hollowsyndicate on 2011-10-09
k do the gnome-panel in terminal, then go 2 system/preference/startup applications. click on add, call it watever u want, then put in gnome-panel in command, then press add n reset. see if it works.

---

### Post by nerdyguy64 on 2011-10-09
Thanks a thousands man, worked great! btw what linux distro do you use?

---

### Post by hollowsyndicate on 2011-10-09
10.04

---

### Post by cscj01 on 2011-10-27
I upgraded to Oneiric yesterday, and I'm using Gnome Classic (obviously Gnome 3).  Today while moving some menu items around, both my panels disappeared.  Then a top panel re-appeared, but it looked like an application menu bar with choices like File, View, etc.  I tried everything to get to my applications but could not. I finally had to perform a force power off and reboot.  When I logged in, my panels were back.  If you can't start anything (I have no icons to launch an application from my desktop), how do you get to a terminal to execute gnome-panels?

---

