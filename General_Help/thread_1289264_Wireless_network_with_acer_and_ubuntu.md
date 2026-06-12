---
title: "Wireless network with acer and ubuntu"
date: 2009-10-12
forum: General Help
---

### Post by JackTar100 on 2009-10-12
Just installed the latest ubuntu on an acer aspire laptop, first time using linux so excuse my noobness but I can't get my wireless internet to work, I have a D-Link router which my main PC(vista) runs off via ethernet and my xbox360 and another laptop(xp) run off wirelessly. 

Any help appreciated.

---

### Post by atomizer on 2009-10-12
open a terminal (applications->accessoires->Terminal) and type 
```

lshw -C network
```

This will give you a list of network-hardware you have in your PC.
Post this output here please (you can copy/paste)
Then we see what wireless card you have, so people can show you how to get the wireless working.

---

### Post by VuduMunky on 2009-10-12
i am not an ubuntu expert so my knowledge is limited. 
did you have wifi access when using the live cd ??? i found that if i just tried to install straight after booting the live cd that wifi wouldnt work but if i got working while using the live cd it would work after install.

---

### Post by JackTar100 on 2009-10-12
*-network:0              
        description: Ethernet interface  
        product: SiS900 PCI Fast Ethernet  
        vendor: Silicon Integrated Systems [SiS]  
        physical id: 4  
        bus info: pci@0000:00:04.0  
        logical name: eth0  
        version: 91  
        serial: 00:c0:9f:81:3a:e0  
        width: 32 bits  
        clock: 33MHz  
        capabilities: bus_master cap_list ethernet physical  
        configuration: broadcast=yes driver=sis900 driverversion=v1.08.10 Apr. 2 2006 latency=173 maxlatency=11 mingnt=52 module=sis900 multicast=yes  
   *-network:1  
        description: Network controller  
        product: BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller  
        vendor: Broadcom Corporation  
        physical id: b  
        bus info: pci@0000:00:0b.0  
        version: 02  
        width: 32 bits  
        clock: 33MHz  
        capabilities: bus_master  
        configuration: driver=b43-pci-bridge latency=64 module=ssb  
   *-network:0 DISABLED  
        description: Wireless interface  
        physical id: 1  
        logical name: wlan0  
        serial: 00:0e:9b:c8:1b:79  
        capabilities: ethernet physical wireless  
        configuration: broadcast=yes multicast=yes wireless=IEEE 802.11bg  
   *-network:1 DISABLED  
        description: Ethernet interface  
        physical id: 2  
        logical name: pan0  
        serial: 16:92:65:df:2a:98  
        capabilities: ethernet physical  
        configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes 



Any Help?

---

### Post by atomizer on 2009-10-12
Broadcom bcm4318 is your wireless.....

I don't have recent experience with that wireless adapter (been a few years since I had that wireless) but I think you should use the windows drivers with a program called **ndiswrapper**.

Here is a post where it is explained a bit further.[http://ubuntuforums.org/showthread.php?t=1188702]("http://ubuntuforums.org/showthread.php?t=1188702")

---

### Post by JackTar100 on 2009-10-12
This is ridiculous, I have hooked up ethernet and it is telling me there is a connection in the notification icon tray thing but I still can't connect to the internet. Wow no wonder so many people run windows if it takes this much effort just to get internet.

Thank you for all your help so far I do appreciate it but am seriously considering just installing xp and being done with it.

---

### Post by sonu 1807 on 2009-10-12
In my HP laptop.. I had broadcom wireless and nvdia graphics...after installing ubunutu, a message pops up in the taskbar which says that some third party drivers need to be installed in the system...once those drivers were installed both the nvidia and broadcom worked properly.....IN LIVE cd you will find it in system-->administration-->hardware drivers

---

### Post by JackTar100 on 2009-10-12
But it is actually telling me that I have a connection in the top right corner, the checkbox is ticked and if I click it it disconnects then I click it again and it tells me it is connected however I still can't seem to connect to the net.

---

### Post by sonu 1807 on 2009-10-12
Check whether firefox is set to work off-line in File menu of firefox...if work offline box is checked.. uncheck it

---

### Post by lrcaballero on 2009-10-12
Hi there!!!!

Left click on the internet icon on your right top corner and you should see the connections available, you should be able to see yours, if not! try restarting your laptop and check again, by default Ubuntu recognizes any wireless connection available. I also have an Acer Aspire timeline 4810TZ, I've had it for 4 weeks now and everything works GREAT!!!

Good Luck,


Luis

---

### Post by JackTar100 on 2009-10-12
> **sonu 1807 said:**
> Check whether firefox is set to work off-line in File menu of firefox...if work offline box is checked.. uncheck it

Nope was not checked.

---

### Post by JackTar100 on 2009-10-12
Bump

---

### Post by seomka on 2009-11-10
I have a similar problem. I worked in a coffee shop on wireless for four hours no problem but come home to a netgear router and a couple hours of online results in having to restart computer to connect to network. Constantly recurring and annoying problem.

---

