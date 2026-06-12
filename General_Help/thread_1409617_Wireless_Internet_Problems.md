---
title: "Wireless Internet Problems"
date: 2010-02-17
forum: General Help
---

### Post by JarrettK on 2010-02-17
I recently installed Ubuntu, and cant get connected to my wireless router(Linksys). I've read all over the internet and tried using the NetworkManager but when I click on that my only option is to "Configure VPN" I can add a wireless connection from there but there is nowhere to connect to the network ...it just reads "Never Used". Can anybody please help me connect to the internet?

---

### Post by Greenwidth on 2010-02-17
If you can, connect wired and look in System > Admin > Hardware Drivers for a driver to enable.
If you can't, type the follwing into a terminal and post the output here.
```
lspci | grep Net
```
to determine the chipset on your card.

---

### Post by JarrettK on 2010-02-17
09:00.0 Network Controller: Broadcam Corporation BCM4322 802.lla/b/g/n Wireless LAN Controller (rev 01)

---

### Post by Greenwidth on 2010-02-18
The drivers you want (STA) are on the LiveCD (it's why the wireless works when using it) and in the repos, they are not included in the installation because they are not open source.

If you can't get access to a wired connection, see section 2 of:
[http://ubuntuforums.org/showthread.php?t=1368699](http://ubuntuforums.org/showthread.php?t=1368699)

---

