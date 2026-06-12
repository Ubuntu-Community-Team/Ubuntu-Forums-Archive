---
title: "Help setting up multiple graphic adapters."
date: 2010-09-23
forum: General Help
---

### Post by proxxx on 2010-09-23
Hello,


#A short introduction.

#I have been using ubuntu 10.04 for a couple months now.
#As a new newbie to linux in general I am doing my best to gain #understanding and learning as much as i can.

#I have installed ubuntu on a couple of systems already , bumping #my head :P
#Yet learned a lot of stuff , especially on the older system.
#Resulting in a small insight concerning graphic drivers. 



Anyway, here goes.

I have bought a new old system for a couple of bucks.
It's equipped with 2 graphic adapters.
I would like to use both cards on separate monitors.

- Ati xpress 200 (rc410)  (onboard chipset)
- Ati X300 PCI-E

The PCI card I already owned before buying the system, 
I use this as my main adapter , it being stronger then the onboard.
The 'primary adapter" runs fine on the mesa driver.
It worked out of the box.

My lspci :

> 
00:00.0 Host bridge: ATI Technologies Inc Radeon Xpress 200 Host Bridge (rev 01)
00:02.0 PCI bridge: ATI Technologies Inc RS480 PCI-X Root Port
00:11.0 IDE interface: ATI Technologies Inc IXP SB400 Serial ATA Controller (rev 80)
00:12.0 IDE interface: ATI Technologies Inc IXP SB400 Serial ATA Controller (rev 80)
00:13.0 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller (rev 80)
00:13.1 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller (rev 80)
00:13.2 USB Controller: ATI Technologies Inc IXP SB400 USB2 Host Controller (rev 80)
00:14.0 SMBus: ATI Technologies Inc IXP SB400 SMBus Controller (rev 81)
00:14.1 IDE interface: ATI Technologies Inc IXP SB400 IDE Controller (rev 80)
00:14.2 Audio device: ATI Technologies Inc IXP SB4x0 High Definition Audio Controller (rev 01)
00:14.3 ISA bridge: ATI Technologies Inc IXP SB400 PCI-ISA Bridge (rev 80)
00:14.4 PCI bridge: ATI Technologies Inc IXP SB400 PCI-PCI Bridge (rev 80)
01:00.0 VGA compatible controller: ATI Technologies Inc RV370 5B60 [Radeon X300 (PCIE)]
01:00.1 Display controller: ATI Technologies Inc RV370 [Radeon X300SE]
02:02.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
02:03.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8169 Gigabit Ethernet (rev 10)


From this point I am rather lost.
By default i dont have a xorg.conf file.


Can anyone help me to setup this configuration?




#I know , i should buy nvidia :P

---

### Post by proxxx on 2010-09-24
Anyone ??

---

