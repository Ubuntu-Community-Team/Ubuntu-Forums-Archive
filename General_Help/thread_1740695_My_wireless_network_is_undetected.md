---
title: "My wireless network is undetected"
date: 2011-04-27
forum: General Help
---

### Post by mightyh on 2011-04-27
My PC has 2 systems, Windows & Ubuntu. Windows can detect my wireless network but Ubuntu can't. The Network Manager does not show any wireless network. How do I fix this problem? I'm still not very good with the Linux system but I keep trying. Thanks for any help.

---

### Post by 3rdalbum on 2011-04-27
What's the chipset of your wireless card? Have you looked in the Additional Drivers program to see if there's a driver offered for your card? (note that you'll need a hardwired/other internet connection first to download the driver).

---

### Post by mightyh on 2011-04-27
My Ubuntu says that there are no proprietary wireless driver in my system. I'm still using the Jaunty Jalopy version. However, I found some command in the older forums which I copied and this is the best information I have for my wireless card:
                     p { margin-bottom: 0.08in; }  Wireless Info
  *-network:1 UNCLAIMED  
        description: Network controller  
        product: ACX 111 54Mbps Wireless Interface  
        vendor: Texas Instruments  
        physical id: 9  
        bus info: pci@0000:00:09.0  
        version: 00  
        width: 32 bits  
        clock: 33MHz  
        capabilities: bus_master cap_list  
        configuration: latency=32  
        resources: memory:e1120000-e1121fff memory:e1100000-e111ffff  

Is it still possible to find a driver for this in the Repositories? Thanks again for any help.

---

### Post by mightyh on 2011-04-28
I can't get any solution to solving my wireless problem so I decided to remove Ubuntu from my PC. I will make a clean install of the new Ubuntu 11.04 and see what happens from there. Finding drivers for the Linux system is not a very easy task for me. That is one of the reasons I'm still hanging on to Windows (not for very long I hope). Many thanks to those who responded to my thread.:P

---

### Post by robertcoulson on 2011-04-28
Yikes

---

### Post by TBABill on 2011-04-28
A couple commands to run in a terminal to find out exactly what device you have (chipset, not brand or model number) are: ```
lspci
``` or for USB devices ```
lsusb
``` For network info ```
sudo lshw -C network
```

To know ALL drivers currently in use, then ```
lsmod
```

---

### Post by mightyh on 2011-05-08
:)Thanks, I'm gonna try these commands.

---

