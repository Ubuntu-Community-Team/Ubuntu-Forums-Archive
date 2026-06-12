---
title: "Connect Wifi via Terminal"
date: 2010-08-14
forum: General Help
---

### Post by redfox1160 on 2010-08-14
I want to connect to a wifi network through the terminal on my ubuntu machine. When I run iwconfig, this is what I get:
```
wlan0     IEEE 802.11bg  ESSID:"\x02\x1A\xFEC\xFB\xFA\xAA:\xFB)\xD1\xE6\x05<|\x94u\xD8\xBEa\x89\xF9\\xBB\xA8\x99\x0F\x95\xB1\xEB\xF1\xB3"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          
```
The network is visible, and I can connect to it using some desktop environments (GNOME/KDE), but not in others (wmii). If someone could tell me how to connect to a network using the terminal, I would greatly appreciate it. Thanks.

---

### Post by redfox1160 on 2010-08-14
I started up wicd:
```
wicd-client -n &
```
When I try to connect to my network, it says "Connection Failed: Bad Password". I don't know why this is happening. I am using the correct password. Any suggestions? Thanks.

---

### Post by redfox1160 on 2010-08-14
I was able to solve it. I uninstalled network-manager:
```
sudo apt-get remove network-manager
```
then I restarted wicd:
```
sudo /etc/init.d/wicd restart
```
After that, I was automatically connected to the network. Hope this helps anyone in the future.

I was doing this using wmii

---

