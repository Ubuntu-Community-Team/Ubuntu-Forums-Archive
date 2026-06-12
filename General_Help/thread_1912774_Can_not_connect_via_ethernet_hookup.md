---
title: "Can not connect via ethernet hookup"
date: 2012-01-21
forum: General Help
---

### Post by JohnFDay on 2012-01-21
I'm running Ubuntu 10.10 and yesterday my desktop computer developed a strange problem which I have been completely unable to correct.

I can no longer connect, via direct ethernet cable, to the web.  I'm running a dual-boot system, with Windows 7 on the other side.  THAT side connects with no problem whatever, but nothing I've tried has been able to get the Ubuntu to link up.  (It was working earlier, by the way, and I've made no known changes to the system.)

Any idea(s) why this is happening...and what can I do to correct it?

Thanks in advance.

John Day

---

### Post by imachavel on 2012-01-21
look at this for basics:

[http://www.cyberciti.biz/tips/ubuntu-linux-view-the-status-of-my-network-interfacescard.html](http://www.cyberciti.biz/tips/ubuntu-linux-view-the-status-of-my-network-interfacescard.html)

but let's get to what it probably is

first enter this:

"sudo lshw -C" network in the terminal without the quotes. ctrl + alt + t ought to get you there

here is my readout:

  *-network               
       description: Ethernet interface
       product: 82562ET/EZ/GT/GZ - PRO/100 VE (LOM) Ethernet Controller
       vendor: Intel Corporation
       physical id: 8
       bus info: pci@0000:03:08.0
       logical name: eth0
       version: 03
       serial: 00:13:20:37:87:1b
       size: 100Mbit/s
       capacity: 100Mbit/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e100 driverversion=3.5.24-k2-NAPI duplex=full firmware=N/A ip=192.168.0.100 latency=64 link=yes maxlatency=56 mingnt=8 multicast=yes port=MII speed=100Mbit/s
       resources: irq:20 memory:dfbff000-dfbfffff ioport:c8c0(size=64)

read this if you want:

[https://help.ubuntu.com/10.04/internet/C/troubleshooting-wireless.html](https://help.ubuntu.com/10.04/internet/C/troubleshooting-wireless.html)

but you said hard wired:

;)

so let's look at your hard wired NIC driver:

open the terminal and enter this:

ifconfig

then look for eth configuration

this is mine:

etho

(hope no one hacks me)

now enter this for whatever version of etho you have:

ethtool -i eth0

mine says:

driver: e100
version: 3.5.24-k2-NAPI
firmware-version: N/A
bus-info: 0000:03:08.0
supports-statistics: yes
supports-test: yes
supports-eeprom-access: yes
supports-register-dump: yes

you need to make sure that driver is installed. Any luck?

---

### Post by imachavel on 2012-01-21
if windows connects you know your hardware is good on the modem side, and the computer NIC or network interface adapter side, it's gotta be internal

---

### Post by JohnFDay on 2012-01-21
> **imachavel said:**
> look at this for basics:

[http://www.cyberciti.biz/tips/ubuntu-linux-view-the-status-of-my-network-interfacescard.html](http://www.cyberciti.biz/tips/ubuntu-linux-view-the-status-of-my-network-interfacescard.html)

but let's get to what it probably is

first enter this:

"sudo lshw -C" network in the terminal without the quotes. ctrl + alt + t ought to get you there

here is my readout:

  *-network               
       description: Ethernet interface
       product: 82562ET/EZ/GT/GZ - PRO/100 VE (LOM) Ethernet Controller
       vendor: Intel Corporation
       physical id: 8
       bus info: pci@0000:03:08.0
       logical name: eth0
       version: 03
       serial: 00:13:20:37:87:1b
       size: 100Mbit/s
       capacity: 100Mbit/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e100 driverversion=3.5.24-k2-NAPI duplex=full firmware=N/A ip=192.168.0.100 latency=64 link=yes maxlatency=56 mingnt=8 multicast=yes port=MII speed=100Mbit/s
       resources: irq:20 memory:dfbff000-dfbfffff ioport:c8c0(size=64)

read this if you want:

[https://help.ubuntu.com/10.04/internet/C/troubleshooting-wireless.html](https://help.ubuntu.com/10.04/internet/C/troubleshooting-wireless.html)

but you said hard wired:

;)

so let's look at your hard wired NIC driver:

open the terminal and enter this:

ifconfig

then look for eth configuration

this is mine:

etho

(hope no one hacks me)

now enter this for whatever version of etho you have:

ethtool -i eth0

mine says:

driver: e100
version: 3.5.24-k2-NAPI
firmware-version: N/A
bus-info: 0000:03:08.0
supports-statistics: yes
supports-test: yes
supports-eeprom-access: yes
supports-register-dump: yes

you need to make sure that driver is installed. Any luck?

===============================================================

Okay, I ran the ifconfig and ethtool.  The ethtool said it needed to be installed.  SO....I installed it and BINGO!  The link was established.

I'm back online in Ubuntu.  Still don't know why it happened, but that doesn't matter anymore.

Thanks much, my friend!  As Sergeant Preston Of The Yukon always used to say, "Well, King, looks like this case is closed!"  (or something like that!)

John Day

---

