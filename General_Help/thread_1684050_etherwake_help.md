---
title: "etherwake help?"
date: 2011-02-08
forum: General Help
---

### Post by pqwoerituytrueiwoq on 2011-02-08
i noticed my desktop has the option in its bios to use this since i mainly use it as a server i wanted to be able to power it on remoly once i found out it was possible
lets say for sake of example the mac address on it is 00:11:22:33:44:55 on the dekstop

also wondering if it is possible to power down the nvidia video card
i would like to have it complexly ignore the card's existent and cut power to the slot
i would like to basically pick server/desktop mode from grub 2 default being server

---

### Post by stinkeye on 2011-02-08
This tutorial worked for me.
[**_[COLOR="DarkRed"]HOWTO: Set your system up for Wake On LAN (WOL)[/COLOR]_**]("http://ubuntuforums.org/showthread.php?t=234588")

---

### Post by pqwoerituytrueiwoq on 2011-02-08
thanks, any idea how to do it from the internet?

---

### Post by stinkeye on 2011-02-08
Have a look here.
[**_[COLOR="DarkRed"]http://www.dd-wrt.com/wiki/index.php/WOL[/COLOR]_**]("http://www.dd-wrt.com/wiki/index.php/WOL")

---

### Post by pqwoerituytrueiwoq on 2011-02-08
I just got it working i had to use udp forwarding not tcp
seems tomato stores the mac address in the background so it works from the ip :)

---

### Post by stinkeye on 2011-02-08
I only just got wol working and not very cluey on this stuff,
so what's the method to wake from the internet.
Thanks.

---

### Post by pqwoerituytrueiwoq on 2011-02-08
know how to do port forwarding for a web server or vnc?
same thing it uses port 9 and the udp protocol
i was testing from teh internet side of my router from the inside
wakeonlan -i 192.168.1.2 00:11:22:33:44:55
desktop is on the 10 network
edit does not work after teh computer has been off for a while
edit2: guess i will just use remote access for my tomato router and and use it to wake the system up

---

