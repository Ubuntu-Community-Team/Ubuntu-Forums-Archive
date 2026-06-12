---
title: "Freshly booted 8.10 with no apps running shows network activity?"
date: 2010-03-30
forum: General Help
---

### Post by jamesisin on 2010-03-30
How can I track down what's using my nic and kill it (if appropriate).  There are no applications running which might be authorized to send and receive packages, so I don't really know why the System Monitor shows network activity.

---

### Post by bobcollard on 2010-03-30
> **jamesisin said:**
> How can I track down what's using my nic and kill it (if appropriate).  There are no applications running which might be authorized to send and receive packages, so I don't really know why the System Monitor shows network activity.
Need to know.  Are you running pppoe, or external modem for DSL, or Broadband, maybe a router?  Anything could be polling your computer to keep it online.  How much network activity are we talking about?  What are your computer specs?  Send a screen shot of the System Monitor without anything else running.

---

### Post by jamesisin on 2010-03-30
It's very little activity.  The 9.10 machine I have here also reports no activity (obviously on the same network).  I am no a cable connection but there is a firewall between these machines (Linksys router) and the Comcast device.

---

### Post by bobcollard on 2010-03-30
> **jamesisin said:**
> It's very little activity.  The 9.10 machine I have here also reports no activity (obviously on the same network).  I am no a cable connection but there is a firewall between these machines (Linksys router) and the Comcast device.
Okay, I've got a Linksys router with DSL, enclosed is a cropped screens shot with (Nothing) going on.  You need a magnifying glass, but, there are hiccups along the one minute interval.

---

### Post by jamesisin on 2010-03-30
Ok.  So, thanks for confirming independently that this machine has more activity than it ought.

How can I track down what's using my nic and kill it?  Some utilities like netstat maybe?

---

### Post by bobcollard on 2010-03-31
> **jamesisin said:**
> Ok.  So, thanks for confirming independently that this machine has more activity than it ought.

How can I track down what's using my nic and kill it?  Some utilities like netstat maybe?
Open Terminal and type in:
```
top
```It will show all running applets and what they are using in terms of RAM. I'm not familiar with Netstat.
EDIT: You might check your startup applications and see if anything to do with network is starting before you want it to.

---

### Post by jamesisin on 2010-03-31
Top is very useful, just not for this.  Unless there is an argument for top which you know about that gives network activity information.

In Windows I can use netstat -b to give specific connection information ([NOPARSE]localip:port remoteip:port[/NOPARSE] [application]), but that option doesn't appear to be available for BASH.

---

### Post by bobcollard on 2010-03-31
> **jamesisin said:**
> Top is very useful, just not for this.  Unless there is an argument for top which you know about that gives network activity information.

In Windows I can use netstat -b to give specific connection information (localip:port remoteip:port [application]), but that option doesn't appear to be available for BASH.
Sorry, like I said it is mostly for RAM usage.  Been doing some looking and found this, might help you:
[http://www.slac.stanford.edu/xorg/nmtf/nmtf-tools.html#nmp](http://www.slac.stanford.edu/xorg/nmtf/nmtf-tools.html#nmp)

---

### Post by bwitherell on 2010-03-31
Try installing wireshark on that computer to capture the packets going to and from it. That should give you a good idea of what is going on.

---

### Post by jamesisin on 2010-03-31
bwitherell - I've heard of Wireshark before (seen it mentioned around here).  I loaded it through Synaptic and will check it out when I can shut some of these applications down.  Thanks.

---

