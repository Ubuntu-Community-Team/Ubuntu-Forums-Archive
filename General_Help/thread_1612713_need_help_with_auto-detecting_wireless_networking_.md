---
title: "need help with auto-detecting wireless networking (currently capabillity is disabled)"
date: 2010-11-03
forum: General Help
---

### Post by SMahoney on 2010-11-03
I'm having trouble getting automatic detection of wireless networking to work.  I'm
a newbie but I got some help from a friend to check the following commands.  Also I've found many descriptions of the same problem in the archives, but none of the suggested fixes work for me.   Wireless networking used to work before the upgrade
to Meercat.   Here's what I have checked:

I checked in *System > Administration > Hardware Drivers* shows no drivers, which 
seems odd.  

lshw shows the device is recognized, but disabled:

sheri@lennie:~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       product: NetXtreme BCM5751M Gigabit Ethernet PCI Express
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 21
       serial: 00:16:d3:2b:d5:dc
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=tg3 driverversion=3.102 firmware=5751m-v3.56 ip=192.168.15.2 latency=0 multicast=yes
       resources: irq:30 memory:ee000000-ee00ffff
 *-network DISABLED
       description: Wireless interface
       product: PRO/Wireless 3945ABG [Golan] Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: wlan0
       version: 02
       serial: 00:18:de:19:fc:2a
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=iwl3945 latency=0 multicast=yes wireless=IEEE 802.11abg
       resources: irq:29 memory:edf00000-edf00fff


iwconfig shows the following info about the wireless network interface:


sheri@lennie:~$ iwconfig
...
wlan0     IEEE 802.11abg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=off   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off


I've tried right-clicking on the network icon at the top of my screen, but the
option to enable wireless is greyed out.

root@lennie:~# ip addr show
1: lo: <LOOPBACK,UP,LOWER_UP> mtu 16436 qdisc noqueue state UNKNOWN 
    link/loopback 00:00:00:00:00:00 brd 00:00:00:00:00:00
    inet 127.0.0.1/8 scope host lo
    inet6 ::1/128 scope host 
       valid_lft forever preferred_lft forever
2: eth0: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1400 qdisc mq state UP qlen 1000
    link/ether 00:16:d3:2b:d5:dc brd ff:ff:ff:ff:ff:ff
    inet 192.168.15.2/24 brd 192.168.15.255 scope global eth0
    inet6 fe80::216:d3ff:fe2b:d5dc/64 scope link 
       valid_lft forever preferred_lft forever
3: wlan0: <BROADCAST,MULTICAST> mtu 1500 qdisc noop state DOWN qlen 1000
    link/ether 00:18:de:19:fc:2a brd ff:ff:ff:ff:ff:ff

I get the following error when I try to bring it up:

root@lennie:~# ip link set wlan0 up
RTNETLINK answers: Unknown error 132


dmesg shows an error was detected:

[10095.596050] iwl3945 0000:03:00.0: MAC is in deep sleep!.  CSR_GP_CNTRL = 0x000003C8
[10095.830843] iwl3945 0000:03:00.0: Hardware error detected.  Restarting.


I also tried disable the FN+Fx key combo for the disabling wireless radio, and it
didn't help. 

Hopefully something here will offer a clear picture of what to do to get it fixed.

---

