---
title: "ubuntu 10.10 wireless problems"
date: 2010-12-28
forum: General Help
---

### Post by solEIN on 2010-12-28
Hi there! I am new to linux world, recently installed ubuntu desktop 10.10 on old laptop (fujitsu-siemens amilo).

When installed, i noticed that the 1.enable wireless is grayed out
                                                2. wireless is disabled

recently acquired a d-link dwl-g122 ver. C1  USB wireless, didnt want to fidle with original.

I am totally new to linux, this is my first installation.

I plead for your help, have researched a lot but the problem stays, i need just some good direction and tutorial.

Tried the gksudo gedit /etc/network/interfaces added these lines: auto wlan1
                                                                                              iface wlan1... IT CHANGES to device not managed, tried  /etc/NetworkManager/nm-system-settings.conf:
 	 	[main]
plugins=ifupdown,keyfile

[ifupdown]
managed=false 
changing it to true the d link is again disabled?


3. when d link is plugged, ubuntu boots but stucks after login screen?

On Vista, home network i use wpa2 psk protection, essid not broadcasting, hidden.

Please help me i would like to learn more!

---

### Post by cariboo on 2010-12-28
Could paste the output of the following commands in your next post. Unplug the device and boot to the desktop, then plug the device in, open a terminal and type:

```
dmesg | tail -n10
```

then in the same terminal type:

```
sudo lshw -C network
```

the output of the above to commands should help in getting your wireless device to work.

---

### Post by solEIN on 2010-12-29
Thanks for the reply:DTried what you suggested and this is what i get:

andrea@macic:~$ dmesg | tail -n10
[   22.490640] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro,commit=0
[   24.437994] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro,commit=0
[   31.575080] padlock: VIA PadLock not detected.
[   85.704062] usb 1-4: new high speed USB device using ehci_hcd and address 3
[   86.271510] phy1: Selected rate control algorithm 'minstrel'
[   86.273262] Registered led device: rt73usb-phy1::radio
[   86.273322] Registered led device: rt73usb-phy1::assoc
[   86.273380] Registered led device: rt73usb-phy1::quality
[   86.275264] usbcore: registered new interface driver rt73usb
[   86.608659] ADDRCONF(NETDEV_UP): wlan1: link is not ready
andrea@macic:~$ sudo lshw -C network
[sudo] password for andrea: 
Sorry, try again.
[sudo] password for andrea: 
  *-network:0 DISABLED    
       description: Wireless interface
       product: RT2500 802.11g
       vendor: RaLink
       physical id: 1
       bus info: pci@0000:02:01.0
       logical name: wlan0
       version: 01
       serial: 00:14:a5:0c:48:15
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=rt2500pci driverversion=2.6.35-22-generic firmware=N/A latency=64 link=no multicast=yes wireless=IEEE 802.11bg
       resources: irq:23 memory:d0204000-d0205fff
  *-network:1
       description: Ethernet interface
       product: BCM4401-B0 100Base-TX
       vendor: Broadcom Corporation
       physical id: d
       bus info: pci@0000:02:0d.0
       logical name: eth0
       version: 02
       serial: 00:40:ca:d6:07:fa
       size: 10MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list rom ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=b44 driverversion=2.0 duplex=half latency=64 link=no multicast=yes port=twisted pair speed=10MB/s
       resources: irq:20 memory:d0208000-d0209fff memory:20000000-2001ffff
  *-network
       description: Wireless interface
       physical id: 1
       bus info: usb@1:4
       logical name: wlan1
       serial: 00:19:5b:6f:25:75
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=rt73usb driverversion=2.6.35-22-generic firmware=N/A link=no multicast=yes wireless=IEEE 802.11bg
andrea@macic:~$ ^C
andrea@macic:~$ 


After restart ubuntu stucks after login screen(d link plugged in)

---

### Post by solEIN on 2010-12-29
Thanks for the reply:DTried what you suggested and this is what i get:

andrea@macic:~$ dmesg | tail -n10
[   22.490640] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro,commit=0
[   24.437994] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro,commit=0
[   31.575080] padlock: VIA PadLock not detected.
[   85.704062] usb 1-4: new high speed USB device using ehci_hcd and address 3
[   86.271510] phy1: Selected rate control algorithm 'minstrel'
[   86.273262] Registered led device: rt73usb-phy1::radio
[   86.273322] Registered led device: rt73usb-phy1::assoc
[   86.273380] Registered led device: rt73usb-phy1::quality
[   86.275264] usbcore: registered new interface driver rt73usb
[   86.608659] ADDRCONF(NETDEV_UP): wlan1: link is not ready
andrea@macic:~$ sudo lshw -C network
[sudo] password for andrea: 
Sorry, try again.
[sudo] password for andrea: 
  *-network:0 DISABLED    
       description: Wireless interface
       product: RT2500 802.11g
       vendor: RaLink
       physical id: 1
       bus info: pci@0000:02:01.0
       logical name: wlan0
       version: 01
       serial: 00:14:a5:0c:48:15
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=rt2500pci driverversion=2.6.35-22-generic firmware=N/A latency=64 link=no multicast=yes wireless=IEEE 802.11bg
       resources: irq:23 memory:d0204000-d0205fff
  *-network:1
       description: Ethernet interface
       product: BCM4401-B0 100Base-TX
       vendor: Broadcom Corporation
       physical id: d
       bus info: pci@0000:02:0d.0
       logical name: eth0
       version: 02
       serial: 00:40:ca:d6:07:fa
       size: 10MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list rom ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=b44 driverversion=2.0 duplex=half latency=64 link=no multicast=yes port=twisted pair speed=10MB/s
       resources: irq:20 memory:d0208000-d0209fff memory:20000000-2001ffff
  *-network
       description: Wireless interface
       physical id: 1
       bus info: usb@1:4
       logical name: wlan1
       serial: 00:19:5b:6f:25:75
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=rt73usb driverversion=2.6.35-22-generic firmware=N/A link=no multicast=yes wireless=IEEE 802.11bg
andrea@macic:~$ ^C
andrea@macic:~$ 


After restart ubuntu stucks after login screen(d link plugged in)

---

### Post by solEIN on 2010-12-29
Thanks for the reply:DTried what you suggested and this is what i get:

andrea@macic:~$ dmesg | tail -n10
[   22.490640] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro,commit=0
[   24.437994] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro,commit=0
[   31.575080] padlock: VIA PadLock not detected.
[   85.704062] usb 1-4: new high speed USB device using ehci_hcd and address 3
[   86.271510] phy1: Selected rate control algorithm 'minstrel'
[   86.273262] Registered led device: rt73usb-phy1::radio
[   86.273322] Registered led device: rt73usb-phy1::assoc
[   86.273380] Registered led device: rt73usb-phy1::quality
[   86.275264] usbcore: registered new interface driver rt73usb
[   86.608659] ADDRCONF(NETDEV_UP): wlan1: link is not ready
andrea@macic:~$ sudo lshw -C network
[sudo] password for andrea: 
Sorry, try again.
[sudo] password for andrea: 
  *-network:0 DISABLED    
       description: Wireless interface
       product: RT2500 802.11g
       vendor: RaLink
       physical id: 1
       bus info: pci@0000:02:01.0
       logical name: wlan0
       version: 01
       serial: 00:14:a5:0c:48:15
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=rt2500pci driverversion=2.6.35-22-generic firmware=N/A latency=64 link=no multicast=yes wireless=IEEE 802.11bg
       resources: irq:23 memory:d0204000-d0205fff
  *-network:1
       description: Ethernet interface
       product: BCM4401-B0 100Base-TX
       vendor: Broadcom Corporation
       physical id: d
       bus info: pci@0000:02:0d.0
       logical name: eth0
       version: 02
       serial: 00:40:ca:d6:07:fa
       size: 10MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list rom ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=b44 driverversion=2.0 duplex=half latency=64 link=no multicast=yes port=twisted pair speed=10MB/s
       resources: irq:20 memory:d0208000-d0209fff memory:20000000-2001ffff
  *-network
       description: Wireless interface
       physical id: 1
       bus info: usb@1:4
       logical name: wlan1
       serial: 00:19:5b:6f:25:75
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=rt73usb driverversion=2.6.35-22-generic firmware=N/A link=no multicast=yes wireless=IEEE 802.11bg
andrea@macic:~$ ^C
andrea@macic:~$ 


After restart ubuntu stucks after login screen(d link plugged in)

---

### Post by nothappynow on 2011-01-25
New to ubuntu, installed ubuntu 10.10, have a Ralink RT 3090, wireless will not work.
Is there a simple fix?

---

### Post by Spyderkid on 2011-01-25
post the output of 
```

lsusb

```
thanks

---

### Post by Spyderkid on 2011-01-25
found something give it a go

1. Make sure the wireless adapter are connected to your computer

2. Open your terminal.
Enter this sudo :&#8221; sudo gedit /etc/network/interfaces &#8221;

3. A text window are appear. Clear all the text on that window. Then, copy and paste the following text at that window:
&#8221;
# This file describes the network interfaces available on your system 
# and how to activate them.

# The loopback network interface auto lo iface lo inet loopback

# This is a list of hotpluggable network interfaces. 

# They will be activated automatically by the hotplug subsystem.

# iface eth0 inet dhcp

auto rausb0

iface rausb0 inet dhcp pre-up ifconfig rausb0 up 
pre-up ifconfig rausb0 down 
pre-up iwconfig rausb0 essid {your ESSID} 
pre-up iwconfig rausb0 key {your WEP key} 
pre-up dhclient rausb0
&#8220;
4. Save it.

5. At terminal, enter sudo reboot

---

### Post by Spyderkid on 2011-02-06
Did my suggestion work?

---

