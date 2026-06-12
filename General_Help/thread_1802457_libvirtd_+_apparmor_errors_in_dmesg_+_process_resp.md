---
title: "libvirtd + apparmor: errors in dmesg + process respawning alot"
date: 2011-07-12
forum: General Help
---

### Post by jmoorse on 2011-07-12
This has been bugging me for a while, haven't been able to figure out a resolution.  I run qemu and virtualbox every once in a while but log entries appear when they are not running

dmesg output:

[] type=1400 audit(1310444517.368:106093): apparmor="DENIED" operation="exec" parent=11531 profile="/usr/sbin/libvirtd" name="/usr/local/bin/qemu" pid=11569 comm="libvirtd" requested_mask="x" denied_mask="x" fsuid=0 ouid=0

Also:

Watching top shows the libvirtd process relaunching at least every 1sec under a different PID.

Ideas?

---

### Post by jmoorse on 2011-07-17
I ended up fixing this by editing the libvirtd profile: /etc/apparmor.d/usr.sbin.libvirtd

[snip]
  /bin/* PUx,
  /sbin/* PUx,
  /usr/bin/* PUx,
  /usr/sbin/* PUx,
  /usr/local/bin/qemu* PUx, <-------I added this rule
[snip]

And reloading the profile:

sudo apparmor_parser -r /etc/apparmor.d/usr.sbin.libvirtd

---

