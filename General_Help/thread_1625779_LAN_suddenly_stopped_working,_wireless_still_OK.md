---
title: "LAN suddenly stopped working, wireless still OK"
date: 2010-11-19
forum: General Help
---

### Post by ean5533 on 2010-11-19
A couple days ago I booted up my Ubuntu 10.10 machine as usual, but the wired LAN connection did not work; it doesn't seem to see any wired connection devices. I can still connect to a wireless network with no problem, and if I plug that same ethernet cable into another machine it works fine. I've been happily using this setup for weeks; the LAN only stopped working a day or two ago. 

So I figure there's two possibilities:

[LIST=1]
[*]A recent update caused NetworkManager to stop working with wired LAN connections, but I'm the only person in the world affected (unlikely)
[*]My motherboard's ethernet port died (this motherboard is only a couple weeks old, so this also seems unlikely)
[/LIST]

I'm not good at diagnosing problems with networking, so who can tell me where to start?

---

### Post by Zookalicious on 2010-11-19
Here's a couple steps for you:

1) try using different cables or test if the ethernet cable you are using still works on another machine. This can be used to determine if you have a faulty wired connection due to cables or the router. 

2) try booting from a live CD. If that LiveCD can use your ethernet connection, then it is a software problem. If it cannot, and you know for a fact that it worked before, then it is most likely a hardware problem and your motherboard might need replacing.

I have actually had two ethernet ports fail on me. I was quite irked when it was the same flaw in the same board within a couple months of one another....

---

### Post by dcstar on 2010-11-19
> **ean5533 said:**
> 
..........
I'm not good at diagnosing problems with networking, so who can tell me where to start?

Install the **ethtool** package, it will show you what the card is doing.

Also look at the syslog file for the boot messages detecting your Ethernet hardware.

---

### Post by ean5533 on 2010-11-20
> **Zookalicious said:**
> 2) try booting from a live CD. If that LiveCD can use your ethernet connection, then it is a software problem. If it cannot, and you know for a fact that it worked before, then it is most likely a hardware problem and your motherboard might need replacing.

I feel silly for not thinking of that test on my own, especially since I still have a copy of 10.04 installed. I booted that up and the ethernet still didn't work, so it looks like we have hardware failure. Damn you, MSI.

> **dcstar said:**
> Also look at the syslog file for the boot messages detecting your Ethernet hardware.

I'm assuming this is what you'd normally see in **/var/log/syslog** for a dead ethernet port?

```
Nov 20 10:21:45 ean5533-EP43-UD3L NetworkManager[1052]: <info> (eth1): carrier is OFF
Nov 20 10:21:45 ean5533-EP43-UD3L NetworkManager[1052]: <info> (eth1): new Ethernet device (driver: 'r8169' ifindex: 2)
Nov 20 10:21:45 ean5533-EP43-UD3L NetworkManager[1052]: <info> (eth1): exported as /org/freedesktop/NetworkManager/Devices/0
Nov 20 10:21:45 ean5533-EP43-UD3L NetworkManager[1052]: <info> (eth1): now managed
Nov 20 10:21:45 ean5533-EP43-UD3L NetworkManager[1052]: <info> (eth1): device state change: 1 -> 2 (reason 2)
Nov 20 10:21:45 ean5533-EP43-UD3L NetworkManager[1052]: <info> (eth1): bringing up device.
Nov 20 10:21:45 ean5533-EP43-UD3L kernel: [   10.691360] r8169 0000:02:00.0: eth1: link down
Nov 20 10:21:45 ean5533-EP43-UD3L kernel: [   10.691770] ADDRCONF(NETDEV_UP): eth1: link is not ready
Nov 20 10:21:46 ean5533-EP43-UD3L NetworkManager[1052]: <info> (eth1): preparing device.
Nov 20 10:21:46 ean5533-EP43-UD3L NetworkManager[1052]: <info> (eth1): deactivating device (reason: 2).
Nov 20 10:21:46 ean5533-EP43-UD3L NetworkManager[1052]: <info> Added default wired connection 'Auto eth1' for /sys/devices/pci0000:00/0000:00:05.0/0000:02:00.0/net/eth1
```

---

### Post by dcstar on 2010-11-20
> **ean5533 said:**
> 
.........
I'm assuming this is what you'd normally see in **/var/log/syslog** for a dead ethernet port?

```
Nov 20 10:21:45 ean5533-EP43-UD3L NetworkManager[1052]: <info> (eth1): carrier is OFF
Nov 20 10:21:45 ean5533-EP43-UD3L NetworkManager[1052]: <info> (eth1): new Ethernet device (driver: 'r8169' ifindex: 2)
Nov 20 10:21:45 ean5533-EP43-UD3L NetworkManager[1052]: <info> (eth1): exported as /org/freedesktop/NetworkManager/Devices/0
Nov 20 10:21:45 ean5533-EP43-UD3L NetworkManager[1052]: <info> (eth1): now managed
Nov 20 10:21:45 ean5533-EP43-UD3L NetworkManager[1052]: <info> (eth1): device state change: 1 -> 2 (reason 2)
Nov 20 10:21:45 ean5533-EP43-UD3L NetworkManager[1052]: <info> (eth1): bringing up device.
Nov 20 10:21:45 ean5533-EP43-UD3L kernel: [   10.691360] r8169 0000:02:00.0: eth1: link down
Nov 20 10:21:45 ean5533-EP43-UD3L kernel: [   10.691770] ADDRCONF(NETDEV_UP): eth1: link is not ready
Nov 20 10:21:46 ean5533-EP43-UD3L NetworkManager[1052]: <info> (eth1): preparing device.
Nov 20 10:21:46 ean5533-EP43-UD3L NetworkManager[1052]: <info> (eth1): deactivating device (reason: 2).
Nov 20 10:21:46 ean5533-EP43-UD3L NetworkManager[1052]: <info> Added default wired connection 'Auto **eth1**' for /sys/devices/pci0000:00/0000:00:05.0/0000:02:00.0/net/eth1
```

Go into Network Manager and look if there is a working entry for **eth1** - not just eth0.

Those kernel entries do look suspicious.

---

### Post by Zookalicious on 2010-11-20
> **ean5533 said:**
> I feel silly for not thinking of that test on my own, especially since I still have a copy of 10.04 installed. I booted that up and the ethernet still didn't work, so it looks like we have hardware failure. Damn you, MSI.

Well if dcstars' tests support the hardware failure theory at least you should still be under warranty :/ also don't feel silly, this is what forums are for! :)

---

### Post by ean5533 on 2010-11-21
> **dcstar said:**
> Go into Network Manager and look if there is a working entry for **eth1** - not just eth0.

Those kernel entries do look suspicious.

There are no entries for eth0 or eth1, though I remember when it was working it was eth0.

On a related note, it looks like I missed a few relevant entries that happened before the stuff I pasted in last time:  

(Stuff in bold is stuff that directly mentions ethernet-related things; stuff in italics is the same snippet that I put in last time)

```
...
Nov 21 10:13:47 ean5533-EP43-UD3L kernel: [    1.234011] udev[132]: starting version 163
**Nov 21 10:13:47 ean5533-EP43-UD3L kernel: [    1.265497] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded**
Nov 21 10:13:47 ean5533-EP43-UD3L kernel: [    1.265516] r8169 0000:02:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
Nov 21 10:13:47 ean5533-EP43-UD3L kernel: [    1.265561] r8169 0000:02:00.0: setting latency timer to 64
Nov 21 10:13:47 ean5533-EP43-UD3L kernel: [    1.265591]   alloc irq_desc for 42 on node 0
Nov 21 10:13:47 ean5533-EP43-UD3L kernel: [    1.265592]   alloc kstat_irqs on node 0
Nov 21 10:13:47 ean5533-EP43-UD3L kernel: [    1.265603] r8169 0000:02:00.0: irq 42 for MSI/MSI-X
**Nov 21 10:13:47 ean5533-EP43-UD3L kernel: [    1.265935] r8169 0000:02:00.0: eth0: RTL8168d/8111d at 0xffffc900110c8000, 6c:62:6d:85:87:1a, XID 081000c0 IRQ 42**
Nov 21 10:13:47 ean5533-EP43-UD3L kernel: [    1.316715] ahci 0000:00:11.0: version 3.0
...
**Nov 21 10:13:47 ean5533-EP43-UD3L kernel: [    9.331996] udev[434]: renamed network interface eth0 to eth1**
...
Nov 21 10:13:47 ean5533-EP43-UD3L NetworkManager[1092]: <info> NetworkManager (version 0.8.1) is starting...
Nov 21 10:13:47 ean5533-EP43-UD3L NetworkManager[1092]: <info> Read config file /etc/NetworkManager/nm-system-settings.conf
Nov 21 10:13:47 ean5533-EP43-UD3L avahi-daemon[1094]: Found user 'avahi' (UID 104) and group 'avahi' (GID 109).
Nov 21 10:13:47 ean5533-EP43-UD3L avahi-daemon[1094]: Successfully dropped root privileges.
Nov 21 10:13:47 ean5533-EP43-UD3L avahi-daemon[1094]: avahi-daemon 0.6.27 starting up.
Nov 21 10:13:47 ean5533-EP43-UD3L NetworkManager[1092]: <info> trying to start the modem manager...
Nov 21 10:13:47 ean5533-EP43-UD3L avahi-daemon[1094]: Successfully called chroot().
Nov 21 10:13:47 ean5533-EP43-UD3L avahi-daemon[1094]: Successfully dropped remaining capabilities.
Nov 21 10:13:47 ean5533-EP43-UD3L modem-manager: ModemManager (version 0.4) starting...
Nov 21 10:13:47 ean5533-EP43-UD3L NetworkManager[1092]: <info> monitoring kernel firmware directory '/lib/firmware'.
Nov 21 10:13:47 ean5533-EP43-UD3L NetworkManager[1092]:    SCPlugin-Ifupdown: init!
Nov 21 10:13:47 ean5533-EP43-UD3L NetworkManager[1092]:    SCPlugin-Ifupdown: update_system_hostname
Nov 21 10:13:47 ean5533-EP43-UD3L NetworkManager[1092]:    SCPluginIfupdown: management mode: unmanaged
**Nov 21 10:13:47 ean5533-EP43-UD3L NetworkManager[1092]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/pci0000:00/0000:00:05.0/0000:02:00.0/net/eth1, iface: eth1)**
Nov 21 10:13:47 ean5533-EP43-UD3L modem-manager: Loaded plugin MotoC
Nov 21 10:13:47 ean5533-EP43-UD3L modem-manager: Loaded plugin ZTE
Nov 21 10:13:47 ean5533-EP43-UD3L modem-manager: Loaded plugin Generic
Nov 21 10:13:47 ean5533-EP43-UD3L modem-manager: Loaded plugin Option High-Speed
Nov 21 10:13:47 ean5533-EP43-UD3L modem-manager: Loaded plugin Option
**Nov 21 10:13:47 ean5533-EP43-UD3L NetworkManager[1092]:    SCPlugin-Ifupdown: device added (path: /sys/devices/pci0000:00/0000:00:05.0/0000:02:00.0/net/eth1, iface: eth1): no ifupdown configuration found.**
Nov 21 10:13:47 ean5533-EP43-UD3L NetworkManager[1092]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/pci0000:00/0000:00:13.2/usb2/2-2/2-2:1.0/net/wlan0, iface: wlan0)
Nov 21 10:13:47 ean5533-EP43-UD3L modem-manager: Loaded plugin Longcheer
Nov 21 10:13:47 ean5533-EP43-UD3L NetworkManager[1092]:    SCPlugin-Ifupdown: device added (path: /sys/devices/pci0000:00/0000:00:13.2/usb2/2-2/2-2:1.0/net/wlan0, iface: wlan0): no ifupdown configuration found.
Nov 21 10:13:47 ean5533-EP43-UD3L NetworkManager[1092]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/virtual/net/lo, iface: lo)
Nov 21 10:13:47 ean5533-EP43-UD3L NetworkManager[1092]:    SCPlugin-Ifupdown: device added (path: /sys/devices/virtual/net/lo, iface: lo): no ifupdown configuration found.
Nov 21 10:13:47 ean5533-EP43-UD3L NetworkManager[1092]:    SCPlugin-Ifupdown: end _init.
Nov 21 10:13:47 ean5533-EP43-UD3L modem-manager: Loaded plugin Sierra
Nov 21 10:13:47 ean5533-EP43-UD3L NetworkManager[1092]: <info> Loaded plugin ifupdown: (C) 2008 Canonical Ltd.  To report bugs please use the NetworkManager mailing list.
Nov 21 10:13:47 ean5533-EP43-UD3L modem-manager: Loaded plugin Huawei
Nov 21 10:13:47 ean5533-EP43-UD3L modem-manager: Loaded plugin SimTech
Nov 21 10:13:47 ean5533-EP43-UD3L modem-manager: Loaded plugin Novatel
Nov 21 10:13:47 ean5533-EP43-UD3L modem-manager: Loaded plugin Ericsson MBM
Nov 21 10:13:47 ean5533-EP43-UD3L NetworkManager[1092]: <info> Loaded plugin keyfile: (c) 2007 - 2008 Red Hat, Inc.  To report bugs please use the NetworkManager mailing list.
Nov 21 10:13:47 ean5533-EP43-UD3L modem-manager: Loaded plugin Nokia
Nov 21 10:13:47 ean5533-EP43-UD3L NetworkManager[1092]:    Ifupdown: get unmanaged devices count: 0
Nov 21 10:13:47 ean5533-EP43-UD3L NetworkManager[1092]:    SCPlugin-Ifupdown: (14995920) ... get_connections.
Nov 21 10:13:47 ean5533-EP43-UD3L NetworkManager[1092]:    SCPlugin-Ifupdown: (14995920) ... get_connections (managed=false): return empty list.
Nov 21 10:13:47 ean5533-EP43-UD3L modem-manager: Loaded plugin AnyData
Nov 21 10:13:47 ean5533-EP43-UD3L modem-manager: Loaded plugin Gobi
Nov 21 10:13:47 ean5533-EP43-UD3L modem-manager: (tty/ttyS1): port's parent platform driver is not whitelisted
Nov 21 10:13:47 ean5533-EP43-UD3L modem-manager: (tty/ttyS2): port's parent platform driver is not whitelisted
Nov 21 10:13:47 ean5533-EP43-UD3L modem-manager: (tty/ttyS3): port's parent platform driver is not whitelisted
Nov 21 10:13:47 ean5533-EP43-UD3L modem-manager: (tty/ttyS0): could not get port's parent device
Nov 21 10:13:47 ean5533-EP43-UD3L kernel: [   11.030498] type=1400 audit(1290352427.303:5): apparmor="STATUS" operation="profile_load" name="/usr/share/gdm/guest-session/Xsession" pid=1110 comm="apparmor_parser"
Nov 21 10:13:47 ean5533-EP43-UD3L kernel: [   11.032025] type=1400 audit(1290352427.313:6): apparmor="STATUS" operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" pid=1114 comm="apparmor_parser"
Nov 21 10:13:47 ean5533-EP43-UD3L kernel: [   11.032065] type=1400 audit(1290352427.313:7): apparmor="STATUS" operation="profile_load" name="/usr/sbin/tcpdump" pid=1115 comm="apparmor_parser"
Nov 21 10:13:47 ean5533-EP43-UD3L kernel: [   11.032279] type=1400 audit(1290352427.313:8): apparmor="STATUS" operation="profile_load" name="/usr/sbin/cupsd" pid=1114 comm="apparmor_parser"
Nov 21 10:13:47 ean5533-EP43-UD3L kernel: [   11.033738] type=1400 audit(1290352427.313:9): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient3" pid=1111 comm="apparmor_parser"
Nov 21 10:13:47 ean5533-EP43-UD3L kernel: [   11.033942] type=1400 audit(1290352427.313:10): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=1111 comm="apparmor_parser"
Nov 21 10:13:47 ean5533-EP43-UD3L kernel: [   11.034053] type=1400 audit(1290352427.313:11): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=1111 comm="apparmor_parser"
Nov 21 10:13:47 ean5533-EP43-UD3L avahi-daemon[1094]: No service file found in /etc/avahi/services.
Nov 21 10:13:47 ean5533-EP43-UD3L NetworkManager[1092]:    Ifupdown: get unmanaged devices count: 0
Nov 21 10:13:47 ean5533-EP43-UD3L NetworkManager[1092]: <info> found WiFi radio killswitch rfkill0 (at /sys/devices/pci0000:00/0000:00:13.2/usb2/2-2/2-2:1.0/ieee80211/phy0/rfkill0) (driver <unknown>)
Nov 21 10:13:47 ean5533-EP43-UD3L NetworkManager[1092]: <info> WiFi enabled by radio killswitch; enabled by state file
Nov 21 10:13:47 ean5533-EP43-UD3L NetworkManager[1092]: <info> WWAN enabled by radio killswitch; enabled by state file
Nov 21 10:13:47 ean5533-EP43-UD3L NetworkManager[1092]: <info> WiMAX enabled by radio killswitch; enabled by state file
Nov 21 10:13:47 ean5533-EP43-UD3L NetworkManager[1092]: <info> Networking is enabled by state file
[B][I]Nov 21 10:13:47 ean5533-EP43-UD3L NetworkManager[1092]: <info> (eth1): carrier is OFF
Nov 21 10:13:47 ean5533-EP43-UD3L NetworkManager[1092]: <info> (eth1): new Ethernet device (driver: 'r8169' ifindex: 2)
Nov 21 10:13:47 ean5533-EP43-UD3L NetworkManager[1092]: <info> (eth1): exported as /org/freedesktop/NetworkManager/Devices/0
Nov 21 10:13:47 ean5533-EP43-UD3L NetworkManager[1092]: <info> (eth1): now managed
Nov 21 10:13:47 ean5533-EP43-UD3L NetworkManager[1092]: <info> (eth1): device state change: 1 -> 2 (reason 2)
Nov 21 10:13:47 ean5533-EP43-UD3L NetworkManager[1092]: <info> (eth1): bringing up device.
Nov 21 10:13:47 ean5533-EP43-UD3L kernel: [   11.057756] r8169 0000:02:00.0: eth1: link down
Nov 21 10:13:47 ean5533-EP43-UD3L kernel: [   11.058165] ADDRCONF(NETDEV_UP): eth1: link is not ready
Nov 21 10:13:47 ean5533-EP43-UD3L NetworkManager[1092]: <info> (eth1): preparing device.
Nov 21 10:13:47 ean5533-EP43-UD3L NetworkManager[1092]: <info> (eth1): deactivating device (reason: 2).[/I][/B]
Nov 21 10:13:47 ean5533-EP43-UD3L avahi-daemon[1094]: Network interface enumeration completed.
Nov 21 10:13:47 ean5533-EP43-UD3L avahi-daemon[1094]: Registering HINFO record with values 'X86_64'/'LINUX'.
Nov 21 10:13:47 ean5533-EP43-UD3L avahi-daemon[1094]: Server startup complete. Host name is ean5533-EP43-UD3L.local. Local service cookie is 2489574912.
**Nov 21 10:13:47 ean5533-EP43-UD3L NetworkManager[1092]: <info> Added default wired connection 'Auto eth1' for /sys/devices/pci0000:00/0000:00:05.0/0000:02:00.0/net/eth1**
...
```

---

### Post by dcstar on 2010-11-22
This what happens on my system:
```

Nov 22 17:57:38 dc-master NetworkManager: <info>  Waking up...
Nov 22 17:57:38 dc-master NetworkManager: <info>  (eth0): now managed
Nov 22 17:57:38 dc-master NetworkManager: <info>  (eth0): device state change: 1 -> 2 (reason 2)
Nov 22 17:57:38 dc-master NetworkManager: <info>  (eth0): bringing up device.
Nov 22 17:57:38 dc-master kernel: [ 2197.329587] r8169: eth0: link up
Nov 22 17:57:38 dc-master kernel: [ 2197.329599] r8169: eth0: link up
Nov 22 17:57:38 dc-master NetworkManager: <info>  (eth0): preparing device.
Nov 22 17:57:38 dc-master NetworkManager: <info>  (eth0): deactivating device (reason: 2).
Nov 22 17:57:38 dc-master NetworkManager: <info>  (eth0): carrier now ON (device state 2)
Nov 22 17:57:38 dc-master NetworkManager: <info>  (eth0): device state change: 2 -> 3 (reason 40)
Nov 22 17:57:38 dc-master NetworkManager: <info>  Activation (eth0) starting connection 'Auto eth0'
Nov 22 17:57:38 dc-master NetworkManager: <info>  (eth0): device state change: 3 -> 4 (reason 0)
Nov 22 17:57:38 dc-master NetworkManager: <info>  Activation (eth0) Stage 1 of 5 (Device Prepare) scheduled...
Nov 22 17:57:38 dc-master NetworkManager: <info>  Activation (eth0) Stage 1 of 5 (Device Prepare) started...
Nov 22 17:57:38 dc-master NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) scheduled...
Nov 22 17:57:38 dc-master NetworkManager: <info>  Activation (eth0) Stage 1 of 5 (Device Prepare) complete.
Nov 22 17:57:38 dc-master NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) starting...
Nov 22 17:57:38 dc-master NetworkManager: <info>  (eth0): device state change: 4 -> 5 (reason 0)
Nov 22 17:57:38 dc-master NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) successful.
Nov 22 17:57:38 dc-master NetworkManager: <info>  Activation (eth0) Stage 3 of 5 (IP Configure Start) scheduled.
Nov 22 17:57:38 dc-master NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) complete.
Nov 22 17:57:38 dc-master NetworkManager: <info>  Activation (eth0) Stage 3 of 5 (IP Configure Start) started...
Nov 22 17:57:38 dc-master NetworkManager: <info>  (eth0): device state change: 5 -> 7 (reason 0)
Nov 22 17:57:38 dc-master NetworkManager: <info>  Activation (eth0) Stage 4 of 5 (IP4 Configure Get) scheduled...
Nov 22 17:57:38 dc-master NetworkManager: <info>  Activation (eth0) Stage 4 of 5 (IP6 Configure Get) scheduled...
Nov 22 17:57:38 dc-master NetworkManager: <info>  Activation (eth0) Stage 3 of 5 (IP Configure Start) complete.
Nov 22 17:57:38 dc-master NetworkManager: <info>  Activation (eth0) Stage 4 of 5 (IP4 Configure Get) started...
Nov 22 17:57:38 dc-master NetworkManager: <info>  Activation (eth0) Stage 4 of 5 (IP4 Configure Get) complete.
Nov 22 17:57:38 dc-master NetworkManager: <info>  Activation (eth0) Stage 4 of 5 (IP6 Configure Get) started...
Nov 22 17:57:38 dc-master NetworkManager: <info>  Activation (eth0) Stage 5 of 5 (IP Configure Commit) scheduled...
Nov 22 17:57:38 dc-master NetworkManager: <info>  Activation (eth0) Stage 4 of 5 (IP6 Configure Get) complete.
Nov 22 17:57:38 dc-master NetworkManager: <info>  Activation (eth0) Stage 5 of 5 (IP Configure Commit) started...
Nov 22 17:57:39 dc-master avahi-daemon[1042]: Joining mDNS multicast group on interface eth0.IPv4 with address 192.168.100.10.
Nov 22 17:57:39 dc-master avahi-daemon[1042]: New relevant interface eth0.IPv4 for mDNS.
Nov 22 17:57:39 dc-master vmnetBridge: Adding interface eth0 index:2
Nov 22 17:57:39 dc-master vmnetBridge: Started bridge eth0 to virtual network 0.
Nov 22 17:57:39 dc-master kernel: [ 2197.631630] /dev/vmnet: open called by PID 1939 (vmnet-bridge)
Nov 22 17:57:39 dc-master kernel: [ 2197.631655] /dev/vmnet: hub 0 does not exist, allocating memory.
Nov 22 17:57:39 dc-master kernel: [ 2197.631703] /dev/vmnet: port on hub 0 successfully opened
Nov 22 17:57:39 dc-master kernel: [ 2197.631736] bridge-eth0: up
Nov 22 17:57:39 dc-master kernel: [ 2197.631744] bridge-eth0: attached
Nov 22 17:57:39 dc-master avahi-daemon[1042]: Registering new address record for 192.168.100.10 on eth0.IPv4.
Nov 22 17:57:39 dc-master NetworkManager: <info>  (eth0): device state change: 7 -> 8 (reason 0)
Nov 22 17:57:39 dc-master vmnetBridge: RTM_NEWROUTE: index:2
Nov 22 17:57:40 dc-master avahi-daemon[1042]: Registering new address record for fe80::21f:d0ff:fed4:a514 on eth0.*.
Nov 22 17:57:41 dc-master NetworkManager: <info>  Policy set 'Auto eth0' (eth0) as default for routing and DNS.
Nov 22 17:57:41 dc-master NetworkManager: <info>  Activation (eth0) successful, device activated.
Nov 22 17:57:41 dc-master NetworkManager: <info>  Activation (eth0) Stage 5 of 5 (IP Configure Commit) complete.
```

---

### Post by ean5533 on 2010-11-22
> **dcstar said:**
> This what happens on my system:
...

Yeah, I'm just gonna go ahead and call it a dead ethernet port. It's a pity, but it's nothing a $10 NIC card won't fix. (Cheaper than shipping back the motherboard to get it replaced, and it doesn't leave me with no computer for two weeks)

---

### Post by dcstar on 2010-11-23
> **ean5533 said:**
> Yeah, I'm just gonna go ahead and call it a dead ethernet port. It's a pity, but it's nothing a $10 NIC card won't fix. (Cheaper than shipping back the motherboard to get it replaced, and it doesn't leave me with no computer for two weeks)

Ethernet cards in PCs are usually the first earthed device on the connection chain of people's ADSL services. Lightening strikes within a geographical area can cause induced spikes which travel along the phone lines looking for a path to earth, and guess where they sometimes find the easiest path?.....

Had any storms nearby recently?

---

### Post by ean5533 on 2010-11-23
> **dcstar said:**
> Ethernet cards in PCs are usually the first earthed device on the connection chain of people's ADSL services. Lightening strikes within a geographical area can cause induced spikes which travel along the phone lines looking for a path to earth, and guess where they sometimes find the easiest path?.....

Had any storms nearby recently?

No lightning strikes nearby in years, but now that I have a NIC I'm sure that we'll have one within the week. That's my luck.

I'm not sure I understand though how using a NIC changes anything. Either the surge travels from the wall to NIC to motherboard to case to ground, or without a NIC it travels from the wall to motherboard to case to ground. How does adding a NIC make it any more likely to happen?

---

