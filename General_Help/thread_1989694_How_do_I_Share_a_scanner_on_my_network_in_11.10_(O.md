---
title: "How do I Share a scanner on my network in 11.10 (Oneiric Ocelot)"
date: 2012-05-28
forum: General Help
---

### Post by bennettg on 2012-05-28
Hi!

I am seeking help in trying to share a scanner on my home network.


I have a HP laserJet 3030 all-in-one (multifunction) laser printer attached via USB to a dell laptop running Ubuntu 11.10.  the dell laptop has a reserved ip address on my network of 192.168.1.135 and also functions as a print server to other computers on my network.  The HP laserJet 3030 all-in-one works as a printer for the other computers on the network via ipp://192.168.1.135:631/printers/Hewlett-Packard-hp-LaserJet-3030

I need to get the HP laserJet 3030 all-in-one to function as a network scanner, so that the Dell labtop at 192.168.1.135 is a scanner server and the other computers on the network are server clients.  The  hp laserjet 3030 is installed and working as a scanner on the dell laptop (server computer).

**Would someone be kind enough to confirm that these are the steps that should be taken? ** *I am particularily focused on user permissions and the appropriate editing of /etc/sane.d/saned.conf since the scanner server is at 192.168.1.135.*

_On the Dell Laptop (scanner server)_
1.  install sane

2.  Tell it to run sane as a server by editing /etc/default/saned to read: 
*****************************************************************
# Defaults for the saned initscript, from sane-utils

# Set to yes to start saned
RUN=Yes

# Set to the user saned should run as
RUN_AS_USER=saned
*****************************************************************


3.  Set the subnet that will be able to see the scanner by editing /etc/sane.d/saned.conf to read:
*****************************************************************
# saned.conf
# Configuration for the saned daemon

## Daemon options
# Port range for the data connection. Choose a range inside [1024 - 65535].
# Avoid specifying too large a range, for performance reasons.
#
# ONLY use this if your saned server is sitting behind a firewall. If your
# firewall is a Linux machine, we strongly recommend using the
# Netfilter nf_conntrack_sane connection tracking module instead.
#
# data_portrange = 10000 - 10100


## Access list
# A list of host names, IP addresses or IP subnets (CIDR notation) that
# are permitted to use local SANE devices. IPv6 addresses must be enclosed
# in brackets, and should always be specified in their compressed form.
#
# The hostname matching is not case-sensitive.

#scan-client.somedomain.firm
#192.168.0.1
192.168.0.1/24
#[2001:7a8:185e::42:12]
#[2001:7a8:185e::42:12]/64

# NOTE: /etc/inetd.conf (or /etc/xinetd.conf) and
# /etc/services must also be properly configured to start
# the saned daemon as documented in saned(8), services(4)
# and inetd.conf(4) (or xinetd.conf(5)).

******************************************************************

4.  correct permissions by sudo adduser saned lp
5.  restart saned by sudo service saned restart
6.  configure the Sane daemon to start automatically at boot by sudo update-rc.d saned defaults



_On other ubuntu machines on the network (clients)_

1.  add the server IP address of the dell laptop (scanner server) to /etc/sane.d/net.conf:
************************************************************************
# This is the net backend config file.

## net backend options
# Timeout for the initial connection to saned. This will prevent the backend
# from blocking for several minutes trying to connect to an unresponsive
# saned host (network outage, host down, ...). Value in seconds.
# connect_timeout = 60

## saned hosts
# Each line names a host to attach to.
# If you list "localhost" then your backends can be accessed either
# directly or through the net backend.  Going through the net backend
# may be necessary to access devices that need special privileges.
# localhost
192.168.1.135
************************************************************

2.  install xsane
3.  run xsane to verify that it sees the hp HP laserJet 3030 (network scanner)


I took some of this from older forum posts that did not involve ubuntu 11.10, but I am a noob.

Thanks in advance!

---

