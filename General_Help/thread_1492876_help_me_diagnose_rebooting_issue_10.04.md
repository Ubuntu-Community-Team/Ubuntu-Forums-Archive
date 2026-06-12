---
title: "help me diagnose rebooting issue 10.04"
date: 2010-05-25
forum: General Help
---

### Post by extendedping on 2010-05-25
well I was using 9.10 with no issues and did the upgrade 2 weeks ago to 10.04. since that first week my pc has been randomly rebooting several times a day. there was never any issue before the upgrade and my pc is in a apc es 650 ups. I was just hoping my post of var log messages might give a clue. I do realize this is probably just an 3 year old computer saying "time to upgrade" but I'd really like some expert advice first. I get a beep and a reboot.  I put a little "before" but you can see the latest reboot occurred at at 08:05. also as a side note, I have a static ip and the command /etc/init.d/dhcp3-server status shows "Status of DHCP server: dhcpd3 is not running" so what are those dhcpd messages? thanks much. 

May 25 06:22:43 ubnuntu dhcpd: Internet Systems Consortium DHCP Server V3.1.3
May 25 06:22:43 ubnuntu dhcpd: Copyright 2004-2009 Internet Systems Consortium.
May 25 06:22:43 ubnuntu dhcpd: All rights reserved.
May 25 06:22:43 ubnuntu dhcpd: For info, please visit [https://www.isc.org/software/dhcp/](https://www.isc.org/software/dhcp/)
May 25 06:22:43 ubnuntu dhcpd: Wrote 0 leases to leases file.
May 25 06:22:43 ubnuntu dhcpd: 
May 25 06:22:50 ubnuntu pulseaudio[5288]: lock-autospawn.c: Cannot access autospawn lock.
May 25 06:51:55 ubnuntu rsyslogd: [origin software="rsyslogd" swVersion="4.2.0" x-pid="3929" x-info="http://www.rsyslog.com"] rsyslogd was HUPed, type 'lightweight'.
May 25 08:05:32 ubnuntu rsyslogd: [origin software="rsyslogd" swVersion="4.2.0" x-pid="3814" x-info="http://www.rsyslog.com"] (re)start
May 25 08:05:32 ubnuntu rsyslogd: rsyslogd's groupid changed to 102
May 25 08:05:32 ubnuntu rsyslogd: rsyslogd's userid changed to 101
May 25 08:05:34 ubnuntu libvirtd: 08:05:34.109: warning : qemudStartup:1076 : Unable to create cgroup for driver: No such device or address
May 25 08:05:34 ubnuntu libvirtd: 08:05:34.205: warning : lxcStartup:1755 : Unable to create cgroup for driver: No such device or address
May 25 08:05:34 ubnuntu dhcpd: Internet Systems Consortium DHCP Server V3.1.3
May 25 08:05:34 ubnuntu dhcpd: Copyright 2004-2009 Internet Systems Consortium.
May 25 08:05:34 ubnuntu dhcpd: All rights reserved.
May 25 08:05:34 ubnuntu dhcpd: For info, please visit [https://www.isc.org/software/dhcp/](https://www.isc.org/software/dhcp/)
May 25 08:05:34 ubnuntu dhcpd: Internet Systems Consortium DHCP Server V3.1.3
May 25 08:05:34 ubnuntu dhcpd: Copyright 2004-2009 Internet Systems Consortium.
May 25 08:05:34 ubnuntu dhcpd: All rights reserved.
May 25 08:05:34 ubnuntu dhcpd: For info, please visit [https://www.isc.org/software/dhcp/](https://www.isc.org/software/dhcp/)
May 25 08:05:34 ubnuntu dhcpd: Wrote 0 leases to leases file.
May 25 08:05:34 ubnuntu dhcpd: 
May 25 08:05:41 ubnuntu pulseaudio[5232]: lock-autospawn.c: Cannot access autospawn lock.
brad@ubnuntu:~$

---

### Post by extendedping on 2010-05-25
is there any other information/file I could post to help diagnose the issue? I really don't want to lose all my pictures etc (my external hd is already full) but don't want to go ahead with a new pc if this is os related...

---

### Post by dino99 on 2010-05-25
rebooting is often a temperature issue, how are yours ? be sure fans are running normally. If the system is overclocked, use normal settings, or look to a clean up.

looking at .xsession-errors (unhide it with menu, /home)

or/and: system admin log viewer, mostly xorg, system , messages, user

---

### Post by extendedping on 2010-05-25
> **dino99 said:**
> rebooting is often a temperature issue, how are yours ? be sure fans are running normally. If the system is overclocked, use normal settings, or look to a clean up.

looking at .xsession-errors (unhide it with menu, /home)

or/and: system admin log viewer, mostly xorg, system , messages, user

thanks I am going to check this tonight, but I know I never overclocked (never touched the bios).

---

