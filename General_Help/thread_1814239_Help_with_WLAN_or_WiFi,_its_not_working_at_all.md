---
title: "Help with WLAN or WiFi, its not working at all"
date: 2011-07-29
forum: General Help
---

### Post by wanttomasterlinux on 2011-07-29
Guys its my second post coz the first one didn't help :( please help, I am new to Linux and neither LAN or WLAN seem to work

Here's some information that might help to solve the problem
on typing.........
sudo lshw
{Content trimmed}

*-network
description: Network controller
product: BCM4311 802.11b/g WLAN
vendor: Broadcom Corporation
physical id: 0
bus info: pci@0000:0b:00.0
version: 01
width: 32 bits
clock: 33MHz
capabilities: pm msi pciexpress bus_master cap_list
configuration: driver=b43-pci-bridge latency=0
resources: irq:16 memory:efcfc000-efcfffff

{Content trimmed}

*-network DISABLED
description: Wireless interface
physical id: 1
logical name: wlan0
serial: 00:19:7e:a0:59:a7
capabilities: ethernet physical wireless
configuration: broadcast=yes driver=b43 driverversion=2.6.38-8-generic fir

as you can see, it identifies my wlan device and uses a driver named b43, but then it says in the end and network is DISABLED!!! grrrrh

I tried to enable it by using the commmad sudo modprobe b43 (b43 is the name of the driver used by linux), then i checked again using.....

lsmod

Module Size Used by
b44 35301 0 
arc4 12473 2 
b43 296610 0 
mac80211 257001 1 b43
cfg80211 156212 2 b43,mac80211
parport_pc 32111 0 
ppdev 12849 0 

good, it shows the module b43 is loaded successfully

then typed


lshw -c network

*-network 
description: Network controller
product: BCM4311 802.11b/g WLAN
vendor: Broadcom Corporation
physical id: 0
bus info: pci@0000:0b:00.0
version: 01
width: 32 bits
clock: 33MHz
capabilities: bus_master cap_list
configuration: driver=b43-pci-bridge latency=0
resources: irq:16 memory:efcfc000-efcfffff

network DISABLED
description: Wireless interface
physical id: 1
logical name: wlan0
serial: 00:19:7e:a0:59:a7
capabilities: ethernet physical wireless
configuration: broadcast=yes driver=b43 driverversion=2.6.38-8-generic fir


same thing again, it tells me that "your Wlan device is working perfectly fine, but wait..........actually its not working, you have disabled it sir" , I just have one thing to say, "wtf is wrong with ya bloody damn laptop" 
Apologies, I sometimes curse my laptop, we understand each other 

plzzz helppppppppppppppppp

---

### Post by gandaran on 2011-07-29
with this thread you can find out what exact drivers and firmware you need to install for broadcom devices, hope it'll help fix the problem.
[http://ubuntuforums.org/showpost.php?p=10796508&postcount=44](http://ubuntuforums.org/showpost.php?p=10796508&postcount=44)

---

### Post by josephmills on 2011-07-29
I was just about to ask for a lspci -nn | grep 14e4 

let us know if you get hung up i do need to update that post 


:popcorn::popcorn:

---

### Post by wanttomasterlinux on 2011-07-29
@ Joseph I liked your post, but I am not really sure which one to install
My driver is BCM4311.According to information provided in the synaptic manager, the driver already installed on my Linux should work fine for me, but apparently it doesn't. And I am little bit unsure whether or not to uninstall that existing driver (which claims to be the right one for my device).
Other thing is, you didn't tell how to install b43sta without an internet connection. My gut feeling is, b43sta might work for me, coz it worked for many other users too!(my wired internet i.e eth0 is not working as well, Linux sucks in this case!!!)

reply soon, I'll really wait for your reply :)

---

### Post by lordleemo1 on 2011-07-29
> **wanttomasterlinux said:**
> @ Joseph I liked your post, but I am not really sure which one to install
My driver is BCM4311.According to information provided in the synaptic manager, the driver already installed on my Linux should work fine for me, but apparently it doesn't. And I am little bit unsure whether or not to uninstall that existing driver (which claims to be the right one for my device).
Other thing is, you didn't tell how to install b43sta without an internet connection. My gut feeling is, b43sta might work for me, coz it worked for many other users too!(my wired internet i.e eth0 is not working as well, Linux sucks in this case!!!)

reply soon, I'll really wait for your reply :)

I take it you have a cd or usb with a copy of Ubuntu on!! insert cd/usb navigate to the Pool folder,then to the Restricted folder,then to the B folder,then to the bcmwl folder. and install the bcmwl-kernel-source..If you have an internet connection on another machine!! Dl bcmwl-kernel-source stick it on a usb and do it that way...

---

### Post by wanttomasterlinux on 2011-07-29
Thanks for the reply
Well I figured that out on unbuntu documentation and uninstalled bcmwl-kernel-source and installed fwcutter thingy, and it didn't work, as expected 
(this Linux is about negative thoughts i.e. they are not serious when they are saying "its better than windows"). I'm being persistent in learning but apparently that didn't even teach me how to install a thing, let alone troubleshooting! :D

anyway, any other solution? :(

---

### Post by wanttomasterlinux on 2011-07-31
> **lordleemo1 said:**
> I take it you have a cd or usb with a copy of Ubuntu on!! insert cd/usb navigate to the Pool folder,then to the Restricted folder,then to the B folder,then to the bcmwl folder. and install the bcmwl-kernel-source..If you have an internet connection on another machine!! Dl bcmwl-kernel-source stick it on a usb and do it that way...

Thanks to joseph, it workeddddddddddddddddddddddd :D

So heres what I did, I first un-installed everything that said BCM- from everything i mean everything (from synaptic manager). I then installed tar,gz file posted on josephs thread! restarted and now my wireless is working fine. I think original b43 driver did&#324;t work for me.

---

