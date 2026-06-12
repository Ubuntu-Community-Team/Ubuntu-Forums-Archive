---
title: "seting up dhcp server in 11.10(error all the time)"
date: 2012-02-22
forum: General Help
---

### Post by mafi127 on 2012-02-22
Hello everyone,

I have been tryed to get dhcp3 server running in ubuntu 11.10 32bit two weeks now, but no success. I am relatively new to setting up Ubuntu Servers.


What I have done so far is:

```

apt-get install dhcp3-server
mv /etc/dhcp3/dhcpd.conf /etc/dhcp3/dhcpd.conf.backup
gedit /etc/dhcp3/dhcpd.conf

```The dhcpd.conf file I have edited this way

```

ddns-update-style ad-hoc;
default-lease-time 600;
max-lease-time 7200;
subnet 192.168.2.128 netmask 255.255.255.128 {
option subnet-mask 255.255.255.128;
option broadcast-address 192.168.2.255;
option routers 192.168.2.129;
option domain-name-servers 8.8.8.8;
range 192.168.2.130 192.168.2.140
}

```When I want to run dhcp3 then I got error( I dont have dhcp3 command only dhcp)
```

root@mafia:~# dhcpd -cf /etc/dhcp3/dhcpd.conf -pf /var/run/dhcp3-server/dhcpd.pid at0
Internet Systems Consortium DHCP Server 4.1.1-P1
Copyright 2004-2010 Internet Systems Consortium.
All rights reserved.
For info, please visit https://www.isc.org/software/dhcp/
Can't open /etc/dhcp3/dhcpd.conf: Permission denied
root@mafia:~#

```If I want to restart dhcp I got error in stoping and starting the server
```

root@mafia:~# /etc/init.d/isc-dhcp-server.dpkg-new restart  
* Stopping ISC DHCP server dhcpd                                        [fail] 
 * Starting ISC DHCP server dhcpd                                                
* check syslog for diagnostics.
                                                                         [fail]
root@mafia:~# 

```

And my syslog will print this
```

Feb 22 17:51:59 mafia dhcpd: Wrote 0 leases to leases file.
Feb 22 17:51:59 mafia dhcpd: 
Feb 22 17:51:59 mafia dhcpd: No subnet declaration for wlan0 (no IPv4 addresses).
Feb 22 17:51:59 mafia dhcpd: ** Ignoring requests on wlan0.  If this is not what
Feb 22 17:51:59 mafia dhcpd:    you want, please write a subnet declaration
Feb 22 17:51:59 mafia dhcpd:    in your dhcpd.conf file for the network segment
Feb 22 17:51:59 mafia dhcpd:    to which interface wlan0 is attached. **
Feb 22 17:51:59 mafia dhcpd: 
Feb 22 17:51:59 mafia dhcpd: 
Feb 22 17:51:59 mafia dhcpd: Not configured to listen on any interfaces!

```
I'm out of ideas, can some1 point me out why my dhcp server dosent start working :/.

---

### Post by roelforg on 2012-02-22
I've got a dhcp server  myself; let me help you.

Try:
```

sudo chown root:root /etc/dhcp/*
sudo chmod 655 /etc/dhcp/dhcpd.conf
service isc-dhcp-server restart

```

---

### Post by mafi127 on 2012-02-24
Thank you for your help :).

did all what you said, but still got this problem.

[PHP]root@mafia:~# dhcpd -cf /etc/dhcp3/dhcpd.conf -pf /var/run/dhcp3-server/dhcpd.pid at0
Internet Systems Consortium DHCP Server 4.1.1-P1
Copyright 2004-2010 Internet Systems Consortium.
All rights reserved.
For info, please visit https://www.isc.org/software/dhcp/
Can't open /etc/dhcp3/dhcpd.conf: Permission denied
root@mafia:~# 
[/PHP]

And another problem is, I dont have service called isc-dhcp-server ( but when using service isc-<tab> then it will autocomplete. but says.

[PHP]root@mafia:~# service isc-dhcp-server restart
isc-dhcp-server: unrecognized service
root@mafia:~# service isc-dhcp-server
isc-dhcp-server: unrecognized service
root@mafia:~# /etc/init.d/isc-dhcp-server.dpkg-new restart
 * Stopping ISC DHCP server dhcpd                                        [fail] 
 * Starting ISC DHCP server dhcpd                                                * check syslog for diagnostics.
                                                                         [fail]
root@mafia:~# tail /var/log/syslog
Feb 24 11:51:22 mafia dhcpd: Wrote 0 leases to leases file.
Feb 24 11:51:22 mafia dhcpd: 
Feb 24 11:51:22 mafia dhcpd: No subnet declaration for eth1 (no IPv4 addresses).
Feb 24 11:51:22 mafia dhcpd: ** Ignoring requests on eth1.  If this is not what
Feb 24 11:51:22 mafia dhcpd:    you want, please write a subnet declaration
Feb 24 11:51:22 mafia dhcpd:    in your dhcpd.conf file for the network segment
Feb 24 11:51:22 mafia dhcpd:    to which interface eth1 is attached. **
Feb 24 11:51:22 mafia dhcpd: 
Feb 24 11:51:22 mafia dhcpd: 
Feb 24 11:51:22 mafia dhcpd: Not configured to listen on any interfaces![/PHP]

Tryed allso

[PHP]root@mafia:~# /etc/init.d/isc-dhcp-server.dpkg-new restart
 * Stopping ISC DHCP server dhcpd                                        [fail] 
 * Starting ISC DHCP server dhcpd                                               
 * check syslog for diagnostics.
                                                                         [fail]
[/PHP]

---

### Post by raja.genupula on 2012-02-24
> check syslog for diagnostics.
may be that log gonna help us .it will be in /var/log

---

### Post by dcstar on 2012-02-24
> **mafi127 said:**
> Hello everyone,

I have been tryed to get dhcp3 server running in ubuntu 11.10 32bit two weeks now, but no success. I am relatively new to setting up Ubuntu Servers.


What I have done so far is:

```

apt-get install dhcp3-server
**mv /etc/dhcp3/dhcpd.conf /etc/dhcp3/dhcpd.conf.backup**
gedit /etc/dhcp3/dhcpd.conf

```
..........
I'm out of ideas, can some1 point me out why my dhcp server dosent start working :/.

**You** move the config file with the correct permissions, then create a brand new file with your dodgy root account (**you** should be using sudo) and wonder why the app has later permissions problems?

---

