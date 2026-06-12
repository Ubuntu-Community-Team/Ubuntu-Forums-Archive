---
title: "Use my netbook's wireless interface to connect desktop computer to the internet"
date: 2010-10-20
forum: General Help
---

### Post by t0p on 2010-10-20
I'm not usually such a dullard, but for some reason I just can't figure out how to do this.  I've looked at various guides and how-tos, but it won't sink in.  I hope someone here might be able to explain in simple terms so I can get this done.

**Situation:** I currently have no wired internet access at home.  But a neightbour has a wifi connection that she has very kindly said I can use.

I own a desktop computer with a a regular eth0 internet interface, a netbook with a wireless card (wlan0), and a wireless router.

**Objective:** I want to be able to connect the desktop computer to the internet, by passing the traffic through the router and the netbook, using the netbook's wireless connection to my neighbour's internet link

Can anyone help please?

---

### Post by KeLa on 2010-10-20
Easy way is that if your wireless router supports "Client" mode you can connect
your desktop to it with eth0 wire and then use router as wireless card to connect your neighbor's wireless connection.

Or you can connect your desktop to netbook with eht0 wire and use it as router to
neighbor's wireless connection.

---

### Post by t0p on 2010-10-22
> **KeLa said:**
> 
Or you can connect your desktop to netbook with eht0 wire and use it as router to
neighbor's wireless connection.

This is what I want to do.  But I don't know *how*.

Anyone?

---

### Post by KeLa on 2010-10-23
This thread will explain how to share internet connection in ubuntu
[http://ubuntuforums.org/showthread.php?t=91370](http://ubuntuforums.org/showthread.php?t=91370)
Before that you need to connect your pc's together with crossover ethernet cable
see: [http://en.wikipedia.org/wiki/Ethernet_crossover_cable](http://en.wikipedia.org/wiki/Ethernet_crossover_cable)

---

### Post by HermanAB on 2010-10-23
Howdy,

On the netbook:
Connect the WiFi as normal, using DHCP.
Enable IP forwarding: $ sudo echo "1">/proc/sys/net/ipv4/ip_forward
Set the ethernet address: sudo ifconfig eth0 192.168.1.1 netmask 255.255.255.0 up

Run a cross-over cable between the netbook and desktop (or use a switch).

On the desktop:
Set the IP address: sudo ifconfig eth0 192.168.1.2 netmask 255.255.255.0 up
Set the route: sudo route add default gw 192.168.1.1

That should do the trick.

---

