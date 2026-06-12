---
title: "Telnetd"
date: 2009-07-22
forum: General Help
---

### Post by gus_zernial on 2009-07-22
I have a Kbuntu jaunty box with a custom 2.6.28 kernel. I've
installed telnetd and can telnet into the box, when the box 
has been started "nomally" (level 5). But when I start the
box in recovery mode (level 3) I can't telnet into the box,
and I can't figure out how to start telnetd on the box. 

I think Kbuntu jaunty uses the openbsd-inetd superserver,
which in turn uses inetd.conf, to start telnetd automatically 
on bootup, am I right???? Do I need to do something in 
inetd.conf or in rc3.d to start telnetd automatically 
when booting to recovery mode?

Or possibly this has to do with the fact that recovery
mode boot is into root??

And how do I start telnetd manually?

(BTW this box is inside a firewall and a DMZ, ssh
is not needed, and users prefer telnet)

---

