---
title: "Graphical interface not launching / Wifi connexion not working"
date: 2011-03-08
forum: General Help
---

### Post by euloiix on 2011-03-08
Hi everyone,

I updated the drivers of my graphic card yesterday because I was encountering lots of problems and crashes. And the all day it was working perfectly, even after several rebooting.

Unfortunately today is another story. When I start Ubuntu, I end up on the terminal and no graphic interface is launching. I tried **startx **but it is not working. 
I tried to fixed it, as well as to fetch back some working drivers for my graphic card,  but I needed some packages and my wifi connexion is not working. 

I tried to edit **/etc/network/interfaces** as the following: 

[HTML]
auto lo
iface lo inet loopback

auto wlan0
iface wlan0 inet dhcp
wireless-essid Livebox-b442
wireless-key XXXX-XXXX-XXXX-XXXX
[/HTML]with XXXX-XXXX-XXXX-XXXX being the WEP key. 
It is not working either.

I do not manage to ping anything else but localhost. 
If you have any idea how I could start my graphic interface again (even in safe mode) or have my wifi connexion working, this would be of great help.

Thank you very much in advance.
:)

---

