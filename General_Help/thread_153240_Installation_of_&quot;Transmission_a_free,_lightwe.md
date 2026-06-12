---
title: "Installation of &quot;Transmission a free, lightweight BitTorrent client&quot; Solved!"
date: 2006-03-31
forum: General Help
---

### Post by goslackware on 2006-03-31
Homepage: [http://transmission.m0k.org/](http://transmission.m0k.org/)
About: Transmission is a free, lightweight BitTorrent client. It features a simple, intuitive interface on top on an efficient, cross-platform back-end.

License: Transmission is open source (MIT license) and runs on Mac OS X (Cocoa interface), Linux/NetBSD/FreeBSD/OpenBSD (GTK+ interface) and BeOS (native interface).


Code to install it in ubuntu with:


wget [http://naturidentisch.de/packages/fc4/transmission/transmission-0.5-2.cru.i386.rpm](http://naturidentisch.de/packages/fc4/transmission/transmission-0.5-2.cru.i386.rpm)
sudo alien transmission-0.5-2.cru.i386.rpm
sudo dpkg -i transmission_0.5-3_i386.deb
sudo ln -s /usr/lib/libcrypto.so /usr/lib/libcrypto.so.5
killall gnome-panel



Notes:
-check for newer versions later on and replace with newest version number.

---

### Post by dr.drake on 2006-04-15
I just tried it, and I must admit it is really lightweight and easy, but....
it is also really slow compared to azureus...
I did a test with different files that I opened in both programs at the same time,

after 5 minutes the score was:
file 1: azureus 00.0%   transmission 01.2%
file 2: azureus 11.0%   transmission 00.3%
file 3: azureus 14.3%   transmission 11.6%
file 4: azureus 01.4%   transmission 01.4%

after 43 minutes the score was:
file 1: azureus 19.5%   transmission 22.1%
file 2: azureus 47.0%   transmission 03.9%
file 3: azureus -done-   transmission 90.9%
file 4: azureus 54.4%   transmission 30.3%

if you are not in a hurry (which is always better for your health anyway) I would suggest use transmission, it is really lightweight and simple, but if you need speed and all the other options and don't mind it being a rescource hog, take azureus, but you should really judge for yourself.

---

### Post by rawler on 2006-04-19
Perhaps a proper package in Universe would be in order?

---

### Post by Jason_25 on 2006-04-19
This is a really slow and unconfigurable client on OSX.  I expect it's the same or worse on linux.  There are much better alternatives.

---

### Post by croak77 on 2006-04-19
I suggest rtorrent. Faster and lighter. :)

---

### Post by kanenas on 2006-06-12
please help using the commands the first poster mentions everything goes ok then i go to applications internet and i use transmission but nothing happens
transmission does not open?

please help how can i run it?

---

### Post by kanenas on 2006-06-12
i managed to find the solution the line 
sudo ln -s /usr/lib/libcrypto.so /usr/lib/libcrypto.so.5

for dapper should be
sudo ln -s /usr/lib/libcrypto.so.0.9.8 /usr/lib/libcrypto.so.5

and everything should work now

---

