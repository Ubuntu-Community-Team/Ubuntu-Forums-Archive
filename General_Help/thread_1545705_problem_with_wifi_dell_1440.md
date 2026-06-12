---
title: "problem with wifi dell 1440"
date: 2010-08-04
forum: General Help
---

### Post by rejimbbs on 2010-08-04
I have ubuntu 9.04 on my dell laptop inspiron 1440. I have a wireless router of belkin, its working fine with windows but not getting wifi on ubuntu. I am new to ubuntu. I tried various solution on the net but not much use.
 Wifi driver is   Broadcom Corporation BCM4312
 sometime laptop shows its connected but when I try with firefox I cant browse the net.
 Dr. Reji

---

### Post by TBABill on 2010-08-04
Have you tried plugging the machine into your router via ethernet cord so the system can download and install the driver? Once plugged in your machine should prompt you that there is a proprietary driver available (if it isn't doing so already in the upper right part of the top panel to the left of the time and network icon). I have 2 machines with the same adapter and have to plug them into a wired port on my router one time so the system can install the driver, then I'm all set.

---

### Post by lovinglinux on 2010-08-04
Also make sure you have ipv6 disabled.
[LIST=1]
[*]Type **about:config** in the address bar, press Enter.
[*]Find network.dns.disableIPv6 in the list.
[*]Right-click -> Toggle.
[*]Restart Firefox and try again.
[/LIST]

---

### Post by rejimbbs on 2010-08-05
I changed the setting of mozilla firefox but still the problem persist.
sometimes on the network icon on the right top side shows that connection is established but still I cant browse the internet. wht to do?

---

### Post by lovinglinux on 2010-08-05
So then I guess you have a wifi issue. Unfortunately, I don't know how to troubleshoot that.

---

