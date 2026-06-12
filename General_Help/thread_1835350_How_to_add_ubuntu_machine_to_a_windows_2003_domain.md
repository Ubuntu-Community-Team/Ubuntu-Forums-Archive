---
title: "How to add ubuntu machine to a windows 2003 domain?"
date: 2011-08-29
forum: General Help
---

### Post by karthick87 on 2011-08-29
I just want to add my ubuntu machine to windows 2003 domain. I tried adding it to domain, but i am getting the following error. Have a look @ the snapshot below.

Details:

Running : ubuntu 10.10

Output of NSSWITCH:

```
# /etc/nsswitch.conf
#
# Example configuration of GNU Name Service Switch functionality.
# If you have the `glibc-doc-reference' and `info' packages installed, try:
# `info libc "Name Service Switch"' for information about this file.

passwd:         compat
group:          compat
shadow:         compat

hosts:          files mdns4_minimal [NOTFOUND=return] dns mdns4
networks:       files

protocols:      db files
services:       db files
ethers:         db files
rpc:            db files

netgroup:       nis
```

---

### Post by scorp123 on 2011-08-29
> **karthick87 said:**
> I just want to add my ubuntu machine to windows 2003 domain.  You're doing it wrong. "nsswitch.conf" has nothing to do with how Windows 2003 AD authentication works.

Long story short: The packages you need are:
[LIST]
[*]likewise-open5
[*]likewise-open5-gui
[/LIST]

Here's a tutorial -- it's a bit dated but should still be valid:
[https://help.ubuntu.com/community/LikewiseOpen](https://help.ubuntu.com/community/LikewiseOpen)

---

### Post by karthick87 on 2011-08-29
I have tried that already. Still i get the same error..

---

### Post by scorp123 on 2011-08-30
> **karthick87 said:**
> I have tried that already. Still i get the same error..

And you're sure your **/etc/resolv.conf** is correct, DNS names are set correctly, the DNS server is working correctly? What happens when you test with **nslookup**?

```
nslookup your-ip-address
nslookup your-host-name
```

Are the values that get returned correct?

---

### Post by karthick87 on 2011-08-30
```
karthick@karthick:~$ nslookup 172.29.32.9
Server:        172.29.32.XX
Address:    172.29.32.XX#53

9.32.29.172.in-addr.arpa    name = vnc-access.xxx.xx.com.
```

```
karthick@karthick:~$ nslookup karthick
;; Got SERVFAIL reply from 172.29.32.XX, trying next server
Server:        172.29.39.XXX
Address:    172.29.39.XXX#53

** server can't find karthick: NXDOMAIN

```

---

### Post by scorp123 on 2011-09-01
```
karthick@karthick:~$ nslookup karthick
;; Got SERVFAIL reply from 172.29.32.XX, trying next server
Server:        172.29.39.XXX
Address:    172.29.39.XXX#53

** server can't find karthick: NXDOMAIN

```And if you use your FQDN? Looks to me like your DNS setup (/etc/resolv.conf) isn't correct.

---

### Post by karthick87 on 2011-09-01
Could you pls explain me in detail?

---

### Post by karthick87 on 2011-09-03
I am able to ping the DNS Address. The DNS address were working fine.. Any other way to debug the problem?

---

