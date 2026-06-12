---
title: "my ubuntu always shuts it down by itself"
date: 2010-01-20
forum: General Help
---

### Post by jfernandez1977 on 2010-01-20
Hi,

I've installed VMware server 2.x on my windows XP SP2 and installed Ubuntu 9.10 on the VMWare.  I have noticed several times that the ubuntu machines shuts it down (not sure the time pattern but it could be that it shuts down after a certain minutes idle).  As a result of that, I always have to restart it.

I checked the event log viewer, it looks like there's always a segfault just before it shuts down.  I've pasted the last few lines of event log below.  Can someone with more experience tell me how to fix the problem?  Thanks.


JF



Jan 19 10:28:16 jfernandez-ubuntu kernel: [   32.648005] mtrr: base(0xf0000000) is not aligned on a size(0x15a0000) boundary
Jan 19 10:28:21 jfernandez-ubuntu kernel: [   37.748105] type=1503 audit(1263914901.917:28): operation="open" pid=1229 parent=1228 profile="/usr/sbin/mysqld" requested_mask="r::" denied_mask="r::" fsuid=0 ouid=0 name="/sys/devices/system/cpu/"
Jan 19 10:28:22 jfernandez-ubuntu kernel: [   37.870316] type=1503 audit(1263914902.047:29): operation="open" pid=1240 parent=1239 profile="/usr/sbin/mysqld" requested_mask="r::" denied_mask="r::" fsuid=0 ouid=0 name="/sys/devices/system/cpu/"
Jan 19 10:28:26 jfernandez-ubuntu kernel: [   42.000373] e1000: eth0: e1000_set_tso: TSO is Enabled
Jan 19 10:41:10 jfernandez-ubuntu rsyslogd: [origin software="rsyslogd" swVersion="4.2.0" x-pid="642" x-info="http://www.rsyslog.com"] rsyslogd was HUPed, type 'lightweight'.
Jan 19 18:03:51 jfernandez-ubuntu kernel: [27366.708415] gnome-panel[1883]: segfault at 7f8c0fded360 ip 00007f8c0e394ef0 sp 00007fffd0c89830 error 4 in libc-2.10.1.so[7f8c0e31f000+166000]
Jan 19 18:03:52 jfernandez-ubuntu kernel: Kernel logging (proc) stopped.

---

### Post by matedl on 2011-06-17
Any solution for this? 

I have a similar problem with VMware Player 3.1.4 and Ubuntu 11.04. As long as I do something in the virtual machine it stays running but if I go away for a "long" time (a few hours) the virtual machine shuts itself down.

---

### Post by hi2prans on 2012-02-15
I am also having a similar problem on Ubuntu 11.10. I have installed Windows on my VMWare server. Whenever I am playing age of empires on this server for about 15-20 minutes, my computer suddenly shuts down.

Unfortunately I do not know which log file to see for providing the output. So if anyone could help...

---

