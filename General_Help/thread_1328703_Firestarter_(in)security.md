---
title: "Firestarter (in)security?"
date: 2009-11-16
forum: General Help
---

### Post by gvsopic on 2009-11-16
Hello,
   I'm running ubuntu on a box that I'm using as a router between my internal network on an ad-hoc wireless connection and the Internet on a 3g USB modem attached to the box. Things are running smoothly but I've noticed a problem with Firestarter. It seems that if the Ad-hoc network goes out of range, the wireless interface becomes inactive, prompting firestarter to disable the Firewall. The problem is, it disables the Firewall on both interfaces, the inactive wireless one and the hot PPP Internet connection thus exposing my machine and leaving it pretty much naked! I've tried to find some resources on this but to no avail. Any ideas? You could try this on a standalone machine by just enabling the ICS for your Lan card (if you're using the wireless as the main one) and trying to start the firewall, it should tell you that it couldn't detect one of the cards and disable the firewall on the one that is active. This is with Firestarter 1.0.3
Thanks
gv

---

### Post by coldReactive on 2009-11-16
sudo apt-get install gufw

use it instead of firestarter.

---

### Post by bodhi.zazen on 2009-11-16
My advice to you is to use a distro that is designed to act as a firewall, ie ipcop or smoothwall.

[http://sourceforge.net/apps/trac/ipcop/wiki](http://sourceforge.net/apps/trac/ipcop/wiki)

---

### Post by gvsopic on 2009-11-24
Thanks for the feedback guys. I've tried gufw before but I liked the firestarter activity log and it's support for ICS. 

Downloaded IPcop and Smoothwall on an old toshiba laptop I had and it connected fine to the Internet but I couldn't get it to detect the IPW2100 card on the machine. I guess I would have to compile the drivers on there. 

Anyhow, to solve my quandary for now I put to use an old Linksys router I had. I stripped it of all DHCP/whatever services that were running on it and plugged in my linux box on one of the lan ports. Now I don't have to deal with the Ad-Hoc wireless hicups I get when trying to connect to the dogone machine's wireless, the linksys router-turned-access-point does that for me. 

Cheers fellas.

---

