---
title: "connetion to internet via Lan server"
date: 2006-03-18
forum: General Help
---

### Post by harys on 2006-03-18
hi, i would apppreciate it if you could tell me how to set up connections on ubuntu. i was used to do it with <tools> <options> <connection setting> under windows, but i didn't find this path when i launched firefox under ubuntu linux.i connect to the internet via server LAN of my university. under windows the path was : tools>options>connections setting>manual proxy configuration "proxy.studenti.unicatt.it" and choose ignore this proxy for local address. thanks for your help. harys

---

### Post by hw-tph on 2006-03-18
At least in Firefox 1.5, it is Edit --> Preferences --> General --> Connection Settings.


Håkan

---

### Post by hajk on 2006-03-18
In Ubuntu you use the menu System/Administration/Networking, you will then see at least one interface, depending on the way you're connected to the LAN. If this is a wired LAN, the interface is probably eth0; if it is a wireless LAN, the interface could have various names, like wlan0 or ath0 or sometimes also eth0 or eth1.

So, highlight the interface you're going to use, then hit Properties, and check Enable the interface. You will then have to give some particulars, like DHCP when the server issues the IP. For a wireless LAN you would also have to provide the network name or essid (pick one from a list, may be) and a WEP key. Then OK, and activate the interface should establish the network. If you don't deactivate the interface before shutting down, then the next time you boot the interface will come up automatically (if you're connected). Simple enough, really...

---

