---
title: "new to ubuntu/linux need some help...wifi"
date: 2012-03-23
forum: General Help
---

### Post by Red X on 2012-03-23
i did a search online and i instaled what i thought would fix my wifi card issues it was the new firmware for it.  anyway i can not get the computer to use wifi any help would be great =]

thanks

---

### Post by Red X on 2012-03-23
cat /etc/lsb-release; uname -a lspci -nnk | grep -iA2 net lsusb iwconfig rfkill list all lsmod




[B]then it gave me this


john@john-Latitude-D420:~$ cat /etc/lsb-release; uname -a
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=11.10
DISTRIB_CODENAME=oneiric
DISTRIB_DESCRIPTION="Ubuntu 11.10"
Linux john-Latitude-D420 3.0.0-16-generic #29-Ubuntu SMP Tue Feb 14 12:49:42 UTC 2012 i686 i686 i386 GNU/Linux
john@john-Latitude-D420:~$ lspci -nnk | grep -iA2 net
09:00.0 Ethernet controller [0200]: Broadcom Corporation NetXtreme BCM5752 Gigabit Ethernet PCI Express [14e4:1600] (rev 02)
	Subsystem: Dell Device [1028:01d6]
	Kernel driver in use: tg3
--
0c:00.0 Network controller [0280]: Broadcom Corporation BCM4311 802.11b/g WLAN [14e4:4311] (rev 01)
	Subsystem: Dell Wireless 1390 WLAN Mini-Card [1028:0007]
	Kernel modules: wl, ssb
john@john-Latitude-D420:~$ lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 413c:a005 Dell Computer Corp. Internal 2.0 Hub
Bus 002 Device 003: ID 0b97:7761 O2 Micro, Inc. Oz776 1.1 Hub
Bus 002 Device 004: ID 0b97:7762 O2 Micro, Inc. Oz776 SmartCard Reader
john@john-Latitude-D420:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

john@john-Latitude-D420:~$ rfkill list all
0: dell-wifi: Wireless LAN
	Soft blocked: yes
	Hard blocked: yes
1: dell-bluetooth: Bluetooth
	Soft blocked: yes
	Hard blocked: yes
john@john-Latitude-D420:~$ lsmo
[/B]

---

### Post by PhantomTurtle on 2012-03-23
I think you have to install the Broadcom wireless drivers using the additional drivers utility that comes with Ubuntu. So just open up Additional Drivers and it should be there. Next click install, and when its done restart. After that it should work.

---

