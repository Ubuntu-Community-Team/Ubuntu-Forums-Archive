---
title: "Dlink wireless connection issue"
date: 2010-06-02
forum: General Help
---

### Post by kmwill23 on 2010-06-02
Hello!  I am new to ubuntu and have it freshly installed and running.  Runs great!  Until I try to connect the wireless, using the NetworkManager and terminal.

Hardware:

Dlink 802.11g wireless router
Belkin N1 wireless adaptor
ubuntu 10.04 LTS

Symptoms:

When attempting to connect to my network, communication can't be established with the router.  The router never sends back any information, and on the router's side it never logs the attempts to establish a connection.  This is the same whether I attempt to use no security, WEP, or WPA.

However, I can connect to other unsecured wireless networks without any issues, including another unsecured Dlink network in the area.

Windows is able to establish this same connection in less than 3 seconds, on the same machine.

Ubuntu recognizes the device and has the correct driver, or I assume so since it does connect to other networks.

---

### Post by PoppaPuddin on 2010-06-04
I am having a similar issue with the same router and want to elaborate  on the problem. I had Ubuntu installed on my netbook before and was  eventually able to get the wireless router working. I had to reconfigure  the router and essentially start from scratch to get all of my devices  (Windows desktop, Windows laptop, Ubuntu 9.10 netbook, and Wii). What I  found the mistake I made before was that I had "WPA2 only" selected on  the router (Setup ->Wireless). I also configured the pre-shared key  to be something that I could input from the keyboard. That seemed to  work in getting everything up and running the first time.

The  computer went down and I had to reinstall Ubuntu (this time I am using  10.04). After installation I was able to get connected to the router but  only briefly. It will drop the connection and then will not  re-authenticate. Even after reboot it will not re-authenticate. I  thought that it might be the level of security so I plugged in the  ethernet and ran the updates but that was not the issue. I turned off  the security and was able to connect wirelessly and maintain a  connection.

---

