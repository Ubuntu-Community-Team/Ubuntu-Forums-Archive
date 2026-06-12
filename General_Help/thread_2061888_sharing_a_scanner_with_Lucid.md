---
title: "sharing a scanner with Lucid"
date: 2012-09-23
forum: General Help
---

### Post by graylion on 2012-09-23
Hi all

I have read this howto: [http://ubuntuforums.org/showthread.php?t=1519201](http://ubuntuforums.org/showthread.php?t=1519201) and I have the following situation:

on the server:

#scanimage -L
device `epson2:libusb:003:002' is a Epson Perfection1240 flatbed scanner

so the scanner gets found.

I added the relevant lines to xinet.conf, services, saned.conf, defaults

I can telnet from the client to port 6566

But: the client does not find the scanner

anybody have an idea?

#cat /etc/default/saned 
# Defaults for the saned initscript, from sane-utils

# Set to yes to start saned
RUN=yes

# Set to the user saned should run as
RUN_AS_USER=saned

----------------------

#cat /etc/xinetd.d/saned 
              # default: off
              # description: The sane server accepts requests
              # for network access to a local scanner via the
              # network.
              service sane-port
              {
                 port        = 6566
                 socket_type = stream
                 wait        = no
                 user        = saned
                 group       = saned
                 server      = /usr/sbin/saned
              }

---------------------

#cat /etc/sane.d/saned.conf 
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
data_portrange = 10000 - 10100


## Access list
# A list of host names, IP addresses or IP subnets (CIDR notation) that
# are permitted to use local SANE devices. IPv6 addresses must be enclosed
# in brackets, and should always be specified in their compressed form.
#
# The hostname matching is not case-sensitive.

#scan-client.somedomain.firm
#192.168.0.1
172.16.2.0/24
#[2001:7a8:185e::42:12]
#[2001:7a8:185e::42:12]/64

# NOTE: /etc/inetd.conf (or /etc/xinetd.conf) and
# /etc/services must also be properly configured to start
# the saned daemon as documented in saned(8), services(4)
# and inetd.conf(4) (or xinetd.conf(5)).

I have tried disabling the data port range - same effect

What am I missing?

Thanks!

---

