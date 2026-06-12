---
title: "Problems with network interfaces when booting"
date: 2006-03-27
forum: General Help
---

### Post by stocksy on 2006-03-27
Hello,

I've installed Breezy from a pressed CD onto my ThinkPad 380Z, but I'm experiencing problems with the network configuration.

Here is my /etc/network/interfaces:
```

auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp
        name Wireless LAN card
        wireless_essid  xxxxxx
        #wireless_essid any
        wireless_key    xx:xx:xx:xx:xx:xx:xx:xx:xx:xx:xx:xx:xx
        wireless_mode   managed

```

It seems that Ubuntu tries to do this before PCMCIA services have started, so when my laptop finishes booting, it has no IP address.

Simply typing 'sudo /etc/init.d/networking restart' fixes this.  How can I stop it trying to start the network interface before PCMCIA cards are available?

Here is my dmesg if that helps:
[http://toastputer.net/tmp/tp-dmesg.txt](http://toastputer.net/tmp/tp-dmesg.txt)

---

### Post by AndyCooll on 2006-03-27
I'm not sure with pcmcia cards since I've only installed wireless on a box, not a laptop. However with my limited knowledge as far as I'm aware "eth0" refers to a standard ethernet network cable connection. When I've installed wireless I'd  have some details for my standard ethernet connection (eth0) and then another additional section with details for my wireless connection (wlan0 or rausb0).

It appears that your "interfaces" aren't set up properly. What do you have in System->Administration->Networking ? Is your wireless connection listed?

:cool:

---

### Post by stocksy on 2006-03-28
[QUOTE=AndyCooll]...as far as I'm aware "eth0" refers to a standard ethernet network cable connection. When I've installed wireless I'd  have some details for my standard ethernet connection (eth0) and then another additional section with details for my wireless connection (wlan0 or rausb0).

It appears that your "interfaces" aren't set up properly. What do you have in System->Administration->Networking ? Is your wireless connection listed?
[/QUOTE]

I could've been clearer when I posted this question, and I apologise for not providing all the relevant information.

I actually did a 'server' install, there is no GUI installed, since Gnome is too heavyweight for this PII 233.  The obvious implication of this is that I can't tell you what is in 'System->Administration->Networking', but I believe that it is just a frontend to configure /etc/network/interfaces?

I'm certain that this card should be detected as eth0, since the laptop has no internal ethernet interface (it's 8 years old), and the same card (Cisco aironet 350) works absolutely fine in my Dapper Drake powered Toshiba laptop (as eth1).

To clarify - there is no problem with getting the wireless connection to work with the existing settings, it just won't work *after i reboot*.

Thanks for your help so far :)

James.

---

### Post by theanorak on 2006-03-28
Are things like pcmcia services/networking started from /etc/rcX.d, where X is your current runlevel? If they are, you could check the order in there and amend the order by renaming the scripts to ensure that pcmcia starts before networking?

---

### Post by stocksy on 2006-03-29
OK, it's working.  I messed up my /etc/network/interfaces - it needs a hotplug  section:

mapping hotplug
script grep
map eth0

Now, the network interface starts with 'starting hotplug' - yippee!  Thanks all.

---

### Post by MDMS on 2008-04-08
Hey STOCKSY!

could you please summarize what you did to get Ethernet working; I'm having a similar problem.  The details are as follows:
--> IBM 380Z laptop with USB to Ethernet adapter plugged in.  This is a wired Ethernet interface.
--> I've installed Xubuntu 7.1 (and also tried 8.04) from the Alternate CD -- no problems except the following:  sound not recognized (I'll deal with that later) and NO Ethernet connectivity...
--> During initial install, Xubuntu cannot find any Ethernet interface.  However, after logging in for the first time, 'ifconfig -a' shows that Ethernet is bound to the Infrared (serial) port, which is weird and eth0 (my adapter) is there but no IP is bound to it.
--> I've tried static and dynamic IP, manual and automatic setup and absolutely nothing related to Ethernet is working (but it did work fine when I had MS Windows ME installed).

So, again, if you could summarize what you noticed from your initial installation experience and what you did to get it working, I think it might help me.

---

