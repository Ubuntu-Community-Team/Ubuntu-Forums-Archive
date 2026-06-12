---
title: "Wireless adapters that work with Ubuntu"
date: 2012-06-07
forum: General Help
---

### Post by Mazate on 2012-06-07
I was wondering if anyone could recommend some wireless adapters that are known to work well with Ubuntu.  I have an all wireless setup now and before I buy the parts to build my new computer I was wondering if anyone knew of a sure-fire wireless adapter that I can count on to work.

---

### Post by mikewhatever on 2012-06-08
Edimax Ew7128g PCI adapter.
```
00:0a.0 Network controller: Ralink corp. RT2500 Wireless 802.11bg (rev 01)
```

Worked out of the box in 10.04 and 12.04.

---

### Post by pdk on 2012-09-11
Ralink corp. RT2500 Wireless 802.11bg (rev 01)
When I first installed 12.04 the wireless card worked intermitantly.
I installed ndiswrapper and that also worked intermitantly.
I removed ndiswrapper and now  I no longer get wlan0

syslog shows 
Loading kernel module for a network device with CAP_SYS_MODULE (deprecated).  Use CAP_NET_ADMIN and alias netdev-wlan0 instead
 Network controller: Ralink corp. RT2500 Wireless 802.11bg (rev 01)
lspci -k shows 
	Subsystem: Surecom Technology Device 13f3
	Kernel modules: rt2500pci
/etc/udev/rules.d/70-persistent.rules does not get a wlan0 generated.
modprobe - l also shows the rt2500pc1 is loaded.

I would really like to solve this problem.
Peter

---

### Post by greatsirkain on 2012-09-11
belkin 802.11 b/g wireless usb dongle worked perfectly from the beginning for me, didn't install a thing, even worked from the ubuntu live disk & it was easy to set up internet connection sharing to my ethernet card + it was dirt cheap. 
You might want to think about a b/g/n version though as fiber optic networks seem to require the newer cards to run full speed.

---

### Post by AndyOpie150 on 2012-09-11
pdk. Are you saying you installed the wireless adapter driver with ndiswrraper?
If yes, after install of the driver with ndiswrapper try this:
```
sudo modprobe ndiswrapper
sudo su
echo ndiswrapper >> /etc/modules
exit
``` Reboot


Got this from chili555 less than a week ago and it worked for me.

---

