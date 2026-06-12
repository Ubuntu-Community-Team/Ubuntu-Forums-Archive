---
title: "I got an NTP error and I think it is related to apparmor."
date: 2009-11-19
forum: General Help
---

### Post by MechaMechanism on 2009-11-19
The NTP error I got.  How do I fix the error.  Is it harmless or should I file a bug report.

```
ntpd[1840]: can't open /var/lib/ntp/ntp.drift.TEMP: Permission denied
``````
kernel: [   21.973691] type=1503 audit(1258411534.417:26): operation="capable" pid=1840 parent=1 profile="/usr/sbin/ntpd" name="dac_override"
```I use 9.10 and am fully updated as of Thurs, Nov 10.

My AppArmor profile came with the system.
> # vim:syntax=apparmor
# Last Modified: Tue Aug 11 16:14:21 CDT 2009
# Updated for Ubuntu by: Jamie Strandboge <jamie@canonical.com>
# ------------------------------------------------------------------
#
#    Copyright (C) 2002-2005 Novell/SUSE
#
#    This program is free software; you can redistribute it and/or
#    modify it under the terms of version 2 of the GNU General Public
#    License published by the Free Software Foundation.
#
# ------------------------------------------------------------------

#include <tunables/global>
#include <tunables/ntpd>
/usr/sbin/ntpd {
  #include <abstractions/base>
  #include <abstractions/nameservice>
  #include <abstractions/user-tmp>

  capability ipc_lock,
  capability net_bind_service,
  capability setgid,
  capability setuid,
  capability sys_chroot,
  capability sys_resource,
  capability sys_time,

  network inet dgram,
  network inet stream,
  network inet6 stream,

  @{PROC}/net/if_inet6 r,
  @{PROC}/*/net/if_inet6 r,
  @{NTPD_DEVICE} r,

  /usr/sbin/ntpd rmix,

  /etc/ntp.conf r,
  /etc/ntp.conf.dhcp r,
  /etc/ntpd.conf r,
  /etc/ntpd.conf.tmp r,

  /etc/ntp.keys r,
  /etc/ntp/** r,

  /etc/ntp.drift rwl,
  /etc/ntp.drift.TEMP rwl,
  /etc/ntp/drift* rwl,
  /var/lib/ntp/*drift rw,
  /var/lib/ntp/*drift.TEMP rw,

  /var/log/ntp w,
  /var/log/ntp.log w,
  /var/log/ntpd w,
  /var/log/ntpstats/loopstats* rwl,
  /var/log/ntpstats/peerstats* rwl,

  /var/run/ntpd.pid w,
}I found this in tunables.
> # Last Modified: Thu Aug  2 14:37:03 2007
# $Id: usr.sbin.ntpd 1102 2008-02-19 10:35:19Z jrjohansen $
# ------------------------------------------------------------------
#
#    Copyright (C) 2002-2005 Novell/SUSE
#
#    This program is free software; you can redistribute it and/or
#    modify it under the terms of version 2 of the GNU General Public
#    License published by the Free Software Foundation.
#
# ------------------------------------------------------------------

#Add your ntpd devices here eg. if you have a DCF clock
# @{NTPD_DEVICE}=/dev/ttyS*
@{NTPD_DEVICE}="/dev/tty10"

---

### Post by p.elsie on 2010-05-24
I think I had the same problem.  In my case I tracked it down to ebox-ntp and reported it on their site.  

[http://trac.ebox-platform.com/ticket/1907](http://trac.ebox-platform.com/ticket/1907)

BTW: for considering Apparmor bugs take a look at [https://wiki.ubuntu.com/DebuggingApparmor](https://wiki.ubuntu.com/DebuggingApparmor) - I'm not sure what a "capable" operation is, but I don't think it is one that creates a temp file - I'd expect maybe something that starts with "file".

---

