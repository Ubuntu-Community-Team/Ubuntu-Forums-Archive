---
title: "mrtg configuration"
date: 2011-11-08
forum: General Help
---

### Post by Bevlar on 2011-11-08
Hi,

I have Nagios configured with MRTG which is working fine.

What I would like to know is how to add an additional switch for monitoring.

When I defined a new switch 172.16.90.250 it overwrote the existing switch 172.16.90.101

Any advice appreciated.

---

### Post by dcstar on 2011-11-08
> **Bevlar said:**
> Hi,

I have Nagios configured with MRTG which is working fine.

What I would like to know is how to add an additional switch for monitoring.

When I defined a new switch 172.16.90.250 it overwrote the existing switch 172.16.90.101

Any advice appreciated.

[http://nagios.sourceforge.net/docs/3_0/monitoring-routers.html](http://nagios.sourceforge.net/docs/3_0/monitoring-routers.html)

---

### Post by Bevlar on 2011-11-14
Hi

I'll try to be a little clearer.

I want to monitor bandwidth usage on multiple switches.

I have successfully setup the first switch localhost@172.16.90.201
it has generated all the .png images and logs required by MRTG.

I added the following to MRTG.cfg

include: switch2.cfg

This does not generate the .pngs and logs for switch2.cfg


Any idea where i might be going wrong?

I used this guide to configure MRTG
[http://linuxbasement.com/content/mrtg-ubuntu-server]("http://linuxbasement.com/content/mrtg-ubuntu-server")

---

