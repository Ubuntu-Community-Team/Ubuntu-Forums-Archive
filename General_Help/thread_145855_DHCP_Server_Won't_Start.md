---
title: "DHCP Server Won't Start"
date: 2006-03-17
forum: General Help
---

### Post by Ignite_nz on 2006-03-17
Hi there,

I'm having problems with the DHCP-3 server I installed earlier on today. I installed it with the following command:```
sudo apt-get install dhcp3-server
```

It installed correctly, however it failed to start the server, so I thought it must be becuase I hadn't edited the configuration file, so I edited it, and this is what it now looks like:

*Note the stuff in BOLD is what I changed.*```
nick@ubuntu:/etc/dhcp3$ cat /etc/dhcp3/dhcpd.conf
#
# Sample configuration file for ISC dhcpd for Debian
#
# $Id: dhcpd.conf,v 1.1.1.1 2002/05/21 00:07:44 peloy Exp $
#

# The ddns-updates-style parameter controls whether or not the server will
# attempt to do a DNS update when a lease is confirmed. We default to the
# behavior of the version 2 packages ('none', since DHCP v2 didn't
# have support for DDNS.)
ddns-update-style none;

# option definitions common to all supported networks...
#option domain-name "example.org";
**option domain-name-servers ns1.orcon.net.nz, ns2.orcon.net.nz;**

default-lease-time 600;
max-lease-time 7200;

# If this DHCP server is the official DHCP server for the local
# network, the authoritative directive should be uncommented.
#authoritative;

# Use this to send dhcp log messages to a different log file (you also
# have to hack syslog.conf to complete the redirection).
log-facility local7;

# No service will be given on this subnet, but declaring it helps the
# DHCP server to understand the network topology.

#subnet 10.152.187.0 netmask 255.255.255.0 {
#}

# This is a very basic subnet declaration.

[B]subnet 192.168.7.0  netmask 255.255.255.0 {
  range 192.168.7.2 192.168.7.255;
  option routers 192.168.7.1;
}[/B]

# This declaration allows BOOTP clients to get dynamic addresses,
# which we don't really recommend.

#subnet 10.254.239.32 netmask 255.255.255.224 {
#  range dynamic-bootp 10.254.239.40 10.254.239.60;
#  option broadcast-address 10.254.239.31;
#  option routers rtr-239-32-1.example.org;
#}

# A slightly different configuration for an internal subnet.
#subnet 10.5.5.0 netmask 255.255.255.224 {
#  range 10.5.5.26 10.5.5.30;
#  option domain-name-servers ns1.internal.example.org;
#  option domain-name "internal.example.org";
#  option routers 10.5.5.1;
#  option broadcast-address 10.5.5.31;
#  default-lease-time 600;
#  max-lease-time 7200;
#}

# Hosts which require special configuration options can be listed in
# host statements.   If no address is specified, the address will be
# allocated dynamically (if possible), but the host-specific information
# will still come from the host declaration.

#host passacaglia {
#  hardware ethernet 0:0:c0:5d:bd:95;
#  filename "vmunix.passacaglia";
#  server-name "toccata.fugue.com";
#}

# Fixed IP addresses can also be specified for hosts.   These addresses
# should not also be listed as being available for dynamic assignment.
# Hosts for which fixed IP addresses have been specified can boot using
# BOOTP or DHCP.   Hosts for which no fixed address is specified can only
# be booted with DHCP, unless there is an address range on the subnet
# to which a BOOTP client is connected which has the dynamic-bootp flag
# set.
#host fantasia {
#  hardware ethernet 08:00:07:26:c0:a5;
#  fixed-address fantasia.fugue.com;
#}

# You can declare a class of clients and then do address allocation
# based on that.   The example below shows a case where all clients
# in a certain class get addresses on the 10.17.224/24 subnet, and all
# other clients get addresses on the 10.0.29/24 subnet.

#class "foo" {
#  match if substring (option vendor-class-identifier, 0, 4) = "SUNW";
#}

#shared-network 224-29 {
#  subnet 10.17.224.0 netmask 255.255.255.0 {
#    option routers rtr-224.example.org;
#  }
#  subnet 10.0.29.0 netmask 255.255.255.0 {
#    option routers rtr-29.example.org;
#  }
#  pool {
#    allow members of "foo";
#    range 10.17.224.10 10.17.224.250;
#  }
#  pool {
#    deny members of "foo";
#    range 10.0.29.10 10.0.29.230;
#  }
#}

```After changing the .conf file, I'm still recieving the following error```
nick@ubuntu:/etc/dhcp3$ sudo /etc/init.d/dhcp3-server restart
 * Stopping DHCP server...                                               [fail]
 * Starting DHCP server...                                               [fail]

```

Another question, ```
option routers 192.168.7.2;
``` I put the IP address of my router here, is this the correct thing to do?

---

### Post by Ignite_nz on 2006-03-17
Anyone? Help would be greatly appreciated.....:)

---

### Post by casper_2095 on 2006-03-17
I don't serve dhcp from ubuntu so I can't test things for yet and be specific.  But your config file *looks* ok.  I'd suggest you copy the default config file someplace you can refer back to if necessary and then trim out all the comments.

```

#my own dhcp server
#
ddns-update-style none;
option domain-name-servers ns1.orcon.net.nz, ns2.orcon.net.nz;
default-lease-time 600;
max-lease-time 7200;
log-facility local7;
option routers 192.168.7.2;

subnet 192.168.7.0  netmask 255.255.255.0 {
  range 192.168.7.2 192.168.7.255;
  option routers 192.168.7.1;
}
```

The routers is fine.  The range should stop at 254 since 255 is the broadcast.  Look in /var/logs for some hints as to why it isn't starting.

---

### Post by casper_2095 on 2006-03-17
Um, I'm running dhcp from OpenBSD and it needs a second config file "/etc/dhcpd.interfaces" to declare the interfaces on which you actually want dhcpd to listen.  Dunno if this is true for the ubuntu version.  It simply has this in it...

```
# List of network interfaces served by dhcpd(8).
#
fxp0
```

---

### Post by Ignite_nz on 2006-03-17
Casper, I have that file also, and my interface is set to eth0. However I have two networkcards in my PC, so I will add the second one to the list also, so it will be eth0 and eth1. 

I have just simplified the config file right down to the un-commented code only. The rest is gone, but still no luck. The server fails when starting :(

---

### Post by Ignite_nz on 2006-03-17
But have no fear, I fixed it. It wasn't working because my settings in my Ubuntu machine were still from my old DHCP server in my Router,which runs at 10.x.x.x, and is really nasty, but all is fixed now :)!

I love ubuntu!

---

