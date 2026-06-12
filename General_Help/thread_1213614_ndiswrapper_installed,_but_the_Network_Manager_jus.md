---
title: "ndiswrapper installed, but the Network Manager just won't connect"
date: 2009-07-15
forum: General Help
---

### Post by Java Geek on 2009-07-15
[FONT="Franklin Gothic Medium"]Hello, I recently changed my Desktop Manager to KDE, but in the process, I reverted all my apps to factory default. After logging onto windows and downloading NDISwrapper, I installed it on Kubuntu.

I installed my drivers properly (I think) and the Network Manager still cannot connect to any networks, encrypted or not. I am in need of great assistance so any help is appreciated.

(Note: I am on Windows so it may take a while for me to post code that is necessary to diagnose the situation.[/FONT]

---

### Post by Screwdriver0815 on 2009-07-15
I assume you are asking regarding wireless LAN? 

Is it like this that the KNetworkmanager asks for the password, tries to connect and asks for the password again... and again... and again? 

This is because the KDE-Networkmanager is buggy like... 

the best way to overcome this is to install the gnome-networkmanager and to uninstall KNetworkmanager.
But I don't know what this does to your drivers and Ndiswrapper stuff.

---

### Post by Java Geek on 2009-07-15
Hmm thanks...my problem is that i cant download anything from my ubuntu system and i have to do it all from windows. Right now, i am attempting to install wicd. OH! And knetworkmanager was purged so i have no clue what to do except continue to fix wicd.e download links to help me, i would highly appreciate it.

---

### Post by Cup of Squirrels on 2009-07-15
Can you see the device and its relevant driver installed when you use "sudo lshw -C network"?

---

### Post by Java Geek on 2009-07-15
The output is:
```

  *-network:0 DISABLED                         
       description: Ethernet interface         
       product: NC100 Network Everywhere Fast Ethernet 10/100
       vendor: ADMtek                                        
       physical id: 1
       bus info: pci@0000:02:01.0
       logical name: eth0
       version: 11
       serial: 00:04:5a:89:9e:5a
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=tulip driverversion=1.1.15 latency=32 maxlatency=128 mingnt=64 module=tulip multicast=yes
  *-network:1 DISABLED
       description: Wireless interface
       product: AR5008 Wireless Network Adapter
       vendor: Atheros Communications Inc.
       physical id: 2
       bus info: pci@0000:02:02.0
       logical name: wlan0
       version: 01
       serial: 00:1b:11:e8:71:a9
       width: 32 bits
       clock: 66MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper+net5416 driverversion=1.55+,07/23/2007,6.0.3.107 latency=128 link=no module=ndiswrapper multicast=yes wireless=IEEE 802.11g
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: 1a:15:c7:5a:c1:d0
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes

```

---

