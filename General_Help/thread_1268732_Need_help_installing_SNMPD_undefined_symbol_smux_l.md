---
title: "Need help installing SNMPD undefined symbol: smux_listen_sd"
date: 2009-09-17
forum: General Help
---

### Post by john_d13 on 2009-09-17
I posted this a while ago but I would like to touch base again as I still havent figured it out.

I use my ubuntu box for cacti,  i installed apt-get install snmp.  snmpwalk works but when I try install snmpd i get this error. 

Setting up snmpd (5.4.1~dfsg-12ubuntu3) ...
 * Starting network management services:                                                                                 /usr/sbin/snmpd: symbol lookup error: /usr/sbin/snmpd: undefined symbol: smux_listen_sd
invoke-rc.d: initscript snmpd, action "start" failed.
dpkg: error processing snmpd (--configure):
 subprocess post-installation script returned error exit status 127
Errors were encountered while processing:
 snmpd
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

### Post by caussourd on 2012-06-05
Hi!

I had a similar error. 

Check that you don't have libnetsnmp* libraries in both /usr/local/lib and /usr/lib

And get rid of the oldest one (mine was in /usr/local/lib). It should be better :-)

Celine

---

### Post by Iowan on 2012-06-05
Closed - 2.5 years old.

---

