---
title: "need help to share internet connection to android phone"
date: 2012-06-01
forum: General Help
---

### Post by Matadewa on 2012-06-01
hi all
i'm using ubuntu 10.10 and usb modem as my internet connection 
in windows sually i used connectifity, but in linux my friend suggest me to use hostapd

he success used it, but when i try, it's give result
```
matadewa@matadewa-K42Jc:~$ **sudo ap_ctl --start**
Starting hostapd
 You can view the log at /var/log/hostapd.log
Starting dnsmasq
SIOCSIFFLAGS: Operation not possible due to RF-kill
ioctl[SIOCSIFFLAGS]: Operation not possible due to RF-kill

dnsmasq: failed to create listening socket: Address already in use

```

then when i try to check hostapd log, this is the result
```
Configuration file: /etc/hostapd/hostapd.conf
nl80211 driver initialization failed.
wlan0: Unable to setup interface.

```

it's seem driver nl80211 not installed yet in my system
i found this link [http://linuxwireless.org/en/users/Documentation/hostapd]("http://linuxwireless.org/en/users/Documentation/hostapd")

but i think it's too complex for newbie like me and my english is worst
can anyone describe it with more simple way?
or maybe give another suggestion how to share interent conection to android phone

---

### Post by Sularco on 2012-06-01
I am assuming that you have installed the dhcp3-server package as well as hostapd? I believe on 10.10 this was required for DHCP IP address allocation. Could you also post the output of:

```

sudo rfkill list all

```

This would show if your WLAN card is locked in any way. The contents of your /etc/hostapd/hostapd.conf and /etc/dhcp3/dhcpd.conf files would also be very very helpful (the last one only if you have the dhcp3-server package installed).
The configuration which I used to successfully link up my Freerunner phone is here:

[http://exain.wordpress.com/2011/03/31/making-a-wifi-hotspot-access-point-using-linux-wifi-lan-cardusb-adapter/]("http://exain.wordpress.com/2011/03/31/making-a-wifi-hotspot-access-point-using-linux-wifi-lan-cardusb-adapter/")

I suggest you read through that document and try if that guide can help you resolve your problems. It certainly worked for me.

---

### Post by Matadewa on 2012-06-02
yes you're right i'm instaled too dhcp3-server
this is the output

***sudo rfkill list all***
```
matadewa@matadewa-K42Jc:~$ sudo rfkill list all
1: phy0: Wireless LAN
	Soft blocked: yes
	Hard blocked: no
matadewa@matadewa-K42Jc:~$ 

```

***etc/hostapd/hostapd.conf***
```
#konfigurasi hostapd untuk hotspot wifi
interface=wlan0
driver=nl80211
ssid=AP_matadewa
hw_mode=g
channel=1

#Jika ingin menggunakan password, hilangakan tanda (#)
#pada baris-baris dibawah ini
#untuk mengganti password, ganti nilai dari wpa_passphrase= (Indonesia Language)
#wpa=1
#wpa_passphrase=opensourcejaya
#wpa_key_mgmt=WPA-PSK
#wpa_pairwise=TKIP CCMP
#wpa_ptk_rekey=600
```

***/etc/dhcp3/dhcpd.conf***
*i just add bold and italic word in the bottom of content
```
#
# Sample configuration file for ISC dhcpd for Debian
#
# Attention: If /etc/ltsp/dhcpd.conf exists, that will be used as
# configuration file instead of this file.
#
# $Id: dhcpd.conf,v 1.1.1.1 2002/05/21 00:07:44 peloy Exp $
#

# The ddns-updates-style parameter controls whether or not the server will
# attempt to do a DNS update when a lease is confirmed. We default to the
# behavior of the version 2 packages ('none', since DHCP v2 didn't
# have support for DDNS.)
ddns-update-style none;

# option definitions common to all supported networks...
option domain-name "example.org";
option domain-name-servers ns1.example.org, ns2.example.org;

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

#subnet 10.254.239.0 netmask 255.255.255.224 {
#  range 10.254.239.10 10.254.239.20;
#  option routers rtr-239-0-1.example.org, rtr-239-0-2.example.org;
#}

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

[B][I]option subnet-mask 255.255.255.0;
default-lease-time 600;
max-lease-time 7200;

option domain-name-servers 8.8.8.8, 8.8.4.4 ;
subnet 192.168.1.0 netmask 255.255.255.0 {
range 192.168.1.10 192.168.1.254;
option broadcast-address 192.168.1.255;
option routers 192.168.1.1;
}[/I][/B]

```

yesterday after make a few changed like this [http://www.saranglebahinformatics.com/2012/03/21/tips-sharing-koneksi-internet-usb-modem-dari-ubuntu-ke-android/]("http://www.saranglebahinformatics.com/2012/03/21/tips-sharing-koneksi-internet-usb-modem-dari-ubuntu-ke-android/") **sorry it's indonesian language*
it's success to make i internet from my android phone and not show *nl80211 driver initialization failed.*
but this time i try to connect it again. . .it's failed again like before

---

### Post by Sularco on 2012-06-02
The webpage you quote is subscription only, so I can not see what modifications you have made. But wouldn't the message
```

Soft blocked: yes

```
indicate the cause of the problem? Therefore the command
```

rfkill unblock wifi

```
should unblock the wireless card, which you then could double-check with another
```

sudo rfkill list all

```
I would suspect that the network-manager grabs your wireless card on boot (that's why it is "Soft blocked") and that you have to unblock it before you can use it with hostapd. If you only want to use it with hostapd then I suppose you must prevent network-manager from grabbing it first.

---

