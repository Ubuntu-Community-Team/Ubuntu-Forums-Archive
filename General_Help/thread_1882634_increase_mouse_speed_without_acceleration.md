---
title: "increase mouse speed without acceleration"
date: 2011-11-17
forum: General Help
---

### Post by cpup on 2011-11-17
Hi,

is there a way to increase mouse speed once acceleration is disable ?

I used the following command to disable mouse acceleration :
xinput set-prop 11 'Device Accel Profile' -1
Where 11 is my mouse id (standard logitech with low dpi  ~800)
It worked great

But now i can't find anything to increase mouse speed.
I tried playing with xinput options but nothing worked, all options seem related to acceleration.
I tried in System Settings> Mouse and TouchPad. Nothing change when i move sliders in Pointer Speed.

I know it's technically possible because i have no problem in windows 7. My mouse is fast enough without acceleration. the only downside is that the mouse is not super accurate but it's fine.

Thanks in advance

PS: I tried to google this problem for days and found nothing.

---

### Post by Frogs Hair on 2011-11-17
Hello and Welcome 

Install the the new configuration editor with the command below .```
sudo apt-get install dconf-tools
``` 
I looked through it quickly but didn't find any mouse related settings but I may have missed them . Also you could check the file system for configuration files

---

### Post by cpup on 2011-11-18
Thanks for the answer.

I tried this command with my ubuntu live cd: it failed to install even after an apt-get update

W: Duplicate sources.list entry cdrom://Ubuntu 11.10 _Oneiric Ocelot_ - Release amd64 (20111012)/ oneiric/main i386 Packages (/var/lib/apt/lists/Ubuntu%2011.10%20%5fOneiric%20Ocelot%5f%20-%20Release%20amd64%20(20111012)_dists_oneiric_main_binary-i386_Packages)
W: You may want to run apt-get update to correct these problems
E: Unable to locate package dconf-tools



I tried with linux mint live cd: it was installed correctly but i was unable to find how to use dconf-tools


Sorry im very newbie with linux

---

