---
title: "so i switched...."
date: 2006-03-26
forum: General Help
---

### Post by Specialsauce on 2006-03-26
and i cant seem to get my internet working. i installed the driver in ndiswrapper like a good boy, but it still refuses to show up when i 'ifconfig -a' in the command line. help please.

---

### Post by mdmarmer on 2006-03-26
What card and chipset do you have?

Which drivers did you use?

What version of Ubuntu?

Mike

---

### Post by jj1814 on 2006-03-26
I fought with my wireless card for an entire day before I found this page .... great resource. [http://christer.homeip.net/wordpress/?page_id=8](http://christer.homeip.net/wordpress/?page_id=8)

Also, every time I boot up, i have to

sudo modprobe ndiswrapper
sudo iwconfig wlan0 essid <essid>
sudo dhclient wlan0

after that, im set and on the internet

---

### Post by Specialsauce on 2006-03-26
[QUOTE=mdmarmer]What card and chipset do you have?

Which drivers did you use?

What version of Ubuntu?

Mike[/QUOTE]
its not a card, its an external wireless adapter. it works under gnome, and its a Linksys WUSB54G adapter. it connects VIA usb if you were wondering.

I installed the driver that worked so well for me in GNOME, and my version is 5.10

---

