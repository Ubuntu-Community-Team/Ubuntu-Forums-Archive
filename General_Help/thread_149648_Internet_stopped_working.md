---
title: "Internet stopped working"
date: 2006-03-24
forum: General Help
---

### Post by jmcoreymv on 2006-03-24
Im using Ubuntu 5.10 with a prism54 card.  The internet worked great for a few days but yesterday it just stopped working.  In the networking control panel it shows the wireless card there and that its connected to my network but I cant ping/use the internet/etc.  I noticed that for some reason it wont keep the default gateway setting.  Everytime I change it, it changes back to blank.  I've tried rebooting and removing/reinstalling the pcmcia card with no luck.  Any ideas?

---

### Post by halfvolle melk on 2006-03-24
Maybe if you add the gateway to the appropriate file it will stay put. You can do this by opening a terminal and type:
```
gedit /etc/network/interfaces
```
In there there's a block that begins with
**# The primary network interface**
Append the following line to the block
**gateway a.b.c.d**
where **a.b.c.d** is the IP of the gateway.

---

### Post by jmcoreymv on 2006-03-24
I tried adding that line to the interfaces file but it did not change anything.

---

### Post by halfvolle melk on 2006-03-24
You can check the configuration with
```
ifconfig
```
Sometimes this might help
```
sudo /etc/init.d/networking restart
```
or you could try
```
sudo ifdown -a
sudo ifup eth0
```
Afterwards check if you can ping anything.

---

### Post by jmcoreymv on 2006-03-24
Still didn't work.  I noticed that it cant grab the DHCP information either when it does DHCPDISCOVER.  I tried setting up it with static information but it didnt help.  Also I noticed when I close the network-admin box, the command line says "CRITICAL **: gst_xml_element_set_content: assertion 'node != NULL' failed.

---

### Post by jmcoreymv on 2006-03-24
Oh I made a mistake when I said it wouldnt hold the gateway information, I meant it wouldn't hold the gateway device.

---

### Post by jmcoreymv on 2006-03-24
I decided to go ahead and reformat and reinstall.  After the reinstall the card still cant access the internet.  It can see all the wifi networks in my area but is also unable to use the other ones (and my own).  If I plug a network cable into the wired NIC then the internet works fine and it lets me set the default gateway device to eth0 (wired nic), but it wont let me set it to eth1 (wireless PCMCIA).  I dont see how ubuntu would automatically work after my first fresh install, but not the second.  I'm using the exact same CD and havent changed the hardware.

---

