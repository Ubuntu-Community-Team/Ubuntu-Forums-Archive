---
title: "Internet works from Live CD only"
date: 2006-06-06
forum: General Help
---

### Post by zBoost on 2006-06-06
Thats pretty strange, and I do consider it as a major bug in Dapper as I saw lot of people had similar problems to mine. It seems there isn't a defined solution. Here's my problem anyway:
Have 2 lan cards, mainboard ASUS K8N, nforce3, eth1 - CNeT PRO200 card, eth0 - nVidia integrated. Now my internet is coming from eth1, static ip configured and works fine in live cd. I can set both network cards, my lan works, I have internet - everything great so far. And I decided to install ubuntu 6.06, installed it, restarted and SURPRISE, my lan works (the integrated eth0) it returns ping, but I don't have internet connection anymore from eth1 and there was no way to start it again. There is no ping to gateway, dns etc... Tryed turning the system off and booting straight to ubuntu ( i have win xp also) but it was the same thing.

This is very annoying, how I will have internet in live cd and not when it is installed ?

---

### Post by dentaku65 on 2006-06-06
try these commands:

sudo killall dhclient
sudo ifconfig eth0 down
sudo ifconfig eth0 up
sudo dhclient eth0

if works you can create a script:

#!/bin/bash
killall dhclient
ifconfig eth0 down
ifconfig eth0 up
dhclient eth0

---

