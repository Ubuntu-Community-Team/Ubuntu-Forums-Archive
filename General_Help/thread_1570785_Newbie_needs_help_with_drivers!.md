---
title: "Newbie needs help with drivers!"
date: 2010-09-08
forum: General Help
---

### Post by naven90 on 2010-09-08
Hey guys, I recently baught this [Acer Aspire Revo R3610]("http://www.ebuyer.com/product/200537").

It came with Linux Linpus (eww), so my first action was to install Ubuntu 10.04. However, the Acer doesnt seem to find any sort of wifi or local connection! Ive tried connecting it to internet via ethernet and wifi, but it doesnt work either way! The wifi for a start doesnt find any hotspots, but my other laptop finds plenty (including our own SKY broadband.) 

So i guess I need the drivers for it. The wireless card I believe is a Ralink 3090.

If anyone could help me out on what to do then I would be so thankful! Im just new to the linux world and dont have a clue :(

---

### Post by lukeiamyourfather on 2010-09-08
Check the hardware drivers utility. If a proprietary driver is included with Ubuntu it should be there and will have an option to install it.

---

### Post by naven90 on 2010-09-08
Hi there lukeiamyourfather,
just did and initially i got the message about it couldn't find a network so most drivers will not be available then it said that there are no propriotery drivers are in use on this system

---

### Post by lukeiamyourfather on 2010-09-08
> **naven90 said:**
> Hi there lukeiamyourfather,
just did and initially i got the message about it couldn't find a network so most drivers will not be available then it said that there are no propriotery drivers are in use on this system

Hmmm, yeah. Forgot about not having a connection. More specifics about the hardware will help to figure out if there are drivers for them or not.

```

sudo lshw -class network

```

---

### Post by Manyette on 2010-09-08
That the Ethernet connection doesn't work makes me think that you might not have had it connected during the install. This is always a mistake, just for reference.

---

### Post by 3Miro on 2010-09-08
The easiest way to install wifi drivers in Ubuntu is to get a wired connection first. Then go to System -> Admin -> Software Updates, check for updates, update the system and reboot. Afterwards, go to System -> Admin -> Hardware Drivers and a driver should be available.

(Technically once you check for updates, you don't have to install them. You can go to Hardware Drivers directly, but updating first is a bit safer and you have to update anyway)

---

### Post by lukeiamyourfather on 2010-09-08
> **Manyette said:**
> That the Ethernet connection doesn't work makes me think that you might not have had it connected during the install. This is always a mistake, just for reference.

That makes no difference. If a supported Ethernet adapter is there during the install then it will be setup for DHCP and will connect automatically if there's a cable connected. I've installed Ubuntu several times on my ThinkPad X61 without issue this way.

---

### Post by MasterNetra on 2010-09-08
hmm...for you internet connection you could get something like: [http://www.newegg.com/Product/Product.aspx?Item=N82E16833180017&cm_re=usb_wireless_adapter-_-33-180-017-_-Product](http://www.newegg.com/Product/Product.aspx?Item=N82E16833180017&cm_re=usb_wireless_adapter-_-33-180-017-_-Product)

I have this and it works fine in Ubuntu, and you can use it to connect to the net and get your drivers or at least check for them.
That is if you don't mind shelling out $12.99. Free Shipping though.

---

### Post by naven90 on 2010-09-08
*-network               
       description: Ethernet interface
       product: MCP79 Ethernet
       vendor: nVidia Corporation
       physical id: a
       bus info: pci@0000:00:0a.0
       logical name: eth0
       version: b1
       serial: 90:fb:a6:86:5f:83
       capacity: 1GB/s
       width: 32 bits
       clock: 66MHz
       capabilities: pm bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=forcedeth driverversion=0.64 latency=0 link=no maxlatency=20 mingnt=1 multicast=yes port=MII
       resources: irq:23 memory:fae7d000-fae7dfff ioport:d080(size=8) memory:fae7e800-fae7e8ff memory:fae7e400-fae7e40f
  *-network DISABLED
       description: Wireless interface
       product: RT3090 Wireless 802.11n 1T/1R PCIe
       vendor: RaLink
       physical id: 0
       bus info: pci@0000:05:00.0
       logical name: wlan0
       version: 00
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=rt3090 latency=0 multicast=yes wireless=RT2860 Wireless
       resources: irq:19 memory:febf0000-febfffff

---

### Post by lukeiamyourfather on 2010-09-08
> **naven90 said:**
> *-network               
       description: Ethernet interface
       product: MCP79 Ethernet
       vendor: nVidia Corporation
       physical id: a
       bus info: pci@0000:00:0a.0
       logical name: eth0
       version: b1
       serial: 90:fb:a6:86:5f:83
       capacity: 1GB/s
       width: 32 bits
       clock: 66MHz
       capabilities: pm bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=forcedeth driverversion=0.64 latency=0 link=no maxlatency=20 mingnt=1 multicast=yes port=MII
       resources: irq:23 memory:fae7d000-fae7dfff ioport:d080(size=8) memory:fae7e800-fae7e8ff memory:fae7e400-fae7e40f
  *-network DISABLED
       description: Wireless interface
       product: RT3090 Wireless 802.11n 1T/1R PCIe
       vendor: RaLink
       physical id: 0
       bus info: pci@0000:05:00.0
       logical name: wlan0
       version: 00
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=rt3090 latency=0 multicast=yes wireless=RT2860 Wireless
       resources: irq:19 memory:febf0000-febfffff

Looks like you should be able to connect with Ethernet to get drivers for the wireless. I did a search and found this in case you don't get anything from the hardware drivers utility.

[https://launchpad.net/~markus-tisoft/+archive/rt3090](https://launchpad.net/~markus-tisoft/+archive/rt3090)

---

### Post by lukeiamyourfather on 2010-09-08
> **MasterNetra said:**
> hmm...for you internet connection you could get something like: [http://www.newegg.com/Product/Product.aspx?Item=N82E16833180017&cm_re=usb_wireless_adapter-_-33-180-017-_-Product](http://www.newegg.com/Product/Product.aspx?Item=N82E16833180017&cm_re=usb_wireless_adapter-_-33-180-017-_-Product)

I have this and it works fine in Ubuntu, and you can use it to connect to the net and get your drivers or at least check for them.
That is if you don't mind shelling out $12.99. Free Shipping though.

In my opinion all of the options to get the current hardware working should be exhausted before purchasing more hardware. Besides, not having a dongle sticking out the side of a laptop is a major benefit of using the internal wireless.

---

### Post by lukeiamyourfather on 2010-09-08
There's a third option if all else fails. A Linux driver of sorts is provided directly by the chipset manufacturer.

[http://www.ralinktech.com/support.php?s=2](http://www.ralinktech.com/support.php?s=2)

---

### Post by naven90 on 2010-09-08
Hey guys, we had to almost rewire the whole house so that we could directly hook up the acer to the router, but we finally managed to get the internet working via ethernet! :) 

We're installing the updates for the drivers through ubuntu so we'll update you guys with what happens as it happens!

---

### Post by naven90 on 2010-09-08
Guys I got it to work! Right, so this is what I did.

1.Connected the Acer to the router directly through ethernet.
2.Installed all the updated through Ubuntu Hardware manager and stuff.
3.Went to this link: [http://www.halibutdepot.org/how_to_build_rt3090_for_ubuntu_lucid/]("http://www.halibutdepot.org/how_to_build_rt3090_for_ubuntu_lucid/") and download the .deb file near the bottom. 
4.Run and install the .deb file and voila! 
5.Reboot computer and it should have worked! :)

---

### Post by naven90 on 2010-09-08
If a mod could change the title of thread to "[solved] Acer R3610 Wireless Problem Fix" then that would be wonderful.

---

### Post by MasterNetra on 2010-09-08
> **lukeiamyourfather said:**
> In my opinion all of the options to get the current hardware working should be exhausted before purchasing more hardware. Besides, not having a dongle sticking out the side of a laptop is a major benefit of using the internal wireless.

Agreed, though it helps to get a wireless usb adapter that you know works in the event you can't get a connection otherwise. I know for me wireless is the only means I can access the internet and this laptop requires either the B43 or STA wireless driver installed, which it is not by default in Ubuntu (well in B43 its missing the bcm source and what not but regardless).


> **naven90 said:**
> If a mod could change the title of thread to "[solved] Acer R3610 Wireless Problem Fix" then that would be wonderful.

Congratz and you should be able to mark it as solved in thread tools.

---

### Post by Manyette on 2010-09-09
Not to be argumentative, but I have made that mistake with two laptops, and on both occasions I had a terrible time getting the Ethernet working.  With it connected, it set it up without any problem.  Once on an HP, and once on an Acer, so I suspect it may be machine or rather wirless chip specific, but I assure you, in some cases, it does make a difference. Twice neanss I'm a slow learner, I guess!

---

