---
title: "bind9 dlz not working"
date: 2012-07-11
forum: General Help
---

### Post by RaythXC on 2012-07-11
I am running ubuntu10.10 because it is the newest version my vps provider has. I am trying to setup BIND with DLZ using the tutorial:
[http://ubuntuforums.org/showthread.php?t=1867237](http://ubuntuforums.org/showthread.php?t=1867237)

I get as far as starting bind for the first time (after editing named.conf) and it fails to start. When I type "named -g -d 9" it gives me the following:

> 
11-Jul-2012 20:57:56.474 starting BIND 9.7.1-P2 -g -d 9
11-Jul-2012 20:57:56.474 built with '--prefix=/usr' '--sysconfdir=/etc/bind' '--localstatedir=/var' '--mandir=/usr/share/man' '--infodir=/usr/share/info' '--enable-threads' '--enable-largefile' '--with-libtool' '--enable-shared' '--enable-static' '--with-openssl=/usr' '--with-gssapi=/usr' '--with-gnu-ld' '--with-dlz-postgres=yes' '--with-dlz-mysql=yes' '--with-dlz-bdb=no' '--with-dlz-filesystem=yes' '--with-dlz-ldap=yes' '--with-dlz-stub=yes' '--with-geoip=/usr' '--enable-ipv6'
11-Jul-2012 20:57:56.474 adjusted limit on open files from 1024 to 1048576
11-Jul-2012 20:57:56.474 found 1 CPU, using 1 worker thread
11-Jul-2012 20:57:56.474 using up to 4096 sockets
11-Jul-2012 20:57:56.474 Registering DLZ_stub driver.
11-Jul-2012 20:57:56.474 Registering SDLZ driver 'dlz_stub'
11-Jul-2012 20:57:56.474 Registering DLZ driver 'dlz_stub'
11-Jul-2012 20:57:56.474 Registering DLZ postgres driver.
11-Jul-2012 20:57:56.474 Registering SDLZ driver 'postgres'
11-Jul-2012 20:57:56.474 Registering DLZ driver 'postgres'
11-Jul-2012 20:57:56.474 Registering DLZ mysql driver.
11-Jul-2012 20:57:56.474 Registering SDLZ driver 'mysql'
11-Jul-2012 20:57:56.474 Registering DLZ driver 'mysql'
11-Jul-2012 20:57:56.474 Registering DLZ filesystem driver.
11-Jul-2012 20:57:56.474 Registering SDLZ driver 'filesystem'
11-Jul-2012 20:57:56.475 Registering DLZ driver 'filesystem'
11-Jul-2012 20:57:56.475 Registering DLZ ldap driver.
11-Jul-2012 20:57:56.475 Registering SDLZ driver 'ldap'
11-Jul-2012 20:57:56.475 Registering DLZ driver 'ldap'
11-Jul-2012 20:57:56.480 loading configuration from '/etc/bind/named.conf'
11-Jul-2012 20:57:56.480 reading built-in trusted keys from file '/etc/bind/bind.keys'
11-Jul-2012 20:57:56.480 set maximum stack size to 18446744073709551615: success
11-Jul-2012 20:57:56.480 set maximum data size to 18446744073709551615: success
11-Jul-2012 20:57:56.480 set maximum core size to 18446744073709551615: success
11-Jul-2012 20:57:56.480 set maximum open files to 18446744073709551615: success
11-Jul-2012 20:57:56.481 using default UDP/IPv4 port range: [1024, 65535]
11-Jul-2012 20:57:56.481 using default UDP/IPv6 port range: [1024, 65535]
11-Jul-2012 20:57:56.482 listening on IPv6 interfaces, port 53
11-Jul-2012 20:57:56.482 clientmgr @0xb693a1e0: create
11-Jul-2012 20:57:56.483 clientmgr @0xb693a1e0: createclients
11-Jul-2012 20:57:56.483 clientmgr @0xb693a1e0: create new
11-Jul-2012 20:57:56.484 client @0xb50e8008: create
11-Jul-2012 20:57:56.484 clientmgr @0xb693a1e0: createclients
11-Jul-2012 20:57:56.484 clientmgr @0xb693a1e0: create new
11-Jul-2012 20:57:56.484 client @0xb50a7008: create
11-Jul-2012 20:57:56.484 listening on IPv4 interface lo, 127.0.0.1#53
11-Jul-2012 20:57:56.484 clientmgr @0xb693a3b8: create
11-Jul-2012 20:57:56.484 clientmgr @0xb693a3b8: createclients
11-Jul-2012 20:57:56.484 clientmgr @0xb693a3b8: create new
11-Jul-2012 20:57:56.485 client @0xb5066008: create
11-Jul-2012 20:57:56.485 clientmgr @0xb693a3b8: createclients
11-Jul-2012 20:57:56.485 clientmgr @0xb693a3b8: create new
11-Jul-2012 20:57:56.485 client @0xb5025008: create
11-Jul-2012 20:57:56.485 listening on IPv4 interface eth0, 208.117.34.245#53
11-Jul-2012 20:57:56.485 clientmgr @0xb693a590: create
11-Jul-2012 20:57:56.485 clientmgr @0xb693a590: createclients
11-Jul-2012 20:57:56.485 clientmgr @0xb693a590: create new
11-Jul-2012 20:57:56.485 client @0xb4fe4008: create
11-Jul-2012 20:57:56.486 clientmgr @0xb693a590: createclients
11-Jul-2012 20:57:56.486 clientmgr @0xb693a590: create new
11-Jul-2012 20:57:56.486 client @0xb4fa3008: create
11-Jul-2012 20:57:56.486 listening on IPv4 interface eth0:0, 208.117.34.244#53
11-Jul-2012 20:57:56.486 clientmgr @0xb693a768: create
11-Jul-2012 20:57:56.486 clientmgr @0xb693a768: createclients
11-Jul-2012 20:57:56.486 clientmgr @0xb693a768: create new
11-Jul-2012 20:57:56.486 client @0xb4f62008: create
11-Jul-2012 20:57:56.486 clientmgr @0xb693a768: createclients
11-Jul-2012 20:57:56.486 clientmgr @0xb693a768: create new
11-Jul-2012 20:57:56.487 client @0xb4f21008: create
11-Jul-2012 20:57:56.487 listening on IPv4 interface eth0:1, 208.117.34.243#53
11-Jul-2012 20:57:56.487 clientmgr @0xb693a940: create
11-Jul-2012 20:57:56.487 clientmgr @0xb693a940: createclients
11-Jul-2012 20:57:56.487 clientmgr @0xb693a940: create new
11-Jul-2012 20:57:56.487 client @0xb4ee0008: create
11-Jul-2012 20:57:56.487 clientmgr @0xb693a940: createclients
11-Jul-2012 20:57:56.487 clientmgr @0xb693a940: create new
11-Jul-2012 20:57:56.488 client @0xb4e9f008: create
11-Jul-2012 20:57:56.488 listening on IPv4 interface eth0:2, 208.117.34.242#53
11-Jul-2012 20:57:56.488 clientmgr @0xb693ab18: create
11-Jul-2012 20:57:56.488 clientmgr @0xb693ab18: createclients
11-Jul-2012 20:57:56.488 clientmgr @0xb693ab18: create new
11-Jul-2012 20:57:56.488 client @0xb4e5e008: create
11-Jul-2012 20:57:56.488 clientmgr @0xb693ab18: createclients
11-Jul-2012 20:57:56.488 clientmgr @0xb693ab18: create new
11-Jul-2012 20:57:56.488 client @0xb4e1d008: create
11-Jul-2012 20:57:56.488 listening on IPv4 interface eth0:3, 208.117.34.241#53
11-Jul-2012 20:57:56.488 clientmgr @0xb693acf0: create
11-Jul-2012 20:57:56.488 clientmgr @0xb693acf0: createclients
11-Jul-2012 20:57:56.488 clientmgr @0xb693acf0: create new
11-Jul-2012 20:57:56.489 client @0xb4ddc008: create
11-Jul-2012 20:57:56.489 clientmgr @0xb693acf0: createclients
11-Jul-2012 20:57:56.489 clientmgr @0xb693acf0: create new
11-Jul-2012 20:57:56.489 client @0xb4d9b008: create
11-Jul-2012 20:57:56.489 listening on IPv4 interface eth0:4, 208.117.34.240#53
11-Jul-2012 20:57:56.489 clientmgr @0xb6964008: create
11-Jul-2012 20:57:56.489 clientmgr @0xb6964008: createclients
11-Jul-2012 20:57:56.489 clientmgr @0xb6964008: create new
11-Jul-2012 20:57:56.489 client @0xb4d5a008: create
11-Jul-2012 20:57:56.489 clientmgr @0xb6964008: createclients
11-Jul-2012 20:57:56.489 clientmgr @0xb6964008: create new
11-Jul-2012 20:57:56.489 client @0xb4d19008: create
11-Jul-2012 20:57:56.490 listening on IPv4 interface eth0:5, 208.117.34.105#53
11-Jul-2012 20:57:56.490 clientmgr @0xb69641e0: create
11-Jul-2012 20:57:56.490 clientmgr @0xb69641e0: createclients
11-Jul-2012 20:57:56.490 clientmgr @0xb69641e0: create new
11-Jul-2012 20:57:56.490 client @0xb4cd8008: create
11-Jul-2012 20:57:56.490 clientmgr @0xb69641e0: createclients
11-Jul-2012 20:57:56.490 clientmgr @0xb69641e0: create new
11-Jul-2012 20:57:56.490 client @0xb4c97008: create
11-Jul-2012 20:57:56.491 generating session key for dynamic DNS
11-Jul-2012 20:57:56.492 Loading 'Mysql zone' using driver mysql
11-Jul-2012 20:57:56.492 Loading SDLZ driver.
11-Jul-2012 20:57:56.495 mysql driver failed to create database connection after 4 attempts
11-Jul-2012 20:57:56.495 SDLZ driver failed to load.
11-Jul-2012 20:57:56.495 DLZ driver failed to load.
11-Jul-2012 20:57:56.495 load_configuration: failure
11-Jul-2012 20:57:56.495 loading configuration: failure
11-Jul-2012 20:57:56.495 exiting (due to fatal error)


I have checked the named.conf file and it is identical to the one in the tutorial, except it uses my username and password for the database. These are correct and I used them successfully on phpmyadmin just 2 minutes before when making the database. Everything else was done EXACTLY so I don't get why this won't work.

---

### Post by RaythXC on 2012-07-11
anyone? i'm kinda desperate on this as i need dlz or something similar to do something with a friend we've been planning for a while.

---

### Post by RaythXC on 2012-07-12
hello?

---

### Post by RaythXC on 2012-07-12
bump

---

### Post by jferrer on 2012-08-06
Hi,
 
Have you got an answer?
I have the same problem.
 
KR,
 
JR

---

### Post by jferrer on 2012-08-06
Here's the way I solved it
 
[COLOR=red][B]view "dbct" {
        match-clients { any; };};[/B][/COLOR]
dlz "Mysql zone" {
   database "mysql
   {host=127.0.0.1 port=3306 dbname=bind9_dlz user=xxx password=xxxxx}
   {SELECT zone FROM dns_records WHERE zone = '$zone$'}
   {SELECT ttl, type, mx_priority, IF(type = 'TXT', CONCAT('\"',data,'\"'), data) AS data
    FROM dns_records
    WHERE zone = '$zone$' AND host = '$record$' AND type <> 'SOA' AND type <> 'NS'}
   {SELECT ttl, type, data, primary_ns, resp_person, serial, refresh, retry, expire, minimum
    FROM dns_records
    WHERE zone = '$zone$' AND (type = 'SOA' OR type='NS')}
   {SELECT ttl, type, host, mx_priority, IF(type = 'TXT', CONCAT('\"',data,'\"'), data) AS data, resp_person, serial, refresh, retry, expire, minimum
    FROM dns_records
    WHERE zone = '$zone$' AND type <> 'SOA' AND type <> 'NS'}
   {SELECT zone FROM xfr_table where zone='$zone$' AND client = '$client$'}";
};

---

