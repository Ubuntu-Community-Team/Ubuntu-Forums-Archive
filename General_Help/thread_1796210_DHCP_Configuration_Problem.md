---
title: "DHCP Configuration Problem"
date: 2011-07-03
forum: General Help
---

### Post by bijumk on 2011-07-03
Hello

I am new to ubuntu, Installed it somefays before and getting used to it

I want to share the Internet from my ubuntu box with 2 Win7 boxes and a  through a switch (have 2 network connections, eth0 - LAN and eth1 - Internet) . Searched a lot i google and got some Idea about the process..

Installed DHCP by

>  sudo apt-get install dhcp3-server
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following NEW packages will be installed:
  dhcp3-server
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 0 B/5,850 B of archives.
After this operation, 69.6 kB of additional disk space will be used.
Selecting previously deselected package dhcp3-server.
(Reading database ... 129823 files and directories currently installed.)
Unpacking dhcp3-server (from .../dhcp3-server_4.1.1-P1-15ubuntu9_all.deb) ...
Setting up dhcp3-server (4.1.1-P1-15ubuntu9) ...
and as per directions I tried to configure it by

> sudo nano /etc/default/dhcp3-serverBut unfortunately the file is blank

checked /etc/dhcp3/dhcpd.conf
no such file created yet... 

please help me to solve the issue

---

### Post by bijumk on 2011-07-04
somebody help me please

---

### Post by Azdour on 2011-07-04
Hi,

Have a look at:

[http://www.ubuntugeek.com/how-to-install-and-configure-dhcp-server-in-ubuntu-server.html](http://www.ubuntugeek.com/how-to-install-and-configure-dhcp-server-in-ubuntu-server.html)

It might help you.

---

### Post by bijumk on 2011-07-04
Thanks Azdour for your quick reply

I was following the instructions of the same page, but cannot continue because there is no dhcp3-server file is created in /etc/default/

---

### Post by linuchsan on 2011-07-04
What does dpkg -l |grep dhcp say?

---

### Post by bijumk on 2011-07-04
It says so

> ii  dhcp3-server                          4.1.1-P1-15ubuntu9                         ISC DHCP server (transitional package)
ii  isc-dhcp-client                       4.1.1-P1-15ubuntu9                         ISC DHCP client
ii  isc-dhcp-common                       4.1.1-P1-15ubuntu9                         common files used by all the isc-dhcp* packages
ii  isc-dhcp-server                       4.1.1-P1-15ubuntu9                         ISC DHCP server for automatic IP address assignment


---

### Post by linuchsan on 2011-07-04
Remove all of your dhcp-servers and install dhcp3-server again.

---

### Post by bijumk on 2011-07-04
Ok Linuschan

can you please tell me the commands for unistallation and installation, coz I tried it 2-3 times and everytime got the same problem

Many thanks

Biju

---

### Post by linuchsan on 2011-07-04
There are different ways to do this, but in your case i would do: sudo dpkg --purge isc-dhcp-server dhcp3-server

---

### Post by bijumk on 2011-07-04
Hi

Now I'm landed here

> sudo dpkg --purge isc-dhcp-server dhcp3-server
dpkg: warning: there's no installed package matching dhcp3-server
dpkg: dependency problems prevent removal of isc-dhcp-server:
 gadmin-dhcpd depends on dhcp3-server; however:
  Package dhcp3-server is not installed.
  Package isc-dhcp-server which provides dhcp3-server is to be removed.
dpkg: error processing isc-dhcp-server (--purge):
 dependency problems - not removing
Errors were encountered while processing:
 isc-dhcp-server

Is that OK ? sorry for my very limited knowledge of linux

---

### Post by linuchsan on 2011-07-04
Try sudo apt-get autoremove

---

