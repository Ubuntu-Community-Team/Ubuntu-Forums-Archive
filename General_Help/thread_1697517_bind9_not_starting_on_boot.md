---
title: "bind9 not starting on boot"
date: 2011-02-28
forum: General Help
---

### Post by hawkmage on 2011-02-28
When a Ubuntu 10.10 I have starts up apache2, MySQL and postfix start properly but bind9 doesn't.  Once booted is I run 'sudo /etc/init.d/bind9 start' it starts.

The only thing odd on this system is I have a "inet6 v4tunnel" interface defined in my /etc/network/interfaces.

From booting in the syslog there is:
```
/var/log/syslog:Feb 28 19:02:42 vaio named[1029]: starting BIND 9.7.1-P2 -u bind -d 9
/var/log/syslog:Feb 28 19:02:42 vaio named[1029]: built with '--prefix=/usr' '--mandir=/usr/share/man' '--infodir=/usr/share/info' '--sysconfdir=/etc/bind' '--localstatedir=/var' '--enable-threads' '--enable-largefile' '--with-libtool' '--enable-shared' '--enable-static' '--with-openssl=/usr' '--with-gssapi=/usr' '--with-gnu-ld' '--with-dlz-postgres=no' '--with-dlz-mysql=no' '--with-dlz-bdb=yes' '--with-dlz-filesystem=yes' '--with-dlz-ldap=yes' '--with-dlz-stub=yes' '--with-geoip=/usr' '--enable-ipv6' 'CFLAGS=-fno-strict-aliasing -DDIG_SIGCHASE -O2' 'LDFLAGS=-Wl,-Bsymbolic-functions' 'CPPFLAGS='
/var/log/syslog:Feb 28 19:02:42 vaio named[1029]: adjusted limit on open files from 1024 to 1048576
/var/log/syslog:Feb 28 19:02:42 vaio named[1029]: found 2 CPUs, using 2 worker threads
/var/log/syslog:Feb 28 19:02:42 vaio named[1029]: using up to 4096 sockets
```Where as running 'sudo /etc/init.d/bind9 start' once booted I get:
```
/var/log/syslog:Feb 28 19:14:51 vaio named[2792]: starting BIND 9.7.1-P2 -u bind -d 9
/var/log/syslog:Feb 28 19:14:51 vaio named[2792]: built with '--prefix=/usr' '--mandir=/usr/share/man' '--infodir=/usr/share/info' '--sysconfdir=/etc/bind' '--localstatedir=/var' '--enable-threads' '--enable-largefile' '--with-libtool' '--enable-shared' '--enable-static' '--with-openssl=/usr' '--with-gssapi=/usr' '--with-gnu-ld' '--with-dlz-postgres=no' '--with-dlz-mysql=no' '--with-dlz-bdb=yes' '--with-dlz-filesystem=yes' '--with-dlz-ldap=yes' '--with-dlz-stub=yes' '--with-geoip=/usr' '--enable-ipv6' 'CFLAGS=-fno-strict-aliasing -DDIG_SIGCHASE -O2' 'LDFLAGS=-Wl,-Bsymbolic-functions' 'CPPFLAGS='
/var/log/syslog:Feb 28 19:14:51 vaio named[2792]: adjusted limit on open files from 1024 to 1048576
/var/log/syslog:Feb 28 19:14:51 vaio named[2792]: found 2 CPUs, using 2 worker threads
/var/log/syslog:Feb 28 19:14:51 vaio named[2792]: using up to 4096 sockets
/var/log/syslog:Feb 28 19:14:51 vaio named[2792]: loading configuration from '/etc/bind/named.conf'
/var/log/syslog:Feb 28 19:14:51 vaio named[2792]: reading built-in trusted keys from file '/etc/bind/bind.keys'
/var/log/syslog:Feb 28 19:14:51 vaio named[2792]: using default UDP/IPv4 port range: [1024, 65535]
/var/log/syslog:Feb 28 19:14:51 vaio named[2792]: using default UDP/IPv6 port range: [1024, 65535]
/var/log/syslog:Feb 28 19:14:51 vaio named[2792]: listening on IPv6 interfaces, port 53
/var/log/syslog:Feb 28 19:14:51 vaio named[2792]: listening on IPv4 interface lo, 127.0.0.1#53
/var/log/syslog:Feb 28 19:14:51 vaio named[2792]: listening on IPv4 interface eth0, XXX.XXX.XXX.XXX#53
/var/log/syslog:Feb 28 19:14:51 vaio named[2792]: generating session key for dynamic DNS
/var/log/syslog:Feb 28 19:14:51 vaio named[2792]: set up managed keys zone for view _default, file 'managed-keys.bind'
/var/log/syslog:Feb 28 19:14:51 vaio named[2792]: automatic empty zone: 254.169.IN-ADDR.ARPA
/var/log/syslog:Feb 28 19:14:51 vaio named[2792]: automatic empty zone: 2.0.192.IN-ADDR.ARPA
/var/log/syslog:Feb 28 19:14:51 vaio named[2792]: automatic empty zone: XXX.XXX.XXX.IN-ADDR.ARPA
/var/log/syslog:Feb 28 19:14:51 vaio named[2792]: automatic empty zone: 113.0.203.IN-ADDR.ARPA
/var/log/syslog:Feb 28 19:14:51 vaio named[2792]: automatic empty zone: 255.255.255.255.IN-ADDR.ARPA
/var/log/syslog:Feb 28 19:14:51 vaio named[2792]: automatic empty zone: X.X.X.X.X.X.X.X.X.X.X.X.X.X.X.X.X.X.X.X.X.X.X.X.X.X.X.X.X.X.X.X.IP6.ARPA
/var/log/syslog:Feb 28 19:14:51 vaio named[2792]: automatic empty zone: X.X.X.X.X.X.X.X.X.X.X.X.X.X.X.X.X.X.X.X.X.X.X.X.X.X.X.X.X.X.X.X.IP6.ARPA
/var/log/syslog:Feb 28 19:14:51 vaio named[2792]: automatic empty zone: D.F.IP6.ARPA
/var/log/syslog:Feb 28 19:14:51 vaio named[2792]: automatic empty zone: 8.E.F.IP6.ARPA
/var/log/syslog:Feb 28 19:14:51 vaio named[2792]: automatic empty zone: 9.E.F.IP6.ARPA
/var/log/syslog:Feb 28 19:14:51 vaio named[2792]: automatic empty zone: A.E.F.IP6.ARPA
/var/log/syslog:Feb 28 19:14:51 vaio named[2792]: automatic empty zone: B.E.F.IP6.ARPA
/var/log/syslog:Feb 28 19:14:51 vaio named[2792]: automatic empty zone: 8.B.D.0.1.0.0.2.IP6.ARPA
/var/log/syslog:Feb 28 19:14:51 vaio named[2792]: automatic empty zone: 0.1.1.0.0.2.IP6.ARPA
/var/log/syslog:Feb 28 19:14:51 vaio named[2792]: command channel listening on 127.0.0.1#953
/var/log/syslog:Feb 28 19:14:51 vaio named[2792]: zone 0.in-addr.arpa/IN: loaded serial 1
/var/log/syslog:Feb 28 19:14:51 vaio named[2792]: zone 127.in-addr.arpa/IN: loaded serial 1
/var/log/syslog:Feb 28 19:14:51 vaio named[2792]: zone XXX.XXX.XXX.in-addr.arpa/IN: loaded serial 110113000
/var/log/syslog:Feb 28 19:14:51 vaio named[2792]: zone XXX.XXX.XXX.in-addr.arpa/IN: loaded serial 109030502
/var/log/syslog:Feb 28 19:14:51 vaio named[2792]: zone 255.in-addr.arpa/IN: loaded serial 1
/var/log/syslog:Feb 28 19:14:51 vaio named[2792]: zone X.X.X.X.X.X.X.X.X.X.X.X.X.X.X.X.ip6.arpa/IN: loaded serial 110128000
/var/log/syslog:Feb 28 19:14:51 vaio named[2792]: zone mydomain.com.com/IN: loaded serial 110127002
/var/log/syslog:Feb 28 19:14:51 vaio named[2792]: zone localhost/IN: loaded serial 1
/var/log/syslog:Feb 28 19:14:51 vaio named[2792]: zone myotherdomain.com/IN: loaded serial 110127002
/var/log/syslog:Feb 28 19:14:51 vaio named[2792]: managed-keys-zone ./IN: loading from master file managed-keys.bind failed: file not found
/var/log/syslog:Feb 28 19:14:51 vaio named[2792]: managed-keys-zone ./IN: loaded serial 0
/var/log/syslog:Feb 28 19:14:51 vaio named[2792]: zone X.X.X.X.X.X.X.X.X.X.X.X.X.X.X.X.ip6.arpa/IN: sending notifies (serial 110128000)
/var/log/syslog:Feb 28 19:14:51 vaio named[2792]: zone XXX.XXX.XXX.in-addr.arpa/IN: sending notifies (serial 110113000)
/var/log/syslog:Feb 28 19:14:51 vaio named[2792]: zone mydomain.com/IN: sending notifies (serial 110127002)
/var/log/syslog:Feb 28 19:14:51 vaio named[2792]: zone myotherdomain.com/IN: sending notifies (serial 110127002)
/var/log/syslog:Feb 28 19:14:51 vaio named[2792]: running
```

---

### Post by hawkmage on 2011-03-01
Even with the bind debug level at set at 90 I do not get any more in the logs that what I posted before.  The lack of errors in the logs is giving me no idea where to start.

I commented out the IPv6 tunnel interface and rebooted and still no help.  bind still is not starting at boot.

---

### Post by hawkmage on 2011-03-01
OK, it is not a permissions issue, I have changed the config and zone files to be owned by bind:bind, root:bind, root:root and bind:root and it has made no difference.

---

