---
title: "Need help on OpenNTPD"
date: 2010-04-27
forum: General Help
---

### Post by sqa on 2010-04-27
Hi all,

I just tried this time synch using OpenNTPD on Windows XP  VMware
on ubuntu-9.10-server-amd64 after i install it clean from scratch then i reboot the server and i received this error message that it supposed not to appear according to guidelines from openbsd, error message are :

[I](this the only one openntpd process that is correct which is at startup)
step time server 192.168.xxx.xxx offset -0.353350 sec
listening on 127.0.0.1
listening on 10.1.1.14
listening on ::1
listening on fe80::250:56ff:feb8:41ef%eth0
                             (beyond this is the unwanted messages)
init: apport pre-start process terminated with status 1
init: apport post-start process terminated with status 1
fatal: bind: Cannot assign requested address
dispatch_imsg in main: pipe closed
                             (but then.......)
ntp engine ready[/I]

now the problem is even it is said that ntp engine is ready but it wont sync or looking for peers that is valid or invalid so its just not working, 

i check my firewall and already open port 123 outgoing ingoing to ntp server to main time server ,because i can manually configure using ntpdate, yet openntpd didnt seems to work properly,

i didnt install any other thing because it didnt say to install any other than openntpd package.

did i make mistakes?? xD kinda depressing tho but kinda curious about it why 

oo the the config is /etc/openntpd/ntpd.conf

listen on *
server time.xxx.xxx (i can ntpdate to this server properly and change my server time accordingly but openntpd simply wont sync status)

cheers,
alv

---

