---
title: "how do I set up interfaces file for dhcp (wireless)?"
date: 2006-03-22
forum: General Help
---

### Post by vayu on 2006-03-22
I have static working on my ethernet.  I have static working with WPA on my wireless AP.  I have DHCP working on wireless with WPA.

I can't get wireless working at hotspots like cafes, hotels, etc...

Here's what my /etc/network/interfaces has:

this is what I have for the hotspot, it doesn't work (after booting I enter 
ifup eth1=hotspot then dhclient):

iface hotspot inet dhcp
        wireless-mode managed
        wireless-essid any
        wireless-key open

for my wireless network with WPA, this works (I issue a wpa_supplicant command followed by dhclient after it boots):

iface eth1 inet dhcp
        gateway x.x.x.x
        dns-nameservers x.x.x.x x.x.x.x
        wireless-essid myessid
auto eth1

(I don't know if I need the gateway and nameserver entries in there, I just left them as they were in the working static entry)

So what should I put for wireless hotspots? If you don't know but have it working please show me what you have.

---

### Post by jpkotta on 2006-03-22
Try network-manager.  I haven't had very good results with it, but maybe you'll do better.  HowTo in the wiki.

Personally, I use network-admin, which is installed on a default system.  That should work reasonably well.

---

### Post by alamba on 2006-03-22
Whenever you're in a hotspot do you go into >>system>>admin>>networking...click on the wireless card and go into configure and choose the wireless LAN available in that location.

A

---

