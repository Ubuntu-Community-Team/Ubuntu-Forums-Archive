---
title: "Netgear WG311 v3 with WPA2?"
date: 2006-03-16
forum: General Help
---

### Post by Hangetsu on 2006-03-16
I have a Netgear WG311 v3 wireless card, and I am trying to connect it to my home network, which does not broadcast its SSID and using WPA2 and AES.

I can get ndiswrapper to use the drivers, but I can't configure it there as it only supports WEP.

I tried wpasupplicant, but that seems to knock out the wlan0 created by ndis!!

I'm at a loss for how to get this thing configured;  my wife finds it hysterical that I have to use her Windows PC to get this message out.  Please help!

---

### Post by Hangetsu on 2006-03-16
It seems to have sorted itself out, and what doesn't make any sense is that iwconfig seems to show it as being connected (or having the info):

wlan0:
IEEE 802.11g ESSID="<MyID>"
Mode: Managed Frequency=2.437 GHz Access Point <MAC address, not straight 0's>
Bit Rate=54 Mb/s Sensitivity=200 dBm
Link Quality=100/100

etc etc...

The information is there, it just doesn't seem to want to connect for some reason.

---

### Post by Hangetsu on 2006-03-17
I got it to work, but it was a bit goofy.  I used ndisgtk (name?), the GUI that goes over top of ndiswrapper.  It found the drivers and set up wlan0, but I didn't *configure *it - The reason being that the configuration only has WEP, where my network is WPA2.

I also installed wpasupplicant and set that up, receiving the information listed in my previous post when I ran iwconfig.  So I was really puzzled last night - I had a linux box recognizing my hardware and drivers, assigning the correct information and keys to connect to my wireless network, yet nothing.

What I did was use ndisgtk to "configure" wlan0, not putting in any key information (as it would be useless via WEP).  Once I rebooted, the wpasupplicant worked to connect me, as my wlan0 device was active this time (rather than being recognized but unconfigured).

---

### Post by dpaint4 on 2006-03-17
[QUOTE=Hangetsu]I got it to work, but it was a bit goofy.  I used ndisgtk (name?), the GUI that goes over top of ndiswrapper.  It found the drivers and set up wlan0, but I didn't *configure *it - The reason being that the configuration only has WEP, where my network is WPA2.

I also installed wpasupplicant and set that up, receiving the information listed in my previous post when I ran iwconfig.  So I was really puzzled last night - I had a linux box recognizing my hardware and drivers, assigning the correct information and keys to connect to my wireless network, yet nothing.

What I did was use ndisgtk to "configure" wlan0, not putting in any key information (as it would be useless via WEP).  Once I rebooted, the wpasupplicant worked to connect me, as my wlan0 device was active this time (rather than being recognized but unconfigured).[/QUOTE]

That's all really really useful information. I hope people can easily find your post in moments of WiFi panic, which seems to be a common affliction around here!

---

