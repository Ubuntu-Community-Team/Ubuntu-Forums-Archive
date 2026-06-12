---
title: "The demon Broadcom situation..."
date: 2011-05-22
forum: General Help
---

### Post by labtek on 2011-05-22
Hello to the group.

Is there a vision of a final simple fix for the Broadcom WiFi issue that seems to be plaguing us these days?

It seems to be a "perfect storm" for driving new converts away from Ubuntu since most people would be using laptops and netbooks with wireless cards not working in Ubuntu. This would be an operational disaster for these folks. Of most people exploring Linux as an alternative to Windows, most would look at Ubuntu first according to some information that I've seen recently.

While trying to configure a wireless card with Ubuntu 10.10 in my Acer Aspire 5100 laptop recently, I was forced to work in Terminal, which reminded me a lot of the old DOS days in which something as little as a missed backslash or some other small error would result in the failure of the command. At it's best, it resulted in much fiddling and twiddling in an area that I preferred not to be.

I'm not a Linux newbie since I've come up through the various early distros of PCLOS, Mepis, Xandros and some others and I understand that one must be prepared to work with the software to get it to work.

Awhile ago, we had a similar situation with NVIDIA video cards that now seems to have been resolved.

Maybe the Broadcom situation will develop in a similar fashion.

---

### Post by dragonfly41 on 2011-05-22
I'm struggling right now to get an Acer Aspire 3613WLMi to install ubuntu 10.10 (installs o.k.) but there is no Internet (wired) connection. An old notebook I know.   My ubuntu 10.10 and internet connection runs o.k. on Dell Inspiron.

I have Broadcom on the Acer which until recently ran Win XP.

I've tried different LiveCD's

ubuntu 10.10
Parted Magic
xubuntu 10.10
Linux Mint
pclinuxOS

but still can't see an Internet connection.

Is there a basic incompatibility between Acer and Linux .. although I've read that some Acer users have installed Linux.   What is the Broadcom issue referred to?

---

### Post by gandaran on 2011-05-22
> **dragonfly41 said:**
> I'm struggling right now to get an Acer Aspire 3613WLMi to install ubuntu 10.10 (installs o.k.) but there is no Internet (wired) connection. An old notebook I know.   My ubuntu 10.10 and internet connection runs o.k. on Dell Inspiron.

I have Broadcom on the Acer which until recently ran Win XP.

I've tried different LiveCD's

ubuntu 10.10
Parted Magic
xubuntu 10.10
Linux Mint
pclinuxOS

but still can't see an Internet connection.

Is there a basic incompatibility between Acer and Linux .. although I've read that some Acer users have installed Linux.   What is the Broadcom issue referred to?
linux runs fine on acer computers and broadcom drivers are just proprietary software so they cant be included in the linux kernel, but Ubuntu provides them in system » administration » hardware/additional drivers after connecting to wired internet first and updating the software package list, then you only have to enable the driver.
if you have problems with hardware drivers please always post the output of typing this code in terminal
```
lspci
```
so we can see the hardware and help find the appropriate driver.

---

### Post by dragonfly41 on 2011-05-22
Thanks for confirmation that Linux works on Acer.

I posted results of sudo lspci in this thread ..

[http://ubuntuforums.org/showthread.php?t=1764313](http://ubuntuforums.org/showthread.php?t=1764313)

```

sudo lspci -k

00:00.0 Host bridge: Intel Corporation Mobile 915GM/PM/GMS/910GML Express Processor to DRAM Controller (rev 03)
    Subsystem: Acer Incorporated [ALI] Device 006a
    Kernel driver in use: agpgart-intel
    Kernel modules: intel-agp
00:02.0 VGA compatible controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 03)
    Subsystem: Acer Incorporated [ALI] Device 006a
    Kernel driver in use: i915
    Kernel modules: i915
00:02.1 Display controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 03)
    Subsystem: Acer Incorporated [ALI] Device 006a
00:1d.0 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 (rev 03)
    Subsystem: Acer Incorporated [ALI] Device 006a
    Kernel driver in use: uhci_hcd
00:1d.1 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 (rev 03)
    Subsystem: Acer Incorporated [ALI] Device 006a
    Kernel driver in use: uhci_hcd
00:1d.2 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 (rev 03)
    Subsystem: Acer Incorporated [ALI] Device 006a
    Kernel driver in use: uhci_hcd
00:1d.3 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 (rev 03)
    Subsystem: Acer Incorporated [ALI] Device 006a
    Kernel driver in use: uhci_hcd
00:1d.7 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller (rev 03)
    Subsystem: Acer Incorporated [ALI] Device 006a
    Kernel driver in use: ehci_hcd
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev d3)
00:1e.2 Multimedia audio controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Audio Controller (rev 03)
    Subsystem: Acer Incorporated [ALI] Realtek ALC 655 codec (in Acer TravelMate 2410 serie laptop)
    Kernel driver in use: Intel ICH
    Kernel modules: snd-intel8x0
00:1e.3 Modem: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Modem Controller (rev 03)
    Subsystem: Acer Incorporated [ALI] Conexant AC'97 CoDec (in Acer TravelMate 2410 serie laptop)
    Kernel modules: snd-intel8x0m
00:1f.0 ISA bridge: Intel Corporation 82801FBM (ICH6M) LPC Interface Bridge (rev 03)
    Subsystem: Acer Incorporated [ALI] Device 006a
    Kernel modules: iTCO_wdt, intel-rng
00:1f.1 IDE interface: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) IDE Controller (rev 03)
    Subsystem: Acer Incorporated [ALI] Device 006a
    Kernel driver in use: ata_piix
00:1f.3 SMBus: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) SMBus Controller (rev 03)
    Subsystem: Acer Incorporated [ALI] Device 006a
    Kernel modules: i2c-i801
06:05.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)
    Subsystem: AMBIT Microsystem Corp. TravelMate 2410
    Kernel driver in use: b43-pci-bridge
    Kernel modules: ssb
06:07.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
    Subsystem: Acer Incorporated [ALI] Device 006a
    Kernel driver in use: 8139too
    Kernel modules: 8139too, 8139cp
06:09.0 CardBus bridge: ENE Technology Inc CB1410 Cardbus Controller (rev 01)
    Subsystem: Acer Incorporated [ALI] Device 006a
    Kernel driver in use: yenta_cardbus
    Kernel modules: yenta_socket


```then ..

```

sudo ifconfig

eth0      Link encap:Ethernet  HWaddr 00:0a:e4:e5:cc:10  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:20 Base address:0x3000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:552 errors:0 dropped:0 overruns:0 frame:0
          TX packets:552 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:43328 (43.3 KB)  TX bytes:43328 (43.3 KB)


```I inspected > System > Administration > Additional Drivers

The result is ..

No proprietary drivers are in use in this system.

[EDIT]

When I tried LiveCD PCLinuxOS

there was no internet connection but this was detected ..

eth0: Realtek SemiConductor Ltd. RTL-8139/8139C/8139C+

Network is down in interface
Wired (Ethernet) (eth0)

---

### Post by gandaran on 2011-05-22
> **dragonfly41 said:**
> Thanks for confirmation that Linux works on Acer.

I posted results of sudo lspci in this thread ..

[http://ubuntuforums.org/showthread.php?t=1764313](http://ubuntuforums.org/showthread.php?t=1764313)

```

sudo lspci -k

00:00.0 Host bridge: Intel Corporation Mobile 915GM/PM/GMS/910GML Express Processor to DRAM Controller (rev 03)
    Subsystem: Acer Incorporated [ALI] Device 006a
    Kernel driver in use: agpgart-intel
    Kernel modules: intel-agp
00:02.0 VGA compatible controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 03)
    Subsystem: Acer Incorporated [ALI] Device 006a
    Kernel driver in use: i915
    Kernel modules: i915
00:02.1 Display controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 03)
    Subsystem: Acer Incorporated [ALI] Device 006a
00:1d.0 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 (rev 03)
    Subsystem: Acer Incorporated [ALI] Device 006a
    Kernel driver in use: uhci_hcd
00:1d.1 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 (rev 03)
    Subsystem: Acer Incorporated [ALI] Device 006a
    Kernel driver in use: uhci_hcd
00:1d.2 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 (rev 03)
    Subsystem: Acer Incorporated [ALI] Device 006a
    Kernel driver in use: uhci_hcd
00:1d.3 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 (rev 03)
    Subsystem: Acer Incorporated [ALI] Device 006a
    Kernel driver in use: uhci_hcd
00:1d.7 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller (rev 03)
    Subsystem: Acer Incorporated [ALI] Device 006a
    Kernel driver in use: ehci_hcd
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev d3)
00:1e.2 Multimedia audio controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Audio Controller (rev 03)
    Subsystem: Acer Incorporated [ALI] Realtek ALC 655 codec (in Acer TravelMate 2410 serie laptop)
    Kernel driver in use: Intel ICH
    Kernel modules: snd-intel8x0
00:1e.3 Modem: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Modem Controller (rev 03)
    Subsystem: Acer Incorporated [ALI] Conexant AC'97 CoDec (in Acer TravelMate 2410 serie laptop)
    Kernel modules: snd-intel8x0m
00:1f.0 ISA bridge: Intel Corporation 82801FBM (ICH6M) LPC Interface Bridge (rev 03)
    Subsystem: Acer Incorporated [ALI] Device 006a
    Kernel modules: iTCO_wdt, intel-rng
00:1f.1 IDE interface: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) IDE Controller (rev 03)
    Subsystem: Acer Incorporated [ALI] Device 006a
    Kernel driver in use: ata_piix
00:1f.3 SMBus: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) SMBus Controller (rev 03)
    Subsystem: Acer Incorporated [ALI] Device 006a
    Kernel modules: i2c-i801
06:05.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)
    Subsystem: AMBIT Microsystem Corp. TravelMate 2410
    Kernel driver in use: b43-pci-bridge
    Kernel modules: ssb
06:07.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
    Subsystem: Acer Incorporated [ALI] Device 006a
    Kernel driver in use: 8139too
    Kernel modules: 8139too, 8139cp
06:09.0 CardBus bridge: ENE Technology Inc CB1410 Cardbus Controller (rev 01)
    Subsystem: Acer Incorporated [ALI] Device 006a
    Kernel driver in use: yenta_cardbus
    Kernel modules: yenta_socket


```then ..

```

sudo ifconfig

eth0      Link encap:Ethernet  HWaddr 00:0a:e4:e5:cc:10  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:20 Base address:0x3000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:552 errors:0 dropped:0 overruns:0 frame:0
          TX packets:552 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:43328 (43.3 KB)  TX bytes:43328 (43.3 KB)


```I inspected > System > Administration > Additional Drivers

The result is ..

No proprietary drivers are in use in this system.

[EDIT]

When I tried LiveCD PCLinuxOS

there was no internet connection but this was detected ..

eth0: Realtek SemiConductor Ltd. RTL-8139/8139C/8139C+

Network is down in interface
Wired (Ethernet) (eth0)
okay, first you have to get wired internet working then you may be able to install the broadcom driver, for the wired internet you don't need to install any driver as realtek chips work out of the box in linux, (some of them don't but yours should) so two questions, your router is always connected to internet or does the computer manage the connection?
does the router have DCHP server enabled? if the router doesn't have DCHP server you can enable then you'll have to set a static IP for Ubuntu, so first login to the router configuration page on windows and check the DHCP server if no DCHP server then take note of the static IP.

---

### Post by gandaran on 2011-05-22
>  My ubuntu 10.10 and internet connection runs o.k. on Dell Inspiron.
sorry only read this now, if you have wired internet on the ubuntu dell laptop then all is okay with the router.
try on the acer running this command then open firefox and see if internet is working
```
sudo ifup eth0
```

---

### Post by dragonfly41 on 2011-05-22
Thanks for the diagnosis ..

(1) I have no router and I'm connected directly to a cable modem and physically switch between

    Dell Inspiron 1720 - ubuntu 10.10 .. which has Internet connection (I'm using to submit this post)
    Acer Aspire 36133WLMi - ubuntu 10.10 .. which has no Internet connection

(2) In editing Auto eth0 (in working Dell Inspiron)

    IPv4 Settings
    Method: Automatic (DHCP)

    IPv6 Settings
    Method: ignore

(3) In the working network on Dell Inspiron I can try in IPv4 settings switching from automatic (DHCP) to manual and setting my static IP address which I have tested.

I can complete the Address field but I'm not sure what to set in Netmask and Gateway fields.

---

### Post by dragonfly41 on 2011-05-22
Your last post crossed as I was posting my last post above ...

**[COLOR=DarkSlateGray]sudo ifup eth0[/COLOR]**

In Acer the response is[COLOR=Navy] .. Ignoring unknown interface eth0=eth0[/COLOR]

In Dell the response is ..[COLOR=Navy]  ifup: interface eth0 already configured[/COLOR]

---

### Post by gandaran on 2011-05-22
> I can complete the Address field but I'm not sure what to set in Netmask and Gateway fields.
netmask should be 255.255.255.0
gateway is the modem IP, the same one used to login to modem/router configuration.
check on the Ubuntu Dell panel network icon for connection information.
another question, do you still have windows on the Acer and does wired internet work on windows in the same Acer?

---

### Post by gandaran on 2011-05-22
> In Acer the response is .. Ignoring unknown interface eth0=eth0
so ethernet interface is not detected, I don't think its missing drivers (maybe I'm wrong) are you sure Ethernet card isn't broken or something?

---

### Post by dragonfly41 on 2011-05-22
> 
... does wired internet work on windows in the same Acer?

... are you sure Ethernet card isn't broken or something?


Windows XP was previously working .. sluggishly .. on this Acer and I removed it when installing ubuntu 10.10.   Internet connection was fine on Windows XP.

However I've left an NTFS partition to reinstall Win XP in dual boot .. leaving ubuntu in other partitions.  So I guess I'll have to reinstall Win XP to check that there is nothing amiss with the actual connection into the Acer.   

Connection is o.k. up to the end of the cable plugging into Acer (or Dell).   But it could be something from thereon inside the Acer.

---

### Post by gandaran on 2011-05-22
dragonfly41
for the wireless drivers you can get them [here for ubuntu 10.10 only]("http://packages.ubuntu.com/maverick/allpackages"), download the broadcom-sta-common and b43-fwcutter to a pen drive but install only one of them on the Acer, if one doesn't work try the other as I don't know exactly which one you will need.
you can check which broadcom drivers are available on the Dell typing broadcom in the Ubuntu synaptic search box.

---

### Post by dragonfly41 on 2011-05-22
I've looked through my notes and at one point when ubuntu was starting up a message flashed up in terminal before the ubuntu splash ..

b43/ncode5.fw not found
b43-open/ncode5.fw not found

go to

[http://wireless.kernel.org/en/users/Drivers/b43#devicefirmware](http://wireless.kernel.org/en/users/Drivers/b43#devicefirmware)

[https://www.isc.org/software/dhcp](https://www.isc.org/software/dhcp)

but I thought these were related to wireless and not ethernet.   
So I need wireless drivers for cable connection?


I'll try the links you've suggested.

Thanks ..

---

### Post by gandaran on 2011-05-22
> So I need wireless drivers for cable connection?
No! install them only if you want wireless working.

---

### Post by dragonfly41 on 2011-05-22
> No! install them only if you want wireless working.

So .. if I only want cable connection?

I'll have to try installing Win XP just to check if the Acer innards are working.

---

### Post by dragonfly41 on 2011-05-22
Here is the update ..

Installed Win XP Pro in separate NTFS partition .. but initially could not get Internet connection.

In case the point of entry of Ethernet cable was faulty I tried a plugin Xircom Cardbus Ethernet II 10/100

I had to switch cable modem off and wait and then on again to force reset of IP address

I found that I could then use either the Realtek NIC or the Xircom Cardbus to make Internet connection.  So I'm not sure if this was a glitch.

I have yet to test the Internet connection on ubuntu on Acer since I lost the ubuntu boot menu when I installed Win XP.

I don't know if ubuntu and Xircom cardbus are compatible.   I'll report back when I've again tried ubuntu Internet connection on Acer.

---

