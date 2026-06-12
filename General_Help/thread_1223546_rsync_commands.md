---
title: "rsync commands"
date: 2009-07-26
forum: General Help
---

### Post by krisrae675 on 2009-07-26
Hi using rsync within our bluetooth software to control and update a network. We have 14 client servers all building data and sending bluetooth messages and all connected to an enterprise master server on an internal network.
The client servers each have there own IP and need to send obex data reports to the enterprise which also has its own IP. The enterprise then sends data back to the clients like content updates and configuration settings.
Our software currently has the following configuration:

OBEX UPDATE (page)
Data Source  rsync://192.168.1.60/ccobex-data/
Sync Options -f :_.rsync-filter --delete-after

RSYNC- FILTER
- /download/**/.lock*
- /download/**/.log*
+ /download
+ /download/**
+ /selfile
+ /selfile/**
+ .rsync-filter
: .rsync-filter
- *

RSYNC CONFIG
uid =nobody
gid =nobody
use chroot =yes
read only =yes
max verbosity =1
timeout =600
transfer logging =yes

[ccobex-data]
path = /var/opt/ccobex
comment = ccobex data files
filter = . /var/opt/ccobex/ .rsync-filter

The data in the ccobex folder contains 
selfile,download,obexfilel.log,obexscan.log
At present only the download and selfile is changed but the obexfile.log and obexscan.log does not change.
Can anyone offer any advice as we have been on this an eternity trying to solve.

---

