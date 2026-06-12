---
title: "Ltsp Install trouble"
date: 2006-03-23
forum: General Help
---

### Post by swordsaint on 2006-03-23
[SIZE="3"][/SIZE]
I am using breezy. I have "/lts/vmlinuz-2.6.9-ltsp-3" setup in my dhcp as the filename and I can browse to its path and for the rootpath I have "192.168.1.53:/opt/ltsp/i386" and i can browse there also but  i don't know whats supposed to be in the rootpath there is just a bunch of folders and two short cuts that don't link to anything  called var and mnt. Also in ltspcfg it says that for tftp i dont have the -s flag. Thanks 

[B]subnet 192.168.1.0 netmask 255.255.255.0 #GREEN
{
	range 192.168.1.1 192.168.1.253;
	option subnet-mask 255.255.255.0;
	option domain-name "localdomain";
	option routers 192.168.1.254;
	option wpad "http://192.168.1.254:81/proxy.pac\n";
	option domain-name-servers 192.168.1.254;
	option ntp-servers 192.168.1.254;
	default-lease-time 3600;
	max-lease-time 7200;
	allow bootp;
} #GREEN

host fix0 # fvs318
{
	hardware ethernet 00:0f:b5:a9:5f:00;
	fixed-address 192.168.1.1;
}

host fix1 # rp114
{
	hardware ethernet 00:30:ab:08:86:0a;
	fixed-address 192.168.1.2;
}

[COLOR="RoyalBlue"]host fix2 # UBUNTU TERMINAL
{
	hardware ethernet 00:0C:29:23:04:87;
	fixed-address 192.168.1.4;
	next-server 192.168.1.53;
	filename "&quot;/lts/vmlinuz-2.4.26-ltsp-3&quot;;";
	option root-path "&quot;192.168.1.53:/opt/ltsp/i386&quot;;";[/COLOR]
}

host fix3 # ltsp VM
{
	hardware ethernet 00:0C:29:AE:CA:BD;
	fixed-address 192.168.1.53;
}

host fix4 # rh9mosix1
{
	hardware ethernet 00:0c:29:81:0d:6c;
	fixed-address 192.168.1.217;
}

host fix5 # dwl2100ap
{
	hardware ethernet 00:13:46:7a:db:29;
	fixed-address 192.168.2.50;
}
[/B]

---

