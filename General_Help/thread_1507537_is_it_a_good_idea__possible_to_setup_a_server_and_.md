---
title: "is it a good idea / possible to setup a server and firewall in one machine"
date: 2010-06-11
forum: General Help
---

### Post by Ioky on 2010-06-11
Hi, all

sense the number of computers is increasing in my household. I am looking forward to setup a file/print server, so I don't know have to get a printer for each computer, and access all the file from all the machine I have. few Linux machine and one each of mac and windows. 

I also want to setup a linux base router/firewall. it is just that I don't know if this possible to done in one machine. like the file/print sever and router/firewall in one machine.

if it is possible, is it a good idea. or they really should be in two machine. 

Thanks all.

---

### Post by bodhi.zazen on 2010-06-11
If you set up a computer as a router it should serve as a router only. You may include a DNS and DHCP server on the router if you wish.

The install should have a minimal install and should not have any additional packages installed, I highly suggest you use a firewall specific distro such as ipcop, there are several to choose from.

On a separate computer , behind the firewall, set up a print (samba) server. The print server can be anywhere and is not particularly taxing on resources, so you could use any of your computers and include a desktop as well.

I also suggest you look at setting up a large network shared drive for shared information. You may use samba for this as well.

---

