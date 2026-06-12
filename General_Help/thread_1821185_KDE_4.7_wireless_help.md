---
title: "KDE 4.7 wireless help"
date: 2011-08-08
forum: General Help
---

### Post by miasmablk on 2011-08-08
I updated to KDE 4.7 today with MUCH trouble muon hung at towards the end of the updrade at 100% so i had to force quit with " sudo ksysguard" it refused to boot into the desktop so i had to complete the upgrade from the terminal/safe mode when it finished i could not get my wireless to work my drivers is installed properly and i have tried toggling the wireless switch, much to my dismay but nothing seems to work. i can't scan for networks and the network-manager app just reports  "WLAN Interface: Error: Invalid state"

---

### Post by roccity1 on 2011-08-08
Are you able to do sudo ifconfig "wireless card" up from a terminal? If not does it give a error. Also you can try removing the driver and reinstalling it again with rmmod "wireless module" and reinstalling with modprobe "wireless module" and then try ifconfig "wireless card" up. note; wireless card is your wireless card like wlan0, eth1.. etc.

---

### Post by miasmablk on 2011-08-08
> **roccity1 said:**
> Are you able to do sudo ifconfig "wireless card" up from a terminal? If not does it give a error. Also you can try removing the driver and reinstalling it again with rmmod "wireless module" and reinstalling with modprobe "wireless module" and then try ifconfig "wireless card" up. note; wireless card is your wireless card like wlan0, eth1.. etc.


muon suddenly, popped up with some updates that it "left out" do to dependencies when i ran "sudo dpkg --configure -a" so i was able to force install them using "sudo apt-get upgrade -f" now everything works perfectly I'll mark this as solved thanks for your help, much appreciated :D

---

