---
title: "Setting up dual monitors"
date: 2010-06-17
forum: General Help
---

### Post by xxdksxx on 2010-06-17
Well i have just made the switch from windows and am trying to set up my dual monitors to where i have my main screen and then the other screen to watch movies etc but the furthest i have gotten is making them clones i have an nvida gforce 8600 graphics card. thanks in advanced : )

---

### Post by DCGStudios on 2010-06-17
Open up a terminal (ctrl + alt + t).. and run 'sudo apt-get update'

Assuming your in gnome, go to System > Administration > Hardware Drivers, and install the proprietary driver for your card. Reboot.

Then go into your nVidia settings and configure it as you wish..

The settings are located at System > Administration > nVidia X Server Settings

Good Luck!

---

### Post by xxdksxx on 2010-06-17
ok cool i will give it a shot thanks

---

### Post by xxdksxx on 2010-06-17
ran into this? what should i do?

---

### Post by cap10Ibraim on 2010-06-17
system >preference>monitors 
uncheck "same image in all monitors play with the two monitors there right or left

---

### Post by JAS510 on 2010-06-19
got the same issue

---

### Post by dpgtfc on 2010-06-22
> **xxdksxx said:**
> ran into this? what should i do?

try opening terminal and typing "sudo nvidia-settings"

---

