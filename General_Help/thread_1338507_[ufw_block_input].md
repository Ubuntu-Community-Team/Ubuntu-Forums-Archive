---
title: "[ufw block input]"
date: 2009-11-26
forum: General Help
---

### Post by utnubuuser on 2009-11-26
I'm getting a ton of these entries in my syslog - approx. every 30 seconds  - > Nov 26 09:56:47 brad-laptop kernel: [  295.265004] [UFW BLOCK INPUT]: IN=eth0 OUT= MAC= SRC=xxx.xxx.x.xx DST=xxx.xxx.x.xxx LEN=199 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=631 DPT=631 LEN=179
Nov 26 09:57:31 brad-laptop kernel: [  295.265004] [UFW BLOCK INPUT]: IN=eth0 OUT= MAC= SRC=xxx.xxx.x.xx DST=xxx.xxx.x.xxx LEN=199 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=631 DPT=631 LEN=179
Nov 26 09:57:59 brad-laptop kernel: [  295.265004] [UFW BLOCK INPUT]: IN=eth0 OUT= MAC= SRC=xxx.xxx.x.xx DST=xxx.xxx.x.xxx LEN=199 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=631 DPT=631 LEN=179
Nov 26 09:58:29 brad-laptop kernel: [  295.265004] [UFW BLOCK INPUT]: IN=eth0 OUT= MAC= SRC=xxx.xxx.x.xx DST=xxx.xxx.x.xxx LEN=199 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=631 DPT=631 LEN=179


Anybody know what they would be by any chance?  Is this the router querrying my machine or vice-versa?

I've changed the actual mac addresses to xxx.xxx.x.xx etc

the DST address is either the router's mailfuction, or my ISP's mail function - from network-tools lookup function I get: DSTxxx.xxx.x.xxx = prisoner.iana.hostmaster.root-servers.org or our ISP postmaster.net....
while the SRC is our homeportal.gateway.2wire.net router or my laptop.

---

