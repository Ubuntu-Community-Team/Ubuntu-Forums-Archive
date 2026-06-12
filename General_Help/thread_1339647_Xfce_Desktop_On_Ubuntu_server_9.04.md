---
title: "Xfce Desktop On Ubuntu server 9.04"
date: 2009-11-27
forum: General Help
---

### Post by StreetWise on 2009-11-27
Hi, I just got a dedicated server running Ubuntu server 9.04, I logged in via putty and installed Xfce Desktop environment.

At the end of the installation i was given this error:


Setting up acpid (1.0.6-9ubuntu4.9.04.3) ...
 * Starting ACPI services...                                                    acpid: can't open /proc/acpi/event: No such file or directory
invoke-rc.d: initscript acpid, action "start" failed.
dpkg: error processing acpid (--configure):
 subprocess post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of acpi-support:
 acpi-support depends on acpid (>= 1.0.4-1ubuntu4); however:
  Package acpid is not configured yet.
dpkg: error processing acpi-support (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of xubuntu-desktop:
 xubuntu-desktop depends on acpid; however:
  Package acpid is not configured yet.
dpkg: error processing xubuntu-desktop (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 acpid
 acpi-support
 xubuntu-desktop
I have tried: sudo /etc/init.d/acpid stop
sudo dpkg --configure acpid
sudo dpkg --configure -a

but nothing seems to work. apps seem to be able to install though.

---

### Post by StreetWise on 2009-11-28
Bump

---

