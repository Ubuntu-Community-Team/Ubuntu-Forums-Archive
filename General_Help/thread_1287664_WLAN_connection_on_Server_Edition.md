---
title: "WLAN connection on Server Edition"
date: 2009-10-10
forum: General Help
---

### Post by andsch on 2009-10-10
Hi all!
I've been searhing for days, to solve my problem.

I have a machine running Ubuntu Server Edition (hardy). By now, it has a wired connection to the router, but I would like to connect it via WLAN.

I've tried:
iwlist scan

But it doesn't regonize any networks.

I think the problem is, missing drivers for the wlan-card.

However by typing:
lspci | grep Network

It prints my WLAN card:
Network controller: Intel Corporation PRO/Wireless 3945ABG Network Connection (rev 02)

BTW there's no light in the WiFi-indicator.

What to do? :D

---

### Post by delcypher on 2009-10-10
First step is to see if a kernel module (driver) is loaded for your wireless card.

```
lspci -k
```

and then find your card (probably at the bottom of the list)

Mine is like this..> 05:03.0 Network controller: RaLink RT2561/RT61 802.11g PCI
	Kernel driver in use: rt61pci
	Kernel modules: rt61pci


If your card has no kernel modules loaded then you will either need to... 

1. upgrade to a kernel that has a module for your card
2. Find the source code for the module for your card and compile it yourself
3. Use ndiswrapper (a tool to load windows xp/vista wireless drivers in linux)

If you do have a kernel module loaded for your card then good news!

1. List the interfaces
```
iwconfig
```

You should have something like wlan0 or wlan1 in there

2. Bring the interface up (where wlan0 is your wireless interface)
```
sudo ifconfig wlan0 up
```

3. Now try scanning for wireless networks.
```
iwlist wlan0 scan
```

4. Set the ESSID of the network you want to join
```
iwconfig wlan0 ESSID "my network name"
```

If you find wireless networks this is where it get's complicated. If your wireless network uses WPA/WPA2 (it should NOT be using WEP that's insecure) then you will to use a tool called wpa_supplicant (probably need wpa_passphrase too) to authenticate first before either setting your IP address manually (using ifconfig) or getting your ip automatically using dhclient.

Read the man pages for wpa_supplicant , wpa_supplicant.conf & wpa_passphrase for help there.

How far through the steps I've listed can you get?

---

### Post by andsch on 2009-10-11
Okay, can't get anything to work :S Im stuck with the first command:
```
lspci -k
```
It just returns:
```
lspci: invalid option --k
```
And a list of valid options.

---

### Post by delcypher on 2009-10-11
```
Display options:
-v		Be verbose (-vv for very verbose)
-k		Show kernel drivers handling each device
-x		Show hex-dump of the standard part of the config space
-xxx		Show hex-dump of the whole config space (dangerous; root only)
-xxxx		Show hex-dump of the 4096-byte extended config space (root only)
-b		Bus-centric view (addresses and IRQ's as seen by the bus)
-D		Always show domain numbers

```

Is some of the options available, find the option in your version of lspci to "Show Kernel drivers handling each device)

to get more info on the lspci command run (press q to quit, h for help)
```
man lspci
```

---

### Post by andsch on 2009-10-11
Can't find it :S

I've just tried ndiswrapper. followed this thread [http://ubuntuforums.org/showthread.php?t=571129](http://ubuntuforums.org/showthread.php?t=571129)

But without succes (i think). But i got some things i can conclude, maybe it can help:

```
iwlist wlan0 power
```
Returns:
```
wlan0   Current mode:off
```
Dont know what this actually means, but i dont think it's good news ;) I've turned on the wireless radio, but still no light in the indicator :(

```
lshw -C network
```
Returns:
```
*-network **DISABLED**
description: Wireless interface
product: PRO/Wireless 3945ABG Network Connection
vendor: Intel Corporation
physical id: 0
bus info: pci@0000:04:00.0
logical name: wmaster0
version: 02
serial: 00:1c:bf:02:75:84
width: 32 bits
clock: 33MHz
capabilities: bus_master cap_list logical ethernet physical wireless
configuration: broadcast=yes **driver=iwl3945** latency=0 module=iwl3945 multicast=yes wireless=I
EEE 802.11g

*-network

....The whole Ethernet interface...
```

How to set the *-network to **ENABLED**?

Or what else to do? :)

---

### Post by delcypher on 2009-10-11
You can run iwlist and your wireless interface appears to be present so you have some tools, follow the commands I gave you from the first post from "iwconfig" onwards.

I'm using my wireless card right now and ```
iwlist wlan1 power
``` returns the "Current mode:off" message too so pay no notice to it for now.

Also as extra thought, do you have the package wireless-tools installed?

---

### Post by andsch on 2009-10-13
Also as extra thought, do you have the package wireless-tools installed?

Now I've installed wireless-tools (i think). I just typed:
```
sudo aptitude install wireless-tools
```
Right?

When I type:
```
iwconfig
```
It returns:
```

lo       no wireless extensions
eth0     no wireless extensions
wmaster  no wireless extensions
wlan0    IEEE 802.11g ESSID:""  Nickname:""
Mode:Managed Frequency:2.412 GHz  Acces Point: Not-Associated
Tx-Power=27dBm
Retry min limit:7  RTS thr:off   Fragment thr=2346 B
Power Management:off
Link Quality:0  Signal level:0  Noise level:0
Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
Tx excessive retries:0   Invalid misc:0   Missed beacon:0

```

Hope that can help :)

---

### Post by P4man on 2009-10-13
Gonna suggest something really silly. Right click network manager (top right) and select 'enable wireless".

---

### Post by andsch on 2009-10-13
Okay got some more :P

I just typed:
```
sudo iwconfig wlan0 ESSID "My network Name"
```

And then:
```
iwlist wlan0 scan
```
Returned:
```
wlan0 scan completed:
...............................
```

But how to connect?

---

### Post by andsch on 2009-10-13
> **P4man said:**
> Gonna suggest something really silly. Right click network manager (top right) and select 'enable wireless".

It's a Server Edition == No GUI

---

