---
title: "Laptop Wireless not working - netgear WG111v2 usb and arthos onboard chip"
date: 2010-10-18
forum: General Help
---

### Post by mruschmann on 2010-10-18
well I noticed a post from [http://ubuntuforums.org/showthread.php?p=6183681](http://ubuntuforums.org/showthread.php?p=6183681) , so lets start there:

1)
HP G60

2)
00:00.0 RAM memory: nVidia Corporation MCP78S [GeForce 8200] Memory Controller (rev a2)
00:01.0 ISA bridge: nVidia Corporation Device 075e (rev a2)
00:01.1 SMBus: nVidia Corporation MCP78S [GeForce 8200] SMBus (rev a1)
00:01.3 Co-processor: nVidia Corporation MCP78S [GeForce 8200] Co-Processor (rev a2)
00:01.4 RAM memory: nVidia Corporation MCP78S [GeForce 8200] Memory Controller (rev a1)
00:02.0 USB Controller: nVidia Corporation MCP78S [GeForce 8200] OHCI USB 1.1 Controller (rev a1)
00:02.1 USB Controller: nVidia Corporation MCP78S [GeForce 8200] EHCI USB 2.0 Controller (rev a1)
00:04.0 USB Controller: nVidia Corporation MCP78S [GeForce 8200] OHCI USB 1.1 Controller (rev a1)
00:04.1 USB Controller: nVidia Corporation MCP78S [GeForce 8200] EHCI USB 2.0 Controller (rev a1)
00:06.0 IDE interface: nVidia Corporation MCP78S [GeForce 8200] IDE (rev a1)
00:07.0 Audio device: nVidia Corporation MCP72XE/MCP72P/MCP78U/MCP78S High Definition Audio (rev a1)
00:08.0 PCI bridge: nVidia Corporation MCP78S [GeForce 8200] PCI Bridge (rev a1)
00:09.0 IDE interface: nVidia Corporation MCP78S [GeForce 8200] SATA Controller (non-AHCI mode) (rev a2)
00:0a.0 Ethernet controller: nVidia Corporation MCP77 Ethernet (rev a2)
00:0b.0 PCI bridge: nVidia Corporation MCP78S [GeForce 8200] PCI Express Bridge (rev a1)
00:14.0 PCI bridge: nVidia Corporation MCP78S [GeForce 8200] PCI Bridge (rev a1)
00:18.0 Host bridge: Advanced Micro Devices [AMD] Family 11h Processor HyperTransport Configuration (rev 40)
00:18.1 Host bridge: Advanced Micro Devices [AMD] Family 11h Processor Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] Family 11h Processor DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] Family 11h Processor Miscellaneous Control
00:18.4 Host bridge: Advanced Micro Devices [AMD] Family 11h Processor Link Control
02:00.0 VGA compatible controller: nVidia Corporation C77 [GeForce 8200M G] (rev a2)
07:00.0 Ethernet controller: Atheros Communications Inc. AR5001 Wireless Network Adapter (rev 01)


Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 005: ID 0846:6a00 NetGear, Inc. WG111v2 54 Mbps Wireless [RealTek RTL8187L]
Bus 002 Device 003: ID 04f2:b091 Chicony Electronics Co., Ltd Webcam
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 0bda:0158 Realtek Semiconductor Corp. USB 2.0 multicard reader
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

3)
eth0      Link encap:Ethernet  HWaddr 00:1f:16:6c:05:4e  
          inet addr:192.168.1.4  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::21f:16ff:fe6c:54e/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:13268 errors:0 dropped:0 overruns:0 frame:0
          TX packets:9842 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:16435963 (16.4 MB)  TX bytes:1138270 (1.1 MB)
          Interrupt:42 Base address:0xa000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:12 errors:0 dropped:0 overruns:0 frame:0
          TX packets:12 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:720 (720.0 B)  TX bytes:720 (720.0 B)

lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=off   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          
wlan1     IEEE 802.11bg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=off   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off

4)
[   13.183356] udev[392]: renamed network interface wlan1 to wlan1-wlan0
[   14.070823] udev[390]: renamed network interface wlan0 to wlan1
[   14.353427] udev[392]: renamed network interface wlan1-wlan0 to wlan0

5)
[   13.183356] udev[392]: renamed network interface wlan1 to wlan1-wlan0
[   14.070823] udev[390]: renamed network interface wlan0 to wlan1
[   14.353427] udev[392]: renamed network interface wlan1-wlan0 to wlan0

6)
  *-network               
       description: Ethernet interface
       product: MCP77 Ethernet
       vendor: nVidia Corporation
       physical id: a
       bus info: pci@0000:00:0a.0
       logical name: eth0
       version: a2
       serial: 00:1f:16:6c:05:4e
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 66MHz
       capabilities: pm msi ht bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=forcedeth driverversion=0.64 duplex=full ip=192.168.1.4 latency=0 link=yes maxlatency=20 mingnt=1 multicast=yes port=MII speed=100MB/s
       resources: irq:42 memory:c0009000-c0009fff ioport:30f8(size=8) memory:c0007c00-c0007cff memory:c0007800-c000780f
  *-network DISABLED
       description: Wireless interface
       product: AR5001 Wireless Network Adapter
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:07:00.0
       logical name: wlan0
       version: 01
       serial: 00:24:2b:86:b1:f8
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ath5k driverversion=2.6.35-22-generic firmware=N/A latency=0 link=yes multicast=yes wireless=IEEE 802.11bg
       resources: irq:23 memory:c2000000-c200ffff
  *-network DISABLED
       description: Wireless interface
       physical id: 1
       bus info: usb@2:1
       logical name: wlan1
       serial: 00:24:b2:33:ba:8e
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=rtl8187 driverversion=2.6.35-22-generic firmware=N/A link=yes multicast=yes wireless=IEEE 802.11bg

7)
wlan0     Failed to read scan data : Network is down

wlan1     Failed to read scan data : Network is down

8)
No LSB modules are available.

9)
2.6.35-22-generic x86_64

10)
 * Reconfiguring network interfaces...                                                                                                                                  Ignoring unknown interface eth0=eth0.




-----------------------------------------------------------------

Ok I need help.  I downloaded, burned, installed ubuntu 10-10 on this laptop.  Problem city with the wireless not being able to work.  I tried the ubuntu troubleshooting for wireless, all it did was tell me to activate my wireless.  I cant get the onboard wireless chip to work in windows either.  It is a mess.  So my buddy gave me this netgear usb thing ... works, but not in any of my usb ports ....

I cant deal with this freaking wireless anymore and i pretty much have a crappy desktop now instead of a mobile laptop.  LOL.

Thz
mike

---

### Post by Hippytaff on 2010-10-18
Have you tried using the windows driver for the chipset with Ndiswrapper?

 AR5001 - [http://www.drivershq.com/Drivers/FUJITSU/A-SERIES-NOTEBOOK/A3040/22272/22273/22275/4621/ModelDrivers.aspx](http://www.drivershq.com/Drivers/FUJITSU/A-SERIES-NOTEBOOK/A3040/22272/22273/22275/4621/ModelDrivers.aspx)

[https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper)

or just updating is worth a punt!? 

```

sudo apt-get update && sudo apt-get upgrade

```

---

### Post by ubunterooster on 2010-10-18
I will organize things, deleting unneeded info> **mruschmann said:**
> well I noticed a post from [http://ubuntuforums.org/showthread.php?p=6183681](http://ubuntuforums.org/showthread.php?p=6183681) , so lets start there:

1)
HP G60

2)```
lspci 

07:00.0 Ethernet controller: Atheros Communications Inc. AR5001 Wireless Network Adapter (rev 01)
``````

lsusb

Bus 002 Device 005: ID 0846:6a00 NetGear, Inc. WG111v2 54 Mbps Wireless [RealTek RTL8187L]
```3)```
ifconfig 

lo        no wireless extensions.

eth0      no wireless extensions.
``````
iwconfig

wlan0     IEEE 802.11bg  ESSID:eek:ff/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=off   
          Retry  long limit:7   RTS thr:eek:ff   Fragment thr:eek:ff
          Power Management:eek:ff
          
wlan1     IEEE 802.11bg  ESSID:eek:ff/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=off   
          Retry  long limit:7   RTS thr:eek:ff   Fragment thr:eek:ff
          Power Management:eek:ff
```4)
```
lsmod


[   13.183356] udev[392]: renamed network interface wlan1 to wlan1-wlan0
[   14.070823] udev[390]: renamed network interface wlan0 to wlan1
[   14.353427] udev[392]: renamed network interface wlan1-wlan0 to wlan0

```5)```
dmesg

[   13.183356] udev[392]: renamed network interface wlan1 to wlan1-wlan0
[   14.070823] udev[390]: renamed network interface wlan0 to wlan1
[   14.353427] udev[392]: renamed network interface wlan1-wlan0 to wlan0

```6)```
sudo lshw -C network

  *-network DISABLED
       description: Wireless interface
       product: AR5001 Wireless Network Adapter
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:07:00.0
       logical name: wlan0
       version: 01
       serial: 00:24:2b:86:b1:f8
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ath5k driverversion=2.6.35-22-generic firmware=N/A latency=0 link=yes multicast=yes wireless=IEEE 802.11bg
       resources: irq:23 memory:c2000000-c200ffff
  *-network DISABLED
       description: Wireless interface
       physical id: 1
       bus info: usb@2:1
       logical name: wlan1
       serial: 00:24:b2:33:ba:8e
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=rtl8187 driverversion=2.6.35-22-generic firmware=N/A link=yes multicast=yes wireless=IEEE 802.11bg
```7)```
iwlist

scan wlan0     Failed to read scan data : Network is down

wlan1     Failed to read scan data : Network is down
```8)```
$ lsb_release -d
[COLOR=Red]
No LSB modules are available.[/COLOR]
```9)```
$ uname -mr 2.6.35-22-generic x86_64

```10)```
sudo /etc/init.d/networking restart 

* Reconfiguring network interfaces...     Ignoring unknown interface eth0=eth0.

```-----------------------------------------------------------------

Ok I need help.  I downloaded, burned, installed ubuntu 10-10 on this laptop.  Problem city with the wireless not being able to work.  I tried the ubuntu troubleshooting for wireless, all it did was tell me to activate my wireless.  I cant get the onboard wireless chip to work in windows either.  It is a mess.  So my buddy gave me this netgear usb thing ... works, but not in any of my usb ports ....

I cant deal with this freaking wireless anymore and i pretty much have a crappy desktop now instead of a mobile laptop.  LOL.

Thz
mike

---

### Post by Hippytaff on 2010-10-18
oops think i suggested the pci driver...your looking for the usb one - 
RTL8187L -http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PFid=1&Level=6&Conn=5&ProdID=36&DownTypeID=3&GetDown=false&Downloads=true#362

theres a linux one

---

### Post by ubunterooster on 2010-10-18
Link did not work... correcting it...done! :D > **Hippytaff said:**
> oops think i suggested the pci driver...your looking for the usb one - 
RTL8187L [http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PFid=1&Level=6&Conn=5&ProdID=36&DownTypeID=3&GetDown=false&Downloads=true#362](http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PFid=1&Level=6&Conn=5&ProdID=36&DownTypeID=3&GetDown=false&Downloads=true#362)

theres a linux one

Okay I think I am just correcting errors of others; not the computer problem...sorry about policing

---

### Post by Hippytaff on 2010-10-18
> **ubunterooster said:**
> Link did not work... correcting it...done! :D 

Okay I think I am just correcting errors of others; not the computer problem...sorry about policing

keep policing...thank you! I started barking up the wrong tree then posted a duff link...long day :-) cheers!

---

### Post by mruschmann on 2010-10-18
I have no idea what is wrong ... Ubuntu is supposed to support the Netgear usb WG111v2 ... When plugged in i get a 'device not ready' message from the network manager at the top right.   The usb and on-board used to work b4 i formatted and updated.  I made a far fetched conclusion that for some reason my on-board wireless chip burned up, so my bud gave me his old usb wireless that works in his ubuntu 9.10.  I starting to sway to wrapping but it seem inferior.

---

### Post by Hippytaff on 2010-10-18
> **mruschmann said:**
> I have no idea what is wrong ... Ubuntu is supposed to support the Netgear usb WG111v2 ... When plugged in i get a 'device not ready' message from the network manager at the top right.   The usb and on-board used to work b4 i formatted and updated.  I made a far fetched conclusion that for some reason my on-board wireless chip burned up, so my bud gave me his old usb wireless that works in his ubuntu 9.10.  I starting to sway to wrapping but it seem inferior.

Its a bit messy but if it work :-) by the way the link I posted (incorrectly and kindly corrected by someone with the ability to see - unlike me this evening) is for the linux/ubuntu driver

---

### Post by mruschmann on 2010-10-18
Is this normal?  I think I got a little steam. ->

sudo ifconfig wlan0 up
SIOCSIFFLAGS: Operation not possible due to RF-kill

rfkill list
0: hp-wifi: Wireless LAN
    Soft blocked: yes
    Hard blocked: no
2: phy0: Wireless LAN
    Soft blocked: yes
    Hard blocked: no
6: phy5: Wireless LAN
    Soft blocked: yes
    Hard blocked: no

---

### Post by Hippytaff on 2010-10-18
[http://ubuntuforums.org/showthread.php?t=1600156](http://ubuntuforums.org/showthread.php?t=1600156) - try unblocking

> 0: hp-wifi: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no


Mine look like this

```

rfkill unblock


```

---

### Post by mruschmann on 2010-10-18
I cant believe it, fixed .... Thz for all the help!!!  Example:

rfkill block <index>|<type> or rfkill unblock <index>|<type> ... depending on your need

From my command:

- rfkill list
- all categories have to be no for unblocked usage
- the <index> is the first number (0,1,2 in my example)
- rfkill unblock 0 
- and so on


THZ so much..... There was no indication of this in any troubleshooting form from Ubuntu.  It was important for me.  BTW somewhere along my week path I Installed the following packages:
linux-backports-modules-wireless-2.6.35-22-generic (2.6.35-22.12)

---

### Post by Hippytaff on 2010-10-18
> **mruschmann said:**
> I cant believe it, fixed .... Thz for all the help!!!  Example:

rfkill block <index>|<type> or rfkill unblock <index>|<type> ... depending on your need

From my command:

- rfkill list
- all categories have to be no for unblocked usage
- the <index> is the first number (0,1,2 in my example)
- rfkill unblock 0 
- and so on


THZ so much..... There was no indication of this in any troubleshooting form from Ubuntu.  It was important for me.  BTW somewhere along my week path I Installed the following packages:
linux-backports-modules-wireless-2.6.35-22-generic (2.6.35-22.12)

Excellent :-D - remember to mark the thread as solved in the forum tools so others can benefit from your hard work and perseverance :-)

---

### Post by johnnytm on 2010-10-18
Easier to just use ```
 sudo rfkill unblock all
``` no need to remember numbers that way :)

---

