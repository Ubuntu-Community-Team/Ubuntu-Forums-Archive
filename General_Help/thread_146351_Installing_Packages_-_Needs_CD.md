---
title: "Installing Packages - Needs CD"
date: 2006-03-18
forum: General Help
---

### Post by Ignite_nz on 2006-03-18
Hi There,

I'm having trouble, whenever I go to install a package, in this case it's mysql-server, my shell asks me to put the CD in, and this is getting annoying - as my server is in another room. Ubuntu never used to ask me for the CD, its only started doing it since I last did a fresh install. Here's what happens:```
root@ubuntu:~# apt-get install mysql-server
Reading package lists... Done
Building dependency tree... Done
The following extra packages will be installed:
  libdbd-mysql-perl libdbi-perl liblockfile1 libmysqlclient14
  libnet-daemon-perl libplrpc-perl mailx mysql-client postfix
Suggested packages:
  dbishell libcompress-zlib-perl mysql-doc procmail postfix-mysql
  postfix-pgsql postfix-ldap postfix-pcre
Recommended packages:
  libmysqlclient14-dev resolvconf
The following NEW packages will be installed:
  libdbd-mysql-perl libdbi-perl liblockfile1 libmysqlclient14
  libnet-daemon-perl libplrpc-perl mailx mysql-client mysql-server postfix
0 upgraded, 10 newly installed, 0 to remove and 2 not upgraded.
Need to get 6188kB/7344kB of archives.
After unpacking 18.0MB of additional disk space will be used.
Do you want to continue [Y/n]? y
Media change: please insert the disc labeled
 'Ubuntu 5.10 _Breezy Badger_ - Release i386 (20051012)'
in the drive '/cdrom/' and press enter

```

If I cant avoid this, is there any way I can mount a copy of the image to a fake drive?

---

### Post by oscar on 2006-03-18
edit your /etc/apt/sources.list and comment out the line that begins "deb cdrom:"

---

### Post by Ignite_nz on 2006-03-18
Thanks, I've done that, but there's another problem now, my Ubuntu machine can't get on the net. How do I make it so that my Ubuntu machine which has the DHCP server on it, get its IP address off its self?

---

### Post by powder on 2006-03-18
You have to give the DHCP server a static IP, it can't distribute itself an IP. ;)

---

### Post by Ignite_nz on 2006-03-18
OK this is weird, I cant get on my network at all now, however my DHCP server is handing out IP addresses fine, and the other machines can get on the network. Here is the config of my /etc/network/interfaces file:```

root@ubuntu:/etc/network# vim interfaces
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# This is a list of hotpluggable network interfaces.
# They will be activated automatically by the hotplug subsystem.
mapping hotplug
        script grep
        map eth0

# The primary network interface
iface eth0 inet static
        address 192.168.7.2
        netmask 255.255.255.0
        network 192.168.7.0
        broadcast 192.168.7.255
        gateway 192.168.7.2
        # dns-* options are implemented by the resolvconf package, if installed
        dns-nameservers 60.234.1.1, 60.234.2.1
```And here is the code of my /etc/dhcp3/dhcpd.conf file:```
root@ubuntu:/etc/network# vim interfaces
root@ubuntu:/etc/network# cd /etc/dhcp3/
root@ubuntu:/etc/dhcp3# vim dhcpd.conf
#
# Sample configuration file for ISC dhcpd for Debian
#
# $Id: dhcpd.conf,v 1.1.1.1 2002/05/21 00:07:44 peloy Exp $
#
ddns-update-style none;
option domain-name-servers 60.234.1.1, 60.234.2.1;
option broadcast-address 192.168.7.255;
default-lease-time 600;
max-lease-time 7200;
authoritative;
log-facility local7;
subnet 192.168.7.0  netmask 255.255.255.0 {
  range 192.168.7.3 192.168.7.254;
  option routers 192.168.7.1;
}

```

---

### Post by Ignite_nz on 2006-03-18
Fixed it, my gateway was wrong -_-

---

