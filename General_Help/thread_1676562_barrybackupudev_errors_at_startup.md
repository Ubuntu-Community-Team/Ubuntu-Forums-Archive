---
title: "barrybackup/udev errors at startup"
date: 2011-01-27
forum: General Help
---

### Post by cyncicle on 2011-01-27
So, I got barrybackup to work on Maverick by moving the blackberry.rules file as recommended in another thread.  It seems to work fine.

My problem is now I'm getting a bunch of udev errors at startup:

```
fsck from util-linux-ng 2.17.2 
udevd[327]: BUS= will be removed in a future udev version, please use SUBSYSTEM= to match the event device, or SUBSYSTEMS= to match a parent device, in /etc/udev/rules.d/65-blackberry.rules:21 
  
udevd[327]: SYSFS{}= will be removed in a future udev version, please use ATTR{}= to match the event device, or ATTRS{}= to match a parent device, in /etc/udev/rules.d/65-blackberry.rules:21 
  
udevd[327]: BUS= will be removed in a future udev version, please use SUBSYSTEM= to match the event device, or SUBSYSTEMS= to match a parent device, in /etc/udev/rules.d/65-blackberry.rules:23 
  
udevd[327]: SYSFS{}= will be removed in a future udev version, please use ATTR{}= to match the event device, or ATTRS{}= to match a parent device, in /etc/udev/rules.d/65-blackberry.rules:23 
  
udevd[327]: BUS= will be removed in a future udev version, please use SUBSYSTEM= to match the event device, or SUBSYSTEMS= to match a parent device, in /etc/udev/rules.d/65-blackberry.rules:29 
  
udevd[327]: SYSFS{}= will be removed in a future udev version, please use ATTR{}= to match the event device, or ATTRS{}= to match a parent device, in /etc/udev/rules.d/65-blackberry.rules:29 
  
udevd[327]: BUS= will be removed in a future udev version, please use SUBSYSTEM= to match the event device, or SUBSYSTEMS= to match a parent device, in /etc/udev/rules.d/65-blackberry.rules:30 
  
udevd[327]: SYSFS{}= will be removed in a future udev version, please use ATTR{}= to match the event device, or ATTRS{}= to match a parent device, in /etc/udev/rules.d/65-blackberry.rules:30 
  
udevd[327]: BUS= will be removed in a future udev version, please use SUBSYSTEM= to match the event device, or SUBSYSTEMS= to match a parent device, in /etc/udev/rules.d/65-blackberry.rules:31 
  
udevd[327]: SYSFS{}= will be removed in a future udev version, please use ATTR{}= to match the event device, or ATTRS{}= to match a parent device, in /etc/udev/rules.d/65-blackberry.rules:31 
  
udevd[327]: BUS= will be removed in a future udev version, please use SUBSYSTEM= to match the event device, or SUBSYSTEMS= to match a parent device, in /etc/udev/rules.d/65-blackberry.rules:33 
```I'm thinking I need to edit the file, but I don't really understand the errors.  Anyone have suggestions?

---

