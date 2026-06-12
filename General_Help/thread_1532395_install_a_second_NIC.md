---
title: "install a second NIC"
date: 2010-07-16
forum: General Help
---

### Post by speedygarth on 2010-07-16
hi there i`m having trouble installing a second NIC to the system it is being picked up during the bootup, but i cannot locate it from IFCONFIG so that i can assign it an IP address.

i`m trying to set it up as the gateway for the other computers on my network.

---

### Post by Iowan on 2010-07-16
You can try **ifconfig -a** - which should > display  all  interfaces  which are currently available, even if down
**sudo lshw -C network** will provide more information about the interface(s).

---

### Post by CyberAxe on 2010-07-23
I'm having a similar problem I've installed a second nic card the same make and model as the existing one (in Ubuntu Server 9.10)

lspci shows them both

```
00:08.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
00:09.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)

```

The first one still works as eth0 but the other one doesn't show up as eth1 like it should.

I've tried editing /etc/udev/rules.d/70-persistent-net.rules and deleting the following lines 

```
# PCI device 0x10ec:0x8139 (8139too)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="XX:XX:XX:XX:XX:XX", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"
```

Then rebooting but to no avail, i was also going to try copying the line then changing the mac address and eth0 to the new card and eth1 respectivley but the problem with these network cards is they don't show the mac address on the card themselves.

I've also tried running /lib/udev/write_net_rules but all I ever get are "missing $INTERFACE" errors.

The output from "sudo lshw -C network"

```
  *-network:0
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 8
       bus info: pci@0000:00:08.0
       logical name: eth0
       version: 10
       serial: XX:XX:XX:XX:XX:XX
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=full ip=192.168.1.2 latency=32 link=yes maxlatency=64 mingnt=32 multicast=yes port=MII speed=100MB/s
       resources: irq:10 ioport:dc00(size=256) memory:d5000000-d50000ff memory:c100000-c10ffff(prefetchable)
  *-network:1 UNCLAIMED
       description: Ethernet controller
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 9
       bus info: pci@0000:00:09.0
       version: 10
       width: 32 bits
       clock: 33MHz
       capabilities: pm cap_list
       configuration: latency=32 maxlatency=64 mingnt=32
       resources: ioport:e000(size=256) memory:c120000-c1200ff memory:c110000-c11ffff(prefetchable)

```

I also plan on using the second card as a gateway.

---

### Post by tarps87 on 2010-07-23
Are you still using Ubuntu 9.10? If so can you post the contents of
/etc/network/interfaces

---

### Post by CyberAxe on 2010-07-23
Here's mine

```
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet static
	address 192.168.1.2
	netmask 255.255.255.0
	#network 192.168.1.0
	broadcast 192.168.1.255
	gateway 192.168.1.1
	# dns-* options are implemented by the resolvconf package, if installed
	#dns-nameservers 212.104.130.9 212.104.130.65
	#dns-search network

#auto eth1
#iface eth1 inet static
#        address 192.168.2.254
#        netmask 255.255.255.0
#        #network 192.168.2.0
#        broadcast 192.168.2.255
#        gateway 192.168.2.1
	 #dns-* options are implemented by the resolvconf package, if installed
	 #dns-nameservers 212.104.130.9 212.104.130.65
	 #dns-search network

# Bridge interface
#auto br0
#iface br0 inet static
#    address 192.168.2.1
#    network 192.168.1.0
#    netmask 255.255.255.0
#    broadcast 192.168.1.255
#    bridge-ports eth0 wlan0


# Wireless Setup
#auto wlan0
#iface wlan0 inet static
#      address 192.168.2.1
#      netmask 255.255.255.0
#      broadcast 192.168.1.255
#      gateway 192.168.1.2
#      wireless-mode managed
#      wireless-channel 11
#      #wireless-essid SpringboardScotland
#      pre-up sleep 10
#      wpa-driver wext
#      wpa-ssid SpringboardScotland
#      wpa-ap-scan 1
#      wpa-proto WPA
#      wpa-pairwise TKIP
#      wpa-group TKIP
#      wpa-key-mgmt WPA-PSK
#      wpa-psk SpringboardNetworkLogin

# Bridge interface
#auto br0
#iface br0 inet static
#    address 192.168.2.1
#    network 192.168.1.0
#    netmask 255.255.255.0
#    broadcast 192.168.1.255
#    bridge-ports eth0 wlan0

```

I tried to get it working buy copying eth0 and renaming to eth1 and changing some of the values but commented it out due to not working

---

### Post by tarps87 on 2010-07-23
> **CyberAxe said:**
> 

I tried to get it working buy copying eth0 and renaming to eth1 and changing some of the values but commented it out due to not working

That was going to be my suggestion, usually works. However have you tried it with dhcp?
auto eth1
iface eth1 inet dhcp

also @speedygarth have you tried this also?

---

### Post by speedygarth on 2010-07-23
i managed to change the ip address of the new card but i still cannot browse the net from the other workstations, i have configured squid and even set the parameters that i need from the ACL file but all i see from the workstation trying to access the net is a page that says "IT WORKS!

do i need to make the second NIC a different IP and subnet or what! all i want is the second card to transfer the internet traffic from the old card to the local Ethernet network.
anyway i hope somebody helps coz i`m almost fed up!

---

### Post by tarps87 on 2010-07-23
I have never actually got round to setting up connection sharing, however this may help:
[https://help.ubuntu.com/community/Internet/ConnectionSharing](https://help.ubuntu.com/community/Internet/ConnectionSharing)

"IT WORKS!" sounds like the default Apache page

---

### Post by CyberAxe on 2010-07-23
> **tarps87 said:**
> That was going to be my suggestion, usually works. However have you tried it with dhcp?
auto eth1
iface eth1 inet dhcp

also @speedygarth have you tried this also?

I've not tried it with dhcp but I shall do so as soon as I get the chance. (The server's at work and I wont be back in till Tuesday)

Thanks.

---

### Post by speedygarth on 2010-07-26
I havent tried it with DHCP i`ll do that and see what happens but any hints on fixing that Apache message "It works".

---

### Post by CyberAxe on 2010-07-26
> **speedygarth said:**
> I havent tried it with DHCP i`ll do that and see what happens but any hints on fixing that Apache message "It works".

Did you setup Apache to use the hostname or the ip for the site your trying to run? as if you aren't attempting to access the exact address (dns / ip or however it was configured) that can usually cause that iirc

---

