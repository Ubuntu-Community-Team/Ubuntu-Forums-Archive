---
title: "Dell Help?"
date: 2011-09-16
forum: General Help
---

### Post by Jlbbly on 2011-09-16
well i just recently installed Ubuntu 10.10 on my Dell Latitude D520 but have no idea how to enable the WiFi, I'm not familiar to laptops. So any help will be awesome.  


Thanks in Advance.

---

### Post by varunendra on 2011-09-16
First off, make sure the WiFi is physically switched 'on' if there is a physical on/off switch provided. It is also done by a key combination of 'Fn' key + some other key depending upon laptop model, or in some models, by merely touching the WiFi LED at the laptop's LED panel.

After that, assuming you are using default Gnome desktop, look at the right side of the upper panel. There should be the Network Manager's icon (four concentric curves, or two up-down arrows). Right click on it and make sure there is a tick mark beside "Enable Networking". Then left-click on it to see a list of available networks (that is- if your WiFi adapter is working and there are wireless networks available in the range). If you see any, just click on it and provide the passphrase if asked. If no networks are found, or if the wifi adapter is not working, then open a terminal (Application > Accessories > Terminal), enter the following commands one-by-one, and post their outputs here:
```
sudo lshw -C network
ifconfig -a
iwconfig
rfkill list all
```Also, if you see networks available but can't connect to them (passphrase not accepted), then you need to add/edit the network in Network Manager (right-click on NetworkManager icon > Edit Connections... > Wireless tab > Add or Edit button) and make sure that correct encryption type is selected (wep/wpa/wpa2 etc) in the security tab.

---

