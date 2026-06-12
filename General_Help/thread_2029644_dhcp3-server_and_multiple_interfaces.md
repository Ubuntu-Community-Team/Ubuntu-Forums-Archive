---
title: "dhcp3-server and multiple interfaces"
date: 2012-07-19
forum: General Help
---

### Post by cheesewizz on 2012-07-19
Hi

I've been using Ubuntu for almost 4 years
and I want to update my DHCP Server

I have eth0 : ISP IP Address
eth1 : Local IP 192.168.50.0 (DHCP Server)
eth1.10 : Virtual Lan with Local IP 192.168.1.0 

in my interfaces
/etc/network/interfaces
I added below:
--------------
auto lo
iface lo inet loopback

mapping hotplug
        scritps grep
        map eth1

iface eth1 inet dhcp

auto eth1
iface eth1 inet static
    address 192.168.50.1
    netmask 255.255.255.0

auto eth1.10
iface eth1.10 inet static
        address 192.168.1.1
        netmask 255.255.255.0
        broadcast 192.168.1.255
        network 192.168.1.0

auto eth1

--------------
then i added this INTERFACES="eth1 eth1.10" under /etc/default/dhcp3-server
--------------

In my DHCP Conf:

ddns-update-style none;
ignore client-updates;
log-facility local7;

subnet 192.168.50.0 netmask 255.255.255.0 {
        option routers 192.168.50.1;
        option subnet-mask 255.255.255.0;
        option domain-name-servers 192.168.50.253, 210.14.32.21, 210.14.32.22;
        option ip-forwarding off;
        default-lease-time 21600;
        max-lease-time 43200;
        ddns-updates on;
        ddns-update-style interim;
        ddns-domainname "computer.tac";
        ddns-rev-domainname "in.addr.arpa";
        ignore client-updates;


host pc1 {
 hardware ethernet 00:16:D4:EB:06:04;
 fixed-address 192.168.50.101;
 option domain-name-servers 192.168.50.253, 210.14.32.21, 210.14.32.22;
 }

}
subnet 192.168.1.0 netmask 255.255.255.0 {

        option routers                  192.168.1.1;
        option subnet-mask              255.255.255.0;
        option broadcast-address        192.168.1.255;
        option domain-name-servers      192.168.50.253;
        option ntp-servers              192.168.50.224;
        option netbios-name-servers     192.168.1.1;
        option netbios-node-type 2;

        default-lease-time 86400;
        max-lease-time 86400;

        host mac49 {
                hardware ethernet 00:0D:60:CB:F7:E3;
                fixed-address 192.168.1.100;
        }
}

-------------

and I run ip route command

root@firewall-desktop:~# ip route
1xx.xx.xx.xx/29 dev eth0  proto kernel  scope link  src 1xx.xx.xx.xx  metric 1 
192.168.50.0/24 dev eth1  proto kernel  scope link  src 192.168.50.1 
192.168.1.0/24 dev eth1.10  proto kernel  scope link  src 192.168.1.1 
169.254.0.0/16 dev eth1  scope link  metric 1000 
default via 127.100.32.73 dev eth0  proto static 
root@firewall-desktop:~# 

root@firewall-desktop:~# route
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
1xx.xx.xx.xx    *               255.255.255.248 U     1      0        0 eth0
192.168.50.0    *               255.255.255.0   U     0      0        0 eth1
192.168.1.0     *               255.255.255.0   U     0      0        0 eth1.10
link-local      *               255.255.0.0     U     1000   0        0 eth1
default         127.100.32.73.st 0.0.0.0         UG    0      0        0 eth0
root@firewall-desktop:~# 


the problem the subnet 2 which is 192.168.1.0
its not working I assigned static on mac49 but doesnt detect it

please anyone can guide me


thanks

---

