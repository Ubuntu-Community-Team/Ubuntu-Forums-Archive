---
title: "Upgrade to 9.10 failed, cannot boot"
date: 2009-11-21
forum: General Help
---

### Post by Culler on 2009-11-21
I tried upgrading from 9.04 to 9.10, the upgrade failed (something about system in an unusable state around halfway of installing) and I had to reboot, now I can't reach the desktop. The error is:

One or more of the mounts listed in /etc/fstab cannot yet be mounted:
(ESC for recovery shell)
/: waiting for /dev/disk/by-uuid/02cdfa0e-4c7e-4628-ae88-dc577914efb8
/tmp: waiting for (null)
swap: waiting for UUID=af46fa52-580d-414f-ac78-dde763885032
/proc/bus/usb: waiting for none

Any suggestions?

---

### Post by Culler on 2009-11-21
Well, I was able to get a little further using [http://ubuntuforums.org/showthread.php?t=1312671](http://ubuntuforums.org/showthread.php?t=1312671)

Esc                      to enter recovery shell
mount -a                 to mount all of the devices in /etc/fstab
mount -o remount,rw /    to make the root dir writeable
dpkg --configure -a       (or something like that) to resume the upgrade

But it stalls on dpkg with:
dpkg: parse error, in file 'var/lib/dpkg/status' near line 38806 package 'dhcp3-common':
'Depends' field, reference to 'libc6': version contains ` '

---

### Post by Culler on 2009-11-21
Managed to fix this. Copied over the corrupted status file with a backup that is kept in the same dir. [http://ubuntuforums.org/showthread.php?t=474587](http://ubuntuforums.org/showthread.php?t=474587)

cp /var/lib/dpkg/status-old /var/lib/dpkg/status
Reran dpkg --configure -a
And then rebooted, now I can log in.

---

