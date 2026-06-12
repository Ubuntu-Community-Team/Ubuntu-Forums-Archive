---
title: "cups wont start and no error log"
date: 2010-08-26
forum: General Help
---

### Post by gordontytler on 2010-08-26
Ubuntu 10.04 I can't print to a locally connected printer via a USB cable. I use lsusb to check the connection...

```
$ lsusb
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 003: ID 03f0:1204 Hewlett-Packard DeskJet 930c
```When I try to start the cups service it does not start and produces no log output.

```
$ sudo /etc/init.d/cups start
 * Starting Common Unix Printing System: cupsd           [ OK ] 
$ sudo /etc/init.d/cups status
Status of Common Unix Printing System: cupsd is not running.
$ ls /var/log/cups -l
total 0 
```The same printer when connected to another PC running the same version of Ubuntu works when the printer port is used. Unfortunately, the netbook I want to use does not have a printer port. 

How can I get cups to start or write to its log ?

---

