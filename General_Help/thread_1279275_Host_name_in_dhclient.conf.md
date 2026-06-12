---
title: "Host name in dhclient.conf"
date: 2009-09-30
forum: General Help
---

### Post by cbmanica on 2009-09-30
After spending a good part of today trying to figure out why my two Ubuntu installs (one 8, one an 8 -> 9 upgrade) seemed to be visible on the corporate network, but not my new Debian 5 netinstall, I tracked down this line in dhclient.conf on the Ubuntu installs:

send host-name "<hostname>";

Is Ubuntu, possibly in the form of Network Manager or something else, magically changing that placeholder into my actual hostname?  Or is Ubuntu doing something else equally magical to tell the DHCP server what host is requesting a lease?  In any case, I had to explicitly specify the hostname in dhclient.conf on the Debian box, so I'm curious what's happening behind the scenes here.

---

### Post by Iowan on 2009-09-30
I've always changed that line to specify my hostname, and [this]("http://ubuntuforums.org/showthread.php?t=275733") old thread is my attempt to do what you say is happening.
  You could try changing the hostname to something else to see if the network echoes the change - or comment out the line to see if the machine disappears from the radar.

---

