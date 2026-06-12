---
title: "System Halts but Power stays on at Shutdown"
date: 2009-11-01
forum: General Help
---

### Post by Rickspark on 2009-11-01
The hard disk stops but the monitor and system unit power stay on when trying to Shutdown

I installed Ubuntu 9.1 a few days ago and the system otherwise works really well.

Entering 'sudo shutdown -h now' does just the same as selecting shutdown - Power and monitor stay on, hard disk stops

Following some guidance from you folks here and research and reading elsewhere, I have now done the following in a last ditch effort to get a bit more life from this old Pentium III...

- Updated the AMI Bios

- Checked the Bios is configure to APM

- From an earlier posting and readying, added the following to /etc/grub.d/40_custom
acpi=off
apm=on
apm=power_off

- Added the following to /etc/modprobe.d/power.conf
amp power_off=1
realmode_power_off=1

....but still had no luck.  Any final thoughts before I abandon the idea of a power off shutdown?

Thank you for looking!

---

### Post by P4man on 2009-11-01
You need ACPI for that, not APM at least as far as I know.
If you did a wubi install you might also have the same problem as this guy:
[http://ubuntuforums.org/showthread.php?t=1309075](http://ubuntuforums.org/showthread.php?t=1309075)

also check the workaround I suggested there, see if that works or not.

---

