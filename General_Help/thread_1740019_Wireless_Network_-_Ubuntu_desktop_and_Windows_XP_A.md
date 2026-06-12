---
title: "Wireless Network - Ubuntu desktop and Windows XP Acer laptop"
date: 2011-04-26
forum: General Help
---

### Post by NeoAndersen on 2011-04-26
Hello

I have internet on my desktop and I want to share it with a laptop through wifi connection... The motherboard is an Asus p5k deluxe wifi and have an Ubuntu 10 LTS installed, the laptop is an Acer Aspire 4330 with Windows XP...

I have tryed this help: [https://help.ubuntu.com/community/WifiDocs/Adhoc#Supported%20Cards]("https://help.ubuntu.com/community/WifiDocs/Adhoc#Supported%20Cards")
But it didn't work... as follow:

gilmar@gilmar-desktop:~$ sudo /etc/dbus-1/event.d/25NetworkManager stop
[sudo] password for gilmar: 
sudo: /etc/dbus-1/event.d/25NetworkManager: command not found
gilmar@gilmar-desktop:~$ sudo /etc/dbus-1/event.d/25NetworkManager stop
sudo: /etc/dbus-1/event.d/25NetworkManager: command not found
gilmar@gilmar-desktop:~$ sudo ip link set wlan0 down
[COLOR="Red"]gilmar@gilmar-desktop:~$ lshw -C network[/COLOR]
WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       product: 88E8056 PCI-E Gigabit Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 12
       serial: 00:1b:fc:ed:bf:91
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list rom ethernet physical
       configuration: broadcast=yes driver=sky2 driverversion=1.25 firmware=N/A ip=10.0.0.1 latency=0 multicast=yes
       resources: irq:28 memory:fe9fc000-fe9fffff ioport:c800(size=256) memory:fe9c0000-fe9dffff(prefetchable)
  *-network DISABLED
       description: Ethernet interface
       product: RTL-8110SC/8169SC Gigabit Ethernet
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 4
       bus info: pci@0000:05:04.0
       logical name: eth1
       version: 10
       serial: 00:1b:fc:ed:be:21
       width: 32 bits
       clock: 66MHz
       capabilities: bus_master cap_list rom ethernet physical
       configuration: broadcast=yes driver=r8169 driverversion=2.3LK-NAPI latency=64 maxlatency=64 mingnt=32 multicast=yes
       resources: irq:16 ioport:e800(size=256) memory:febfec00-febfecff memory:80800000-8081ffff(prefetchable)
  *-network DISABLED
      [COLOR="Red"] description: Wireless interface[/COLOR]
       physical id: 1
       logical name: wlan0
       serial: 00:15:af:22:ca:35
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11bg
gilmar@gilmar-desktop:~$ sudo iwconfig wlan0 mode ad-hoc
[COLOR="Red"]Error for wireless request "Set Mode" (8B06) :
    SET failed on device wlan0 ; Operation not supported.[/COLOR]
gilmar@gilmar-desktop:~$:guitar:

---

