---
title: "No Internet Connection Icon On Top Panel"
date: 2011-08-04
forum: General Help
---

### Post by PossumNZ on 2011-08-04
When connected to the Internet I have no icon on the top Panel notifying my laptop is connected even though I can use the Internet.
I would also like to set up a wireless connection but can't find any network manager in the Launcher.
Any help always appreciated.

---

### Post by mikewhatever on 2011-08-04
The icon in the panel is nm-applet. It should be in the user startup processes under the title 'Network Manager'. If you disabled startup processes make sure it's not disabled. You can also check if it's running with the 
**ps aux | grep nm-applet** command.
To access the wireless configuration interface, use System->Preferences->Network Connections.

---

### Post by wildmanne39 on 2011-08-05
Hi, you can run these commands in a terminal and it will help us to get your wireless working.
```
sudo lshw -C network 
```
```
lspci -nn | grep 0280
```
```
lsusb
```
```
lsmod
```
```
iwconfig
```
```
rfkill list all
```
and post the outcome here by clicking on new reply and click # and paste the information between the brackets.
Thank you

---

