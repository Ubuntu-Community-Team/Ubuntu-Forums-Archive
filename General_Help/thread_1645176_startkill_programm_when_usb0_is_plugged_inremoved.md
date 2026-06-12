---
title: "start/kill programm when usb0 is plugged in/removed"
date: 2010-12-14
forum: General Help
---

### Post by dirtyheizer on 2010-12-14
hey,

i have an usb device Amtel Raven and Ubuntu 10.10 running in an Virtual box.

**What i want:**

a script what does the following :

1) If usb0(Bus 002 Device 003: ID 03eb:2021 Atmel Corp.) connected, do

a) sysctl -w net.ipv6.conf.all.forwarding=1
b) ip -6 address add aaaa::1/64 dev usb0
c) /etc/init.d/radvd restart
d) export PATH=$PATH:/usr/local/avr/bin

2) if usb0(Bus 002 Device 003: ID 03eb:2021 Atmel Corp.) disconnected, do

a) kill/close process radvd "etc/init.d/radvd"

THe script sould run alltime in an while(1) if possible...
so that it reacts on plugging in/out the usb device..

Kind regards for tips,

thx
dirtyheizer

---

