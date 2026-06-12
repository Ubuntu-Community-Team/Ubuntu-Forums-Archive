---
title: "configuring internet from the command line"
date: 2010-02-23
forum: General Help
---

### Post by golanbatrac on 2010-02-23
I just installed a command line version of karmic to an old desktop.  During installation, DHCP failed, so I attempted to configure manually (without really knowing what I'm doing) and wound up without a connection.  I've been searching for solutions, but really don't understand what I need to do.  A million thanks to anyone who can help me get up and running (or at least give me a push in the right direction).

I can either connect the computer directly to the cable modem via USB, or directly to my wireless router via ethernet cable.  I know what the ip address for my laptop (which is connected wirelessly to the router) but don't know if that would be the same for the desktop or not, and don't really know anything else.

---

### Post by patchwork on 2010-02-23
I'm not  guru on this stuff, but you can check your interfaces using

```
ifconfig -a
```

and try to enable your interface using 

```
ifup -a
```

Check out the man pages for ifconfig and ifup for more info.

```
man ifconfig
man ifup
```

BTW, the ip address of your desktop should not be the same as your laptop going through a router on DHCP...each address must be unique to each node on the network

---

### Post by golanbatrac on 2010-02-23
I think I finally got it to work (fingers-crossed).  I'm reinstalling using the ethernet cable from the router instead of the usb cable from the modem, and it appears to have auto-connected.  That still doesn't do anything for my complete and total inability to understand the least little thing about networking and internet connections (no matter how many man pages and FAQs I read).  I need to buy a book on the subject, for sure...

Thanks, patchwork.

---

### Post by dcstar on 2010-02-24
> **golanbatrac said:**
> I just installed a command line version of karmic to an old desktop.  During installation, DHCP failed, so I attempted to configure manually (without really knowing what I'm doing) and wound up without a connection.  I've been searching for solutions, but really don't understand what I need to do.  A million thanks to anyone who can help me get up and running (or at least give me a push in the right direction).

I can either connect the computer directly to the cable modem via USB, or directly to my wireless router via ethernet cable.  I know what the ip address for my laptop (which is connected wirelessly to the router) but don't know if that would be the same for the desktop or not, and don't really know anything else.

All the network configuration is in /etc/network/interfaces.

You will not get USB to work, only Ethernet.

```
man interfaces
```

---

