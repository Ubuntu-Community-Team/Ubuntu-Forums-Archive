---
title: "Help needed using a wifi card with ndiswrapper"
date: 2006-04-04
forum: General Help
---

### Post by DownloadTHIS on 2006-04-04
I installed my wireless card (D-Link DWL-520 PCI card) with ndiswrapper through ndistk successfully, but now have no idea how to enable it. A little help please?

---

### Post by evilgold on 2006-04-04
modprobe ndiswrapper
sudo ifconfig wlan0 up
sudo iwconfig ESSID YOURESSIDHERE
sudo dhclient wlan0

...assuming your nic is listed as wlan0 from "ifconfig -a"

Edit: forgot modprobe

---

### Post by evilgold on 2006-04-04
Also, your card has linux drivers, so you should probably try those first.

[http://support.dlink.com/faq/view.asp?prod_id=357](http://support.dlink.com/faq/view.asp?prod_id=357)

---

### Post by DownloadTHIS on 2006-04-04
[QUOTE=evilgold]modprobe ndiswrapper
sudo ifconfig wlan0 up
sudo iwconfig ESSID YOURESSIDHERE
sudo dhclient wlan0

...assuming your nic is listed as wlan0 from "ifconfig -a"

Edit: forgot modprobe[/QUOTE]
Stupid question, what's an ESSID and how do I find out what mine is?

---

### Post by trent dillman on 2006-04-04
If you use Gnome, use the Network Manager.

Your ESSID is the name of your network (e.g., "linksys", "my_wireless_network")

---

