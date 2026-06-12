---
title: "configure two ip"
date: 2010-04-26
forum: General Help
---

### Post by JJJCR on 2010-04-26
hi guys is it possible  to configure one static ip such as 203.blah.blah.blah and then 192.blah.blah.blah
Need your help on how to do this. Thanks. :P

---

### Post by wmatthews on 2010-04-26
Right click on the network icon, click on "edit connections" and add all the addresses that you would like!

---

### Post by lisati on 2010-04-26
Many routers come with the ability to set static IP addresses, which can be safer than setting them in Ubuntu if you're likely to be connecting, say, your laptop with more than one network, e.g. home and work. The exact details will depend on which router you're using.

---

### Post by JJJCR on 2010-04-26
> **lisati said:**
> Many routers come with the ability to set static IP addresses, which can be safer than setting them in Ubuntu if you're likely to be connecting, say, your laptop with more than one network, e.g. home and work. The exact details will depend on which router you're using.
hi lisati, thanks for the reply.
so you mean i'll set the static ip on the router and how about the dynamic ip which is for the local network?
But if i want to set in ubuntu any guides or steps to start with? Thanks again :popcorn:

---

### Post by bab1 on 2010-04-26
> **JJJCR said:**
> hi lisati, thanks for the reply.
so you mean i'll set the static ip on the router and how about the dynamic ip which is for the local network?
But if i want to set in ubuntu any guides or steps to start with? Thanks again :popcorn:

What Lisati has said is not true.  Dynamic addresses (via DHCP) are less reliable.  The DHCP server can fail.  A static address is configured by a file and is ultimately more reliable that any running process.

A static address is not defined as: unchanging.  They are defined by how it is configured.  Manually configuring an address makes it static.  The unchanging DHCP served address is known as "reserved" and it is still dynamic even if it is unchanging.

---

### Post by bab1 on 2010-04-26
> **lisati said:**
> Many routers come with the ability to set static IP addresses, which can be safer than setting them in Ubuntu if you're likely to be connecting, say, your laptop with more than one network, e.g. home and work. The exact details will depend on which router you're using.

Routers do not set static IP addresses for clients.  They are dynamic if they are leased out by DHCP.  Yes, they may be unchanging but they are still dynamic.

---

### Post by blueridgedog on 2010-04-26
I would configure the static public IP on the router, and then a static private IP on your system and configure the router to route traffic from the public IP to the private one.

---

### Post by Iowan on 2010-04-26
I call it a "static lease"...
Are you attempting to configure a static address on two interfaces, or two static addresses on one interface? Is it a Network Manager controlled machine - or does it use */etc/network/interfaces* (server)?

---

### Post by JJJCR on 2010-04-27
> **Iowan said:**
> I call it a "static lease"...
Are you attempting to configure a static address on two interfaces, or two static addresses on one interface? Is it a Network Manager controlled machine - or does it use */etc/network/interfaces* (server)?

hi all, thanks for the replies.

i'm trying to configure two static addresses on one interface. need your insight guys on how to achieve this. Thanks.

---

### Post by blueridgedog on 2010-04-27
> **JJJCR said:**
> hi all, thanks for the replies.

i'm trying to configure two static addresses on one interface. need your insight guys on how to achieve this. Thanks.

Then the first post in the thread is what you want.

---

### Post by JJJCR on 2010-05-03
> **blueridgedog said:**
> Then the first post in the thread is what you want.

yes bluridgedog, so is there a just a file in which i can edit or add in the ip addresses? thanks.

---

### Post by dcstar on 2010-05-03
> **JJJCR said:**
> yes bluridgedog, so is there a just a file in which i can edit or add in the ip addresses? thanks.

Follow the advice already correctly given to you, open the Ethernet interface, find the IPv4 section and add in as many IP addresses as you like.

When you have added in the new address, exit all the boxes and then left-click the network icon and click on the listed connection to implement the changes.

---

### Post by blueridgedog on 2010-05-03
There are countless pages online on how to edit the configuration files if you don't want to use the gnome configuration tool:

[https://help.ubuntu.com/8.10/serverguide/C/network-configuration.html](https://help.ubuntu.com/8.10/serverguide/C/network-configuration.html)

[http://www.ubuntugeek.com/ubuntu-networking-configuration-using-command-line.html](http://www.ubuntugeek.com/ubuntu-networking-configuration-using-command-line.html)

However, to take over editing them manually, you will need to uninstall the Gnome network manager, which I do not recommend.  The first reply to this post indicated how to add additional IP addresses using the Gnome tool.

---

