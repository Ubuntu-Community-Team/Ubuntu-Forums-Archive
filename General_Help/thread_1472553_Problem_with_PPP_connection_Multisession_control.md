---
title: "Problem with PPP connection: Multisession control"
date: 2010-05-04
forum: General Help
---

### Post by Taak on 2010-05-04
My notebook is connected using wlan to a **Pirelli Alice Wgate 2 Plus WiFi router. **I set it up following this tutorial:
 
[http://wiki.ubuntu-it.org/Hardware/Modem/PirelliWgate2PlusWiFi](http://wiki.ubuntu-it.org/Hardware/Modem/PirelliWgate2PlusWiFi)
 
It works without any problem and the network connection works at 100%.
 
 
The problem started when I had to connect an access point to my network. When my notebook is connected to the access point and I try to start pppoe connection:
 
```
 
sudo pon adsl-provider
plog

```
 
it says:
 
```
 
Connected to [mac address] via interface wlan0
Using interface ppp0
Connect: ppp0 <--> wlan0
Remote message: REASON013 - MULTISESSION CONTROL
PAP authentication failed
Connection terminated.

```
 
So my internet connection doesn't work. How can I fix this? What is multisession control?

---

### Post by Taak on 2010-05-04
It would be good for me to connect my notebook to the router and not to the access point (without removing the access point).
 
I tried to insert MAC address of router in the wireless setup but it doesn't work...

---

### Post by Taak on 2010-05-04
So I'm on the Network-manager trying to modify mi wireless connection.
 
I have to modify BSSID or MAC address in order to force my notebook to connect to router and not to access point.
 
**1) Which parameter should I use? BSSID or MAC address? I tried both with no result.**
 
**2) Which MAC address should I insert? I tried to insert the result of "arp -a 192.168.1.1" (where 192.168.1.1 is my router LAN address) but it doesn't work**

---

