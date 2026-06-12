---
title: "No wireless networks found"
date: 2011-06-30
forum: General Help
---

### Post by O-pos on 2011-06-30
Hello,

I upgraded to Ubuntu 11.04, and the wireless was working fine until now when it does not recognize anything and says "No wireless networks found". If I plug the cable into my laptop, then it works (that's how I am communicating right now). I am not sure what the problem is, hardware or software. Could you help?

---

### Post by TeoBigusGeekus on 2011-06-30
Have you searched in Hardware Drivers whether there is a proprietary driver for your wireless card?

---

### Post by O-pos on 2011-06-30
No, how do I do that?

But it was working fine on the new OS.. Would it still have to do with the hardware driver?

---

### Post by TeoBigusGeekus on 2011-06-30
> **O-pos said:**
> Would it still have to do with the hardware driver?
Could be...

Now, I assume you use unity: search for Additional (or Hardware) Drivers with the top left menu thingy.
Once you find it, open it and see if there's a driver for your card.

---

### Post by O-pos on 2011-06-30
I have the classic view, I did not understand the new desktop. How do I do it in the classic view?

---

### Post by TeoBigusGeekus on 2011-06-30
> **O-pos said:**
> I have the classic view, I did not understand the new desktop. How do I do it in the classic view?

Ah, good, I hate unity...

Go to Administration->System->Hardware (or Additional) Drivers.

---

### Post by O-pos on 2011-06-30
ok, I did and it says that no proprietary drivers are in use on this system

---

### Post by TeoBigusGeekus on 2011-06-30
Are there no available ones?

---

### Post by O-pos on 2011-06-30
I assume not, at least nothing is listed

---

### Post by life in color on 2011-06-30
Had the same problem, are you using a Broadcom Wireless card?

---

### Post by O-pos on 2011-06-30
Not sure what card I am using, I have a HP pavilion dv2000t laptop..

---

### Post by dFlyer on 2011-06-30
Are you dual booting, if so can you connect wifi under windows. About 6 months ago I have a NetGEAR wireless router get fried and had to replace it.

---

### Post by TeoBigusGeekus on 2011-06-30
```
lshw -C network
```

---

### Post by O-pos on 2011-06-30
No dual boot, just Ubuntu (got sick of Windows)

Here is the output to the code:


:~$ sudo lshw -C network
[sudo] password for pos: 
  *-network               
       description: Ethernet interface
       product: 88E8039 PCI-E Fast Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:05:00.0
       logical name: eth0
       version: 14
       serial: 00:16:d3:f8:26:5e
       size: 100Mbit/s
       capacity: 100Mbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=sky2 driverversion=1.28 duplex=full firmware=N/A ip=192.168.0.12 latency=0 link=yes multicast=yes port=twisted pair speed=100Mbit/s
       resources: irq:44 memory:f4200000-f4203fff ioport:3000(size=256)
  *-network DISABLED
       description: Wireless interface
       product: PRO/Wireless 3945ABG [Golan] Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:07:00.0
       logical name: wlan0
       version: 02
       serial: 00:1c:bf:27:ba:98
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=iwl3945 driverversion=2.6.38-8-generic firmware=N/A latency=0 link=no multicast=yes wireless=IEEE 802.11abg
       resources: irq:47 memory:f4300000-f4300fff

---

### Post by life in color on 2011-06-30
I have an HP Pavilion as well so I assume you have a broadcom wireless card which are terrrrrible for linux but they will work if you try EVERYTHING let me see if I can find the thread that helped me.

---

### Post by TeoBigusGeekus on 2011-06-30
> **O-pos said:**
> 
       description: Wireless interface
       product: PRO/Wireless 3945ABG [Golan] Network Connection
       vendor: Intel Corporation

See [this]("http://ubuntuforums.org/showthread.php?t=1689100").

---

### Post by life in color on 2011-06-30
> 
See this.

I agree Chili555 helped fix my WiFi, definitely check that out.

---

### Post by O-pos on 2011-06-30
rkfill says:

:~$ rfkill list all
0: hp-wifi: Wireless LAN
	Soft blocked: yes
	Hard blocked: no
1: phy0: Wireless LAN
	Soft blocked: yes
	Hard blocked: yes


dmesg says:

:~$ dmesg | grep iwl
[    5.593297] iwl3945: Intel(R) PRO/Wireless 3945ABG/BG Network Connection driver for Linux, in-tree:s
[    5.593301] iwl3945: Copyright(c) 2003-2010 Intel Corporation
[    5.593368] iwl3945 0000:07:00.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[    5.593383] iwl3945 0000:07:00.0: setting latency timer to 64
[    5.648668] iwl3945 0000:07:00.0: Tunable channels: 11 802.11bg, 13 802.11a channels
[    5.648672] iwl3945 0000:07:00.0: Detected Intel Wireless WiFi Link 3945ABG
[    5.648824] iwl3945 0000:07:00.0: irq 47 for MSI/MSI-X
[    5.775416] ieee80211 phy0: Selected rate control algorithm 'iwl-3945-rs'

---

### Post by O-pos on 2011-06-30
It appears that the block was in the software.

sudo rfkill unblock all

This command did the wonder :)

---

### Post by life in color on 2011-06-30
```

It appears that the block was in the software.

sudo rfkill unblock all

This command did the wonder 

```
I guess we had different problems than I'm glad to hear it was an easy fix, mine wasn't that way at all O.0

---

### Post by TeoBigusGeekus on 2011-06-30
> **O-pos said:**
> It appears that the block was in the software.

sudo rfkill unblock all

This command did the wonder :)

Brilliant! Don't forget to mark the thread as solved.

---

### Post by O-pos on 2011-06-30
How do I mark it solved>

---

### Post by TeoBigusGeekus on 2011-06-30
Thread tools->Mark as solved.

---

### Post by O-pos on 2011-06-30
Thanks again guys

---

