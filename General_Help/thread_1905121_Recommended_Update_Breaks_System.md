---
title: "Recommended Update Breaks System"
date: 2012-01-06
forum: General Help
---

### Post by Blackbird_13 on 2012-01-06
Recommended Maverick update (libgweather-common) failed and totally messed up system - see terminal output.

> 1 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 1,010kB of archives.
After this operation, 0B of additional disk space will be used.
Do you want to continue [Y/n]? Y
Get:1 [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) maverick-updates/main libgweather-common all 2.30.3-0ubuntu1.1 [1,010kB]
Fetched 1,010kB in 4s (234kB/s)             
(Reading database ... 266452 files and directories currently installed.)
Preparing to replace libgweather-common 2.30.3-0ubuntu1 (using .../libgweather-common_2.30.3-0ubuntu1.1_all.deb) ...
Unpacking replacement libgweather-common ...
Processing triggers for gnome-icon-theme ...
gtk-update-icon-cache: **
Gtk:ERROR:/build/buildd/gtk+2.0-2.22.0/gtk/updateiconcache.c:1102:write_bucket: assertion failed: (*offset == ftell (cache))
Aborted
WARNING: icon cache generation failed
dpkg: unrecoverable fatal error, aborting:
 unable to flush updated status of `gnome-icon-theme': Read-only file system
touch: cannot touch `/var/lib/update-notifier/dpkg-run-stamp': Read-only file system
sh: cannot create /var/lib/update-notifier/updates-available: Read-only file system
E: Problem executing scripts DPkg:ost-Invoke 'if [ -d /var/lib/update-notifier ]; then touch /var/lib/update-notifier/dpkg-run-stamp; fi; if [ -e /var/lib/update-notifier/updates-available ]; then echo > /var/lib/update-notifier/updates-available; fi '
E: Sub-process returned an error code
E: Sub-process /usr/bin/dpkg returned an error code (2)After the failure to upgrade I couldn't get into "system log", "system monitor" or open a "terminal" -  windows did open, but they only had a white background. PC then failed to reboot, halting at at a busybox terminal.

Fortunately I am running Maverick in VirtualBox so was able to have another go from a previous saved snapshot. Have tried the update from "Update Manager" and "Synaptic" with the same result. The other recommended upgrades were successfully installed.

Does anyone know how I should proceed?

---

### Post by Catharsis on 2012-01-06
Whoa, sounds like a bug in the package. Immediately after the upgrade, run 'ubuntu-bug libgweather-common' and give the developers all that info you just gave.

---

### Post by Blackbird_13 on 2012-01-06
Thanks for your reply. I have now reported my problem: Bug #912724

---

