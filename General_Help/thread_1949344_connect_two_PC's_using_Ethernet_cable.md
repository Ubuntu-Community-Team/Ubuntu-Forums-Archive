---
title: "connect two PC's using Ethernet cable"
date: 2012-03-30
forum: General Help
---

### Post by ramakanta on 2012-03-30
Hello, 
please help me the step by step configuration procedure of direct connected to  two PC's using ethernet crossover cable for tranfering of data .
 
From : UBUNTU OS <----------> Windows OS
         
          UBUNTU OS <----------> UBUNTU OS
          
          Windows OS<----------> Windows OS
 
 
 
Thank You.

---

### Post by HermanAB on 2012-03-30
Step by step for Widows? - use the GUI.

What you need to do is this:

Windows:
IP Address: 192.168.1.1
Netmask: 255.255.255.0
Gateway: 192.168.1.2
Share a directory.

Linux:
IP Address: 192.168.1.2 (ifconfig eth0 192.168.1.2 netmask 255.255.255.0)
Netmask: 255.255.255.0 
Gateway: 192.168.1.1 (route add eth0 default gw 192.168.1.1)
Use Nautilus connect to server command.

---

### Post by ramakanta on 2012-03-30
> **HermanAB said:**
> Step by step for Widows? - use the GUI.

What you need to do is this:

Windows:
IP Address: 192.168.1.1
Netmask: 255.255.255.0
Gateway: 192.168.1.2
Share a directory.

Linux:
IP Address: 192.168.1.2 (ifconfig eth0 192.168.1.2 netmask 255.255.255.0)
Netmask: 255.255.255.0 
Gateway: 192.168.1.1 (route add eth0 default gw 192.168.1.1)
Use Nautilus connect to server command.
if possible kindly give me step by step procees for linux .
thanks

---

### Post by HermanAB on 2012-03-30
It is right there, in the brackets.  

Google and learn.

---

