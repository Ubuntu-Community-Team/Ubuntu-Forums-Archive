---
title: "Can't get into 10.0.0.2"
date: 2011-04-10
forum: General Help
---

### Post by warrior_juggalo on 2011-04-10
Hey, I need to forward a port for transmission, I right click on my network manager, Click on "Connection Information" And it gives me.....



Interface: 802.11 WiFi (wlan0)
Hardware address: 00:1E:2A:21:c7:21
Driver: rtl8187
Speed: 48 Mb/s
Security: WPA/WPA2

IPv4
IP Address: 10.0.0.2
Broadcast address: 10.0.0.255
Subnet Mask: 255.255.255.0
Default Route: 10.0.0.138
Primary DNS: 10.0.0.138

IPv6
Ignored

I enter "10.0.0.2" in firefox and it says it's "Unable to connect", I am doing this right am i not?

---

### Post by ~Plue on 2011-04-10
10.0.0.2 is *your* lan ip. the router's ip is, from what i gather from your post, 10.0.0.138

/to set up 'port forwarding', you'll need to use the latter

---

### Post by lmarmisa on 2011-04-10
If you have no http server running on your computer, you get that message of Firefox.

If you wish to check your network, open a terminal (Applications -> Accessories -> Terminal) and type these two commands (Ctrl-C to abort):

```

ping 10.0.0.2
ping 10.0.0.138

```

---

### Post by warrior_juggalo on 2011-04-11
> **~Plue said:**
> 10.0.0.2 is *your* lan ip. the router's ip is, from what i gather from your post, 10.0.0.138

/to set up 'port forwarding', you'll need to use the latter

Thank you, It worked, Unfortunately what did not work was what i wanted to get into it for in the first place.

I wanted to port forward for Transmission to speed up downloads it double/tripled the speed for about 30 minutes now it's slow as it was before.

---

### Post by Enigmapond on 2011-04-11
That usually needs to be done by accessing your router and doing it there. Have you tried putting this in the address bar? 192.168.1.1 or 192.168.0.1 Normally this gives you internet access to the router configuration. Once there, you should have a setting for port forwarding and the port that Trasmission uses is 51413. If you are unsure how to access the router, google your routers model and port forwarding for instructions. If it's a Netgear router, just type routerlogin.net in the address bar the default pass is admin & password.

---

