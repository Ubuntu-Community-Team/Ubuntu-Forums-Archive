---
title: "/var/run/dbus/system_bus_socket   Missing"
date: 2009-12-28
forum: General Help
---

### Post by ranch hand on 2009-12-28
I am trying to update StonerEdition1.0 (9.04 respin) to 9.10.  I am using "apt-get dist-upgrade" with an edited /etc/apt/sources.list.  This was a clean install, updated to current (today) and then the upgrade attempt.

No restricted extras installed some of the packages that came with SE1.0 removed because I can't use them or do not need them.

SE1.0 had grub1.96 installed and in use before upgrade.

Renamed "/etc/X11/xorg.conf" to "xorg.conf.jaunty" before upgrade.

I have a long list of failures but the one that is key is the failure to configure "dbus".

This can't be done because the "/var/run/dbus/system_bus_socket" file is missing.  This file is not in the one other 9.10 I have on this drive but that is an Xfce respin of Ubuntu (Zenix  real nice).

I am doing this upgrade thru chroot from a testing version of 10.04 which does have this file.

I am not allowed to copy this file as root from one OS to another.

I have tried "dpkg --configure --force-configure-any dbus" with no luck at all.

As you can tell from my join date, which is earlier than my first in stall of Ubuntu (my first Linux), I am pretty green.  I am at the end of my string here on this problem.

This is not an important installation, it is on my test platform, it can be just wiped and forgotten.  I have had this problem once before, though, and would really like to get this cleared.

Any help greatly appreciated.

---

