---
title: "begginer needs help with wireless card"
date: 2009-11-12
forum: General Help
---

### Post by farfenwaffle on 2009-11-12
Hello! I recently got a Dell Optiplex(gx110) with Ubuntu 8.04 but it did not have any wireless card. I went and bought a wireless g pci adapter and put it into the pci slot.

I have absolutely no idea what to do now. The cd that it came with is for windows xp, so i guess i need some sort of driver? I would love anything that could help, thanks!
:D

Update: card is wg311v3

---

### Post by The Funkbomb on 2009-11-12
What card did you get?

Next thing we need to figure out is if Ubuntu is recognizing it.

Go into terminal and type:

```
sudo lshw -C Network
```

Copy and paste the output here.  Paste it in [noparse]```
 
```[/noparse] by clicking the # button on top.

---

### Post by farfenwaffle on 2009-11-12
Funkbomb, i would do that if my linux i am using had internet. I am using my xp to post. What is the information I need to get from the output?

---

### Post by The Funkbomb on 2009-11-12
Basically, we're looking to see if your wireless card is recognized by Ubuntu.

Plug in a thumb drive to your Ubuntu machine, copy it to gedit/text editor, save it and bring it over to XP.  Paste it here.

---

### Post by farfenwaffle on 2009-11-12
Alright, here is the output I got:
```
  *-network:0 UNCLAIMED   
       description: Ethernet controller
       product: 88w8335 [Libertas] 802.11b/g Wireless
       vendor: Marvell Technology Group Ltd.
       physical id: b
       bus info: pci@0000:01:0b.0
       version: 03
       width: 32 bits
       clock: 66MHz
       capabilities: pm bus_master cap_list
       configuration: latency=64
  *-network:1
       description: Ethernet interface
       product: 3c905C-TX/TX-M [Tornado]
       vendor: 3Com Corporation
       physical id: c
       bus info: pci@0000:01:0c.0
       logical name: eth0
       version: 78
       serial: 00:b0:d0:99:70:dd
       size: 10MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=3c59x duplex=half latency=64 link=no maxlatency=10 mingnt=10 module=3c59x multicast=yes port=MII speed=10MB/s

```

---

### Post by ghostborg on 2009-11-12
You could try installing ndiswrapper from synaptic and use your windows driver inf file.

Of course, you would need to use a lan connection to DL ndiswrapper.
Try inserting the Ubuntu CDROM , it might be on there.

From your XP machine search the Ubuntuforums for your pci card and see what people recommend.

Another alternative is to try Ubuntu 9.10 Live and see if it works out of the box. Then install if you wish.

---

### Post by sawick61 on 2009-11-12
Did you try looking on the manufacturer's website for your wireless nic to see if they offer a linux driver?

---

### Post by The Funkbomb on 2009-11-12
You could also plug in via ethernet and see if you can find proprietary drivers in System>Administration>Hardware Drivers

---

### Post by sawick61 on 2009-11-12
> **The Funkbomb said:**
> You could also plug in via ethernet and see if you can find proprietary drivers in System>Administration>Hardware Drivers

if the card manufacturer doesnt have support for the driver and ubuntu ultimately doesn't recognize it.  if you are able to plug into ethernet, see below...

[https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper)

---

### Post by farfenwaffle on 2009-11-12
I wonder, it says on the output I posted that the vendor is 3com isn't that a completely different producer of adapters? do you think it recognizes the card?

---

### Post by sawick61 on 2009-11-13
> **farfenwaffle said:**
> I wonder, it says on the output I posted that the vendor is 3com isn't that a completely different producer of adapters? do you think it recognizes the card?

the 3 com interface appears to be LAN aka ethernet aka cat 5.  it is the one listed above that appears to be your wireless.  and its not listed as dell because thats likely the open source driver currently installed to the system..which is incompatible with your card..which is why it isn't working.  follow the steps in the link i included above and it will resolve any issue ur having.

---

### Post by sawick61 on 2009-11-13
> **sawick61 said:**
> the 3 com interface appears to be LAN aka ethernet aka cat 5.  it is the one listed above that appears to be your wireless.  and its not listed as dell because thats likely the open source driver currently installed to the system..which is incompatible with your card..which is why it isn't working.  follow the steps in the link i included above and it will resolve any issue ur having.

but before doing that, do what some other guy suggested and if you can, plug ur linux box up to internet if possible and click system | administration | hard ware drivers, and see if there is a download for yours thru there.

---

