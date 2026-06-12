---
title: "IPMI takes control of IP"
date: 2011-06-10
forum: General Help
---

### Post by niclaso on 2011-06-10
My Dell T300 is running Ubuntu server 11.04.

I'm trying to setup an IPMI system, so I can turn on my server when it's offline. It works fine when the server is turned off,
but when the operating system is on, IPMI will not share its IP with the OS. The OS and IPMI constantly changing which one who can connect through the IP.

I installed IPMI using these commands:
apt-get install openipmi ipmitool
echo "ipmi_devintf" >> /etc/modules
echo "ipmi_si" >> /etc/modules
I configured the IP, login and password in the BIOS.
IPMI IP=192.168.1.2

I have two network ports. The first one is for public usage and second one is locally only.

/etc/network/interfaces
# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet static
        address 192.168.1.2
        netmask 255.255.255.0
        network 192.168.1.0
        broadcast 192.168.1.255
        gateway 192.168.1.1

# The secondary network interface
auto eth1
iface eth1 inet static
        address 192.168.1.3
        netmask 255.255.255.0
        network 192.168.1.0

---

