---
title: "rc.local processes some entries but not others"
date: 2011-07-12
forum: General Help
---

### Post by star_trooper_man on 2011-07-12
My rc.local file is this:

echo auto > /sys/bus/usb/devices/1-2/power/level
echo auto > /sys/bus/usb/devices/1-4/power/level
echo min_power > /sys/class/scsi_host/host0/link_power_management_policy
echo min_power > /sys/class/scsi_host/host1/link_power_management_policy
echo 1 > /sys/module/snd_hda_intel/parameters/power_save
echo 1500 > /proc/sys/vm/dirty_writeback_centisecs
for i in /sys/bus/pci/devices/*/power/control ; do echo auto > $i ; done
hdparm -B 2 -M 128 -S 12 /dev/sda
exit 0

The owner is "root" and the permissions are 744.  When run manually, i.e. sudo /etc/rc.local, it all works.  When loaded automatically on booting, it appears to implement the first two entries, and then stop.  My question: why is this, and how can it be resolved, that is, how can I execute all these automatically?

---

### Post by mali2297 on 2011-07-13
Check that the script does not contain any *bashisms* but can be run using /bin/sh:
```

sudo /bin/sh /etc/rc.local

```

---

### Post by star_trooper_man on 2011-07-13
Well, I seem to have created a different script, and configured it to run automatically, except that it doesn't seem to work either.  The script is


#! /bin/sh
#/etc/init.d/autorun
#
PATH=/sbin:/usr/sbin:/bin:/usr/bin
# Some things that run always
echo auto > /sys/bus/usb/devices/1-2/power/level
echo auto > /sys/bus/usb/devices/1-4/power/level
echo 1 > /sys/module/snd_hda_intel/parameters/power_save
echo 1500 > /proc/sys/vm/dirty_writeback_centisecs
for i in /sys/class/scsi_host/*/link_power_management_policy ; do echo min_power
 > $i ; done
for i in /sys/bus/pci/devices/*/power/control ; do echo auto > $i ; done
hdparm -B 2 -M 128 -S 12 /dev/sda

exit 0

and the permissions are 755; again it's owned by root.  And yes, it satisfies your test and works with 
sudo /bin/sh /etc/init.d/autorun

UPDATE
I've ascertained that the script does execute, by putting various "echo" statements at both ends.  This, weakly, suggests that the script runs but either the statements it contains are not all executed or that the changes made are reverted.  Where might I be going wrong?

---

