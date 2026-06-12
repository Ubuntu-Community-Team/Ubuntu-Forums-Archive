---
title: "wireless usb card"
date: 2010-12-22
forum: General Help
---

### Post by mike22112211 on 2010-12-22
i am trying to get my wireless usb card working, ive got ubuntu feisty fawn. when i type lsusb i get the following message:

Bus 002 Device 002: ID 148f:9021 Ralink Technology, Corp.
Bus 002 Device 001: ID 0000:0000
Bus 001 Device 001: ID 0000:0000

but when i type iwconfig i get the following message:

lo        no wireless extensions.

eth0    no wireless extensions.

so it doesnt show up as wifi0 etc... any ideas on how to make it show up? thanks in advance.

---

### Post by Hippytaff on 2010-12-22
Ralink can be a pain, especially with older versions of ubuntu...give this a bash
[http://ubuntuforums.org/showthread.php?t=502526](http://ubuntuforums.org/showthread.php?t=502526)
 
Edit -> Or maybe think about upgrading to 10.04

---

### Post by TBABill on 2010-12-22
Can you provide the information in the file /etc/modules please? Need to see what driver is being loaded. Also the information in /etc/modprobe.d/blacklist.conf to see what is blacklisted.
 
Your card should be using the rt73usb driver from what I can tell so we need to make sure it isn't blacklisted and that it's loading.

---

