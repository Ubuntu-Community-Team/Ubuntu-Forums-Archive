---
title: "Where is inetd config. file?"
date: 2010-09-04
forum: General Help
---

### Post by bilkay on 2010-09-04
Several man pages refer to the inetd configuration file supposedly located at /etc/inetd.conf. There is no file by that name anywhere on my 10.04 system. Anyone know where it is?

---

### Post by AlphaLexman on 2010-09-04
Well here is a copy of mine:
```
#<off># sane-port    stream    tcp    nowait    saned:saned    /usr/sbin/saned saned
#<off># netbios-ssn    stream    tcp    nowait    root    /usr/sbin/tcpd    /usr/sbin/smbd

```
Which I've never edited, so it should be a default.

---

