---
title: "UBUNTU CLoud nightmare"
date: 2011-11-16
forum: General Help
---

### Post by scubablue on 2011-11-16
Hello,

Set up Ubuntu 10.04 Enterprise following the guide

[https://help.ubuntu.com/community/UEC/CDInstall](https://help.ubuntu.com/community/UEC/CDInstall)

got stuck on step 6. 

The http:ip:8443 does not show images (I added a couple manually manually that I can see) 

I got a NC and on (SC/CC/Walrus)

The NC Interface settings
***********************
br0       Link encap:Ethernet  HWaddr 00:1a:92:1c:b3:7a  
          inet addr:10.150.252.45  Bcast:10.150.255.255  Mask:255.255.252.0
          inet6 addr: fe80::21a:92ff:fe1c:b37a/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:7173511 errors:0 dropped:0 overruns:0 frame:0
          TX packets:5023735 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:2873720512 (2.8 GB)  TX bytes:3080069909 (3.0 GB)

eth0      Link encap:Ethernet  HWaddr 00:1a:92:1c:b3:7a  
          inet6 addr: fe80::21a:92ff:fe1c:b37a/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:7175461 errors:0 dropped:0 overruns:0 frame:0
          TX packets:5461048 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:100 
          RX bytes:2974395662 (2.9 GB)  TX bytes:3108188885 (3.1 GB)
          Memory:c8200000-c8220000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:21891 errors:0 dropped:0 overruns:0 frame:0
          TX packets:21891 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:395092 (395.0 KB)  TX bytes:395092 (395.0 KB)

virbr0    Link encap:Ethernet  HWaddr ea:31:83:7a:1d:29  
          inet addr:192.168.122.1  Bcast:192.168.122.255  Mask:255.255.255.0
          inet6 addr: fe80::e831:83ff:fe7a:1d29/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:21929 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:707991 (707.9 KB)

The NC /etc/eucalyptus/eucalyptus.conf

***********************************
EUCALYPTUS="/"
EUCA_USER="eucalyptus"

# Affects: CLC, Walrus, SC
DISABLE_DNS="Y"
DISABLE_ISCSI="Y"
JVM_MEM="512m"

# Affects: CC, NC
# See: **NOTE** below
ENABLE_WS_SECURITY="Y"
LOGLEVEL="DEBUG"
VNET_PUBINTERFACE="br0"
VNET_PRIVINTERFACE="br0"
VNET_MODE="MANAGED-NOVLAN"

# Affects: CC
# See: **NOTE** below
CC_PORT="8774"
SCHEDPOLICY="ROUNDROBIN"
POWER_IDLETHRESH="300"
POWER_WAKETHRESH="300"
NC_SERVICE="axis2/services/EucalyptusNC"
VNET_DHCPDAEMON="/usr/sbin/dhcpd3"
VNET_DHCPUSER="dhcpd"
NODES=""
VNET_ADDRSPERNET="32"
#VNET_SUBNET=""
#VNET_NETMASK=""
#VNET_DNS=""
#VNET_PUBLICIPS=""

# Affects: NC
NC_PORT="8775"
HYPERVISOR="kvm"
MANUAL_INSTANCES_CLEANUP=0
VNET_BRIDGE="br0"
INSTANCE_PATH="/var/lib/eucalyptus/instances/"

SC/CC/WALRUS
***************** ifconfig
eth0      Link encap:Ethernet  HWaddr 00:04:23:ae:b0:62  
          inet addr:10.150.252.50  Bcast:10.150.255.255  Mask:255.255.252.0
          inet6 addr: fe80::204:23ff:feae:b062/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:81028 errors:0 dropped:0 overruns:0 frame:0
          TX packets:86423 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:100 
          RX bytes:42830383 (42.8 MB)  TX bytes:38279093 (38.2 MB)

eth0:metadata Link encap:Ethernet  HWaddr 00:04:23:ae:b0:62  
          inet addr:169.254.169.254  Bcast:0.0.0.0  Mask:255.255.255.255
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:416648 errors:0 dropped:0 overruns:0 frame:0
          TX packets:416648 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:228942720 (228.9 MB)  TX bytes:228942720 (228.9 MB)

SC/CC/WALRUS /etc/eucalyptus/eucalyptus.conf file

EUCALYPTUS="/"
EUCA_USER="eucalyptus"

# Affects: CLC, Walrus, SC
DISABLE_DNS="Y"
DISABLE_ISCSI="Y"
JVM_MEM="512m"

# Affects: CC, NC
# See: **NOTE** below
ENABLE_WS_SECURITY="Y"
LOGLEVEL="DEBUG"
VNET_PUBINTERFACE="eth0"
VNET_PRIVINTERFACE="eth0"
VNET_MODE="MANAGED-NOVLAN"

# Affects: CC
# See: **NOTE** below
CC_PORT="8774"
SCHEDPOLICY="ROUNDROBIN"
POWER_IDLETHRESH="300"
POWER_WAKETHRESH="300"
NC_SERVICE="axis2/services/EucalyptusNC"
VNET_DHCPDAEMON="/usr/sbin/dhcpd3"
VNET_DHCPUSER="dhcpd"
NODES=""
VNET_ADDRSPERNET="32"
#VNET_SUBNET=""
#VNET_NETMASK=""
#VNET_DNS=""
#VNET_PUBLICIPS=""

# Affects: NC
NC_PORT="8775"
HYPERVISOR="kvm"
MANUAL_INSTANCES_CLEANUP=0
VNET_BRIDGE="br0"
INSTANCE_PATH="/var/lib/eucalyptus/instances/"


My local network with access to the internet is 10.150.252.0/22 dg 10.150.252.2

I have tried to get this working for a month a no luck. I also get a ERROR 60 on the store tab on the [http://ip:8443](http://ip:8443). 

Tried hybridfox and get an instance error..Any ideas?

---

