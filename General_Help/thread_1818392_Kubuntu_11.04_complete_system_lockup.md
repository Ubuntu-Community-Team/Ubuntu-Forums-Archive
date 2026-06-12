---
title: "Kubuntu 11.04 complete system lockup"
date: 2011-08-04
forum: General Help
---

### Post by false_chicken on 2011-08-04
I recently installed Kubuntu and occasionally the entire system will lock up at random. Everything stops. Number lock wont even turn on or off. I have to restart. Its has done this several times but the only time that I can remember what I was doing was the most recent lock up. I had Firefox open and I was in the terminal. As soon as I clicked the maximise button on the terminal it locked up. I have tried looking through some logs to maybe get some info on what is happening but I don't know where to start. Any suggestions? Thanks.

EDIT: I found out that every time that I maximised the terminal it would lock up. I disabled desktop effects to see if that is the issue and so far it seems like it was. I would like to have the effects though so any suggestions on how to maybe fix that would be greatly appreciated. 

Kubuntu 11.04 x86
Nvidia GTS 250
Asrock N68-S Mobo
AMD Phenom II x4 945
3 GB DDR2 Ram

---

### Post by ankspo71 on 2011-08-05
Hi,
I think the problem is related to this thread: [http://ubuntuforums.org/showthread.php?t=1742919](http://ubuntuforums.org/showthread.php?t=1742919)
There is also a bug report in the link.

This was happening to me in Kubuntu 11.04 too. I either got a system freeze or massive graphics corruption when I clicked on the maximize button of Konsole (or resized konsole). 

My advice is to stay away from Konsole for now and use a different terminal as a substitute until the problem is fixed.

lxterminal  (terminal used in LXDE desktops)
xfce4-terminal (terminal used in XFCE desktops)
gnome-terminal (terminal used in GNOME desktops)
and there are several others to choose from.

PS. You can change the default terminal at System Settings > Default Applications > Terminal Emulator.

---

