---
title: "[Jaunty] Can't connect to internet"
date: 2011-03-03
forum: General Help
---

### Post by azlan95 on 2011-03-03
Hi everyone

I'm using a desktop having 9.04 as the OS.  This machine is connected to a router.  The router supports both wireless and normal wired connections.

I already plugged in a LAN cable connecting the desktop to the router.  My desktop can access the router's admin via 192.168.1.1.  But I can't seem to configure the network manager to access the internet via wired connection.  I want to use wired because I don't have wireless adapter installed on the desktop.

Please help me have internet access.  Thank you.

Azlan

---

### Post by davidmohammed on 2011-03-03
jaunty is no longer supported - I would encourage you to download the 10.04 LTS.  You can no longer download updates directly - only from the repository archive manually.

If you've got access to the routers admin page then look for some DHCP settings - you should set the router to be a DHCP server.  Your ubuntu will then automatically pick up an IP address.

Do you connect to the internet via ADSL?  If so, you'll need a ADSL router, or a ADSL modem with an ethernet port that connects to your router.  Check the router ADSL internet connection settings - it will tell you what the status of your internet connection is.

---

### Post by turtle153 on 2011-03-03
The opposite worked for me. I had to keep resetting the router to access the internet with DCHP but now I assigned it to a static IP it's flawless.

---

### Post by gsgleason on 2011-03-03
Azlan, please show output of 'netstat -nr' from a terminal.

---

### Post by azlan95 on 2011-03-03
> **gsgleason said:**
> Azlan, please show output of 'netstat -nr' from a terminal.

This is the output

Kernel IP routing table
Destination     Gateway         Genmask         Flags   MSS Window  irtt Iface
192.168.1.0     0.0.0.0         255.255.255.0   U         0 0          0 eth0
169.254.0.0     0.0.0.0         255.255.0.0     U         0 0          0 eth0
0.0.0.0         192.168.1.1     0.0.0.0         UG        0 0          0 eth0


Somehow I must have changed something which made it to work at this moment.  So thank you all for all the help.

Azlan

---

