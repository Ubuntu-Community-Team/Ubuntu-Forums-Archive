---
title: "Ubuntu 11.04 and 11.10 not heeding DHCP option 42 for NTP-servers"
date: 2011-10-24
forum: General Help
---

### Post by k999 on 2011-10-24
Hi,

I've set up an NTP server on a closed network. The DHCP server's IP is distributed using DHCP Option 42 (ntp-servers). This was automatically picked up by an Ubuntu 10.04 Lucid Lynx server.

However, I've set up several instances of Ubuntu 11.04 Natty Narwhal and now Ubuntu 11.10 Oneiric Ocelot, and they aren't picking up this information.

More specifically, I can see that the Ubuntu 11.* servers are receiving the correct information from the DHCP server, because dhclient's lease file shows the correct information (twice for some reason, but that shouldn't matter). When this information is received and ntpd is installed (which it is!), dhclient has a trigger that should have written a file /var/lib/ntp/ntp.conf.dhcp, which would later have been picked up by ntpd, but this file is never written.

Attempting to debug further, I noticed there's a debug trigger in dhclient's trigger directory. I tried to enable it, but nothing happens. I evn tried editing /sbin/dhclient-script directly to output this very simple debug info, but the file /tmp/abc isn't even created:
```
echo "HELLO" > /tmp/abc
```

So it appears to me that the problem with Ubuntu 11.* is that /sbin/dhclient-script isn't actually run at all, at least on the desktop installs I have. Looking at /var/log/syslog and trying to understand apparmor's output, it appears that /usr/lib/connman/scripts/dhclient-script is called, but that file doesn't exist on my system. I tried symlinking it to /sbin/dhclient-script, but that didn't help either.

Has anyone else got this working, who can help confirm/refute this?

---

