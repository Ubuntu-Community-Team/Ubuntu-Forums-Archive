---
title: "WEP Encryption"
date: 2005-03-03
forum: General Help
---

### Post by Rajjan on 2005-03-03
I'm currently installing Ubunto for the first time and everything seems to go just fine. However, one small (security isnt small) problem occurs when the part where you should configure the wireless network device (my eth1). The problem is that we cannot use WEP-keys, only open wireless connections (without a wepkey). I'm not really sure what the problem lies but I hope that someone can help, thanks.

Hardware:
ROUTER: Netgear 54MBPS Wireless Router WGR614 v2
NIC: Intel Corporation PRO/Wireless LAN 2100 3B Mini PCI Adapter
LAPTOP: Compaq nx7010

---

### Post by byourg on 2005-03-03
eth1 is not considered a wireless connection. wlan and ath are considered wireless connections. You need to reconfigure your lan connection to these types, then you will get a WEP key dialog box in network configuration. Hope this helps.

---

### Post by dracnor on 2005-03-04
If eth1 doesnt show up in your network configuration tool, see if you can get to it from the command line.  A wireless connection can be bound to eth1 depending on configuration.  In the terminal type iwconfig and it will show you a list of adapters with wireless extensions. To set the encryption key type iwconfig eth1 enc s:KEYHERE, you can also set it up with hex if you want.  man iwconfig for more details.

hth

---

### Post by Rajjan on 2005-03-04
Well. I turned off the WEP Encryption on AP. Then everything works fine. But,  I´m not running without security... 

the wlan0 as you prefer, is called eth1, and is in fact an wireless connection,  So i kan asign an hexadeimal key, but it still dosent work...  :sad:  So... :(

---

### Post by az on 2005-03-04
My orinocco pcmcia card is also considered an eth device.  My usb crappy wireless device is called wlan0.  It depends on the kernel module.

---

### Post by chris415 on 2006-04-16
[QUOTE=Rajjan]Well. I turned off the WEP Encryption on AP. Then everything works fine. But,  I´m not running without security... 

the wlan0 as you prefer, is called eth1, and is in fact an wireless connection,  So i kan asign an hexadeimal key, but it still dosent work...  :sad:  So... :([/QUOTE]


Well what has happened is it fixed?   I am having the same issues, and I tried all of the above steps, and I still can not get mycisco card and  Linksys AP and Ubantu/linux to work?

{banging my head on the table}

---

