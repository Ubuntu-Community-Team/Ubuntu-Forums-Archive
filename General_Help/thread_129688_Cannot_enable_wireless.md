---
title: "Cannot enable wireless"
date: 2006-02-14
forum: General Help
---

### Post by palomar on 2006-02-14
I have installed my PCMCIA wireless card using NDISWrapper. Installation went well and if I do 'iwlist wlan0 scan' I can see the name of my other PC (ESSID). So the physical connection is OK i think.

Then I go to KDE system administration -> Network settings . My wlan0 is listed, but disabled. If I enabe it, it is enabled for about 1 second and then automatically it gets disabled again :( When looking at ifconfig and iwconfig the doesn't have an IP address. Also when I enter an IP address manually it gets disabled immediately.

How can I make my wlan work?

---

### Post by palomar on 2006-02-14
hmz, I think this is not a very popular forum category with 18 views of this topic in 3 hours.... Can a moderator move this topic to the main 'Networking' category of this forums? Thx.

---

### Post by palomar on 2006-02-14
I have made progress by following the official ndiswrapper manual located at [http://ndiswrapper.sourceforge.net/mediawiki/index.php/Installation](http://ndiswrapper.sourceforge.net/mediawiki/index.php/Installation) . Especially the commands: 
iwconfig wlan0 essid 'other_computername' 
iwconfig wlan0 mode Ad-hoc
dhclient wlan0

I think it's stranget hat it wouldn't work with the point&click KDE wireless tool.

---

### Post by FlakJacket on 2006-02-14
I had the same problem.  Try enabling dhcp on the eth1 device.  I think that is how I solved my issue.  Or maybe it was just continuous trying to enable it.

Flak

---

