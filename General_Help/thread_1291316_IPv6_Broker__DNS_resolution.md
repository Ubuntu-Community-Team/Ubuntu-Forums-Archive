---
title: "IPv6 Broker / DNS resolution?"
date: 2009-10-14
forum: General Help
---

### Post by xdemo on 2009-10-14
Hi there, i am trying to enable hostmasking w/ vhost for irc usage/anonymity. So far i have installed and setup tspc and registered an account with freenet6. I have also made an account on afraid.org for their free dns subdomains. I have experience with setting this up before on a windows vista pc, the process is fairly similar, but a little confusion....

I have followed some easy explained steps on various tutorials for enabling the ipv6 tunnel /broker to work properly. All is good, and i can connect to ipv6 enabled ircd servers

e.g: my hostmask/tunnel end-point now shows as
* [demo] is connecting from *@********.broker.freenet6.net 2001:5c0:1000:b::4351
under a /whois

Is 2001:5c0:1104:d400::1/64 my delegated prefix as of which would show in the "windows" client? As far as im aware, the address is being advertised on ifconfig, so it should appear this is the address i need to insert on the afraid.org website for ipv6 reverse lookup?

Heres a paste from my terminal of my wifi connection:

```
demo@jaunty:~$ ifconfig ra0
ra0       Link encap:Ethernet  HWaddr xx:xx:xx:xx:xx:xx  
          inet addr:192.168.1.64  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: 2001:5c0:1104:d400::1/64 Scope:Global
          inet6 addr: fe80::21c:dfff:fe6a:4398/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:16473 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1742 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:3168214 (3.1 MB)  TX bytes:157373 (157.3 KB)

demo@jaunty:~$ 
```

I gave freedns/afraid about 48 hours for their dns to update, but it seems im doing something wrong...

This is the code ipv6 reverse subnet ([http://freedns.afraid.org/reverse/](http://freedns.afraid.org/reverse/)) i have added, (the one advertised on ifconfig):
```
2001:5c0:1104:d400::1/64	add record | delete subnet
2001:05c0:1104:d400:0000:0000:0000:0001	ding.some.eviltorrents.com	remove
```

And on Sub-domain section ([http://freedns.afraid.org/subdomain/](http://freedns.afraid.org/subdomain/)) i have this set to an AAAA record:
```
eviltorrents.com	[ add ]
	ding.some.eviltorrents.com	AAAA	2001:05c0:1104:d400:0000:0000:0000:0001
```

Either this is the wrong address i have added to the afraid.org freedns website, or i have set up something wrong.

Do i need to use my tunnel endpoint for dns?
(ie the one in my actual connection displayed by the irc server 2001:5c0:1000:b::435)

Also, this may help: here is my /etc/tsp/tspc.conf in case it isnt setup correctly.
```
#-----------------------------------------------------------------------------
# tspc.conf
#-----------------------------------------------------------------------------
#
# This source code copyright (c) Hexago Inc. 2002-2004.
#
# This program is free software; you can redistribute it and/or modify it 
# under the terms of the GNU General Public License (GPL) Version 2, 
# June 1991 as published by the Free  Software Foundation.
#
# This program is distributed in the hope that it will be useful, 
# but WITHOUT ANY WARRANTY;  without even the implied warranty of 
# MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  
# See the GNU General Public License for more details.
#
# You should have received a copy of the GNU General Public License 
# along with this program; see the file GPL_LICENSE.txt. If not, write 
# to the Free Software Foundation, Inc., 59 Temple Place, Suite 330, Boston, 
# MA 02111-1307 USA
#------------------------------------------------------------------------------

#
# authentication method:
#  auth_method=any|digest-md5|anonymous|plain
#   any is the prefered one, since the most secure mechanism common to
#    the client and the broker will be used.
#   digest-md5 is sending the username in clear, but no password is sent.
#   plain is sending both username and password in clear.
#   anonymous sends no username and no password
#  recommended: any
auth_method=any

#
# IPv4 address of the client for its tunnel endpoint:
#  client_v4=auto|A.B.C.D (valid ipv4 address)
#  auto = tspc will find the primary ipv4 address
#   on the operating system
#
client_v4=auto

#
# user identification:
#  userid=anonymous|your_userid
#  anonymous means no userid. With anonymous, you don't need to register
#   to get an userid from the broker. However, prefixes (router mode) nor
#   permanent ipv6 address are available in anonymous mode.
#  your_userid means the userid you registered to the broker. The userid
#   must be using only legal dns label names (eg: [a-zA-Z0-9-] ) since
#   the userid is used inside your user hostname.
userid=***************

#
# password:
# passwd=your_password
#  leave empty if userid=anonymous
#  your_password means the password you have been assigned with your
#   userid
passwd=***************

#
# Name of the script:
# template=checktunnel|linux
#
# the value is the file name of the script in the /usr/lib/tspc directory
# The script will be executed after the TSP session is completed. The script
#  is configuring the tunnel interface and routes.
# checktunnel is only printing information and does not configure any tunnel
# setup will do the actual work
# you could customize your own script, name it and put the filename in 
#  the template variable.
# on unix, '.sh' is added to the name of the script. 
# on windows, '.bat' is added to the name of the script.
# 
template=linux

#
# 'server' is the tunnel broker identifier
#   Value is the tunnel broker IP address or FQDN and an optional port number
#   The default port number is 3653.
#  
# Examples:
# server=hostname # FQDN
# server=A.B.C.D  # IPv4 address
# server=hostname:port_number  
# server=A.B.C.D:port_number
#
# For users with accounts, 'server' should be set to the Freenet6 
# tunnel broker with authenticated accounts (broker.freenet6.net)
server=montreal.freenet6.net
#
# The default value is the Freenet6 tunnel broker for 
# anonymous accounts (anon.freenet6.net)
# server=anon.freenet6.net

#
#
# retry_delay=time
# retry tells the client to retry connection after time (seconds) in case of 
# failure or tunnel keepalive timeout (0 = no retry)
retry_delay=30

#
# Tunnel encapsulation mode:
# tunnel_mode can take the following values
# "v6v4"  request an IPv6 in IPv4 tunnel
# "v6udpv4" request an IPv6 in UDP in IPv4 tunnel (for clients behind a NAT)
# "v6anyv4"   Let the broker choose the tunnel mode appropriate for my client
#  with v6anyv4, the broker will discover if the client is behind a NAT or not
#   and will offer to the TSP client the correct tunnel mode.
# recommended is: v6anyv4
tunnel_mode=v6anyv4

#
# Tunnel Interface name:
# Interface name to use to create the tunnel. This is OS dependent
# and the default is choosen based on the OS. 
# if_tunnel_v6v4 is the tunnel interface name for the v6v4 encapsulation mode
# if_tunnel_v6udpv4 is the tunnel interface name for the v6udpv4 encap mode
if_tunnel_v6v4=sit1
if_tunnel_v6udpv4=tun

#
# proxy_client indicates that this client acts as a TSP proxy for
# some remote client tunnel endpoint machine. Typically, this is set to "yes" if
# we are running this client on a machine that will NOT be configuring
# the tunnel endpoint (for example, using the cisco template).
# This should be used with a static IPv4 address in client_v4 variable.
# NOTE: proxy_client=yes is incompatible with tunnel_mode=v6udpv4
# The default is "no"
proxy_client=no

#
# Keepalive for v6udpv4 tunnels:
#  keepalive indicates that this client will send keepalives to keep the
#   tunnel active (v6udpv4 tunnel) and detect inactive tunnel (no response from
#   server). When a tunnel is determined to be inactive, the TSP client
#   automatically reconnects to the server.
# keepalive_interval is a suggestion from the TSP client to the broker
#  for the interval between two keepalive messages. The broker
#  may impose a different interval value to the client if the interval 
#  value is too low.
# keepalive is "yes" by default
# keepalive_interval is 30 seconds by default
keepalive=yes
keepalive_interval=30

#
# Logging facility uses syslog on Unix platforms
#syslog_facility=DAEMON
#syslog_level=INFO

#
#---------------------
# Router configuration
#
# In order to configure the machine as a router, a prefix must be requested
# and an interface must be specified.  The prefix will be advertised
# through that interface.
#
# host_type=host|router
#  default = host.
host_type=router

#
# prefixlen specifies the required prefix length for the TSP client 
#  network. Valid values are 64 or 48. 64 is for one link. 48 is for
#  a whole enterprise network (65K links).
prefixlen=64

#
# if_prefix is the name of the OS interface that will be configured
#  with the first /64 of the received prefix from the broker and the
#  router advertisement daemon is started to advertise that prefix
#  on the if_prefix interface.
if_prefix=ra0

#
# For reverse DNS delegation of the prefix, define the following:
# Example: dns_server=mydnsserver.domain
dns_server=ns1.afraid.org:ns2.afraid.org:ns3.afraid.org:ns4.afraid.org

# end of tspc.conf
#-----------------------------------------------------------------------------
```

Thank you in advance if anyone knows. I'm stuck for ideas, spent hours tweaking some config settings in the above file, and various settings on the afraif website.

Hopefully if you have some experience with this, please help me thanks!

---

### Post by xdemo on 2009-10-14
Bump: anyone???

---

