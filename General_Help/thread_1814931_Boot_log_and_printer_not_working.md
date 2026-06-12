---
title: "Boot log and printer not working"
date: 2011-07-30
forum: General Help
---

### Post by anselm on 2011-07-30
Hello everyone,

I have noticed since I have updated to 10.04.3 this has been coming up in my boot log.

udevd[249]: SYSFS{}= will be removed in a future udev version, please use ATTR{}= to match the event device, or ATTRS{}= to match a parent device, in /etc/udev/rules.d/85-brltty.rules:23

Also my printer has quit working also, have tried reinstalling cups, reinstalling the print drivers printer still does not work.

Does this entry in the the boot log have anything to do with the printer?

Thanks

---

### Post by ajgreeny on 2011-07-30
I get almost the same error message in my boot.log, only the numbers are different, and in my case it appears twice with number differences between both of my two versions and your version.

I suspect this is all part of the change from init.d to upstart or something of that kind, but whatever is causing it, I have no problems with my system, and I can still print with no problem, so I don't think the message is of consequence, and do not think it is anything to do with your printer problems.  What printer is it; has it always worked OK before the update?

Here's my boot.log twin entries:-
> udevd[335]: SYSFS{}= will be removed in a future udev version, please use ATTR{}= to match the event device, or ATTRS{}= to match a parent device, in /etc/udev/rules.d/56-hpmud_support.rules:10 
  
udevd[335]: SYSFS{}= will be removed in a future udev version, please use ATTR{}= to match the event device, or ATTRS{}= to match a parent device, in /etc/udev/rules.d/56-hpmud_support.rules:12

---

### Post by anselm on 2011-07-30
Yea my printer worked before the update, it is a dell photo 720 printer it is the same printer as a lexmark z600 printer. I used the drivers for the lexmarkz 600 printer made by redhat they were the only linux distro that had made drivers for this printer. The drivers were in tar form had to install from the command line, tried reinstall the drivers did not help.

---

### Post by ajgreeny on 2011-07-30
In that case I assume the redhat driver is not compatible with ubuntu 10.04.  Sorry, but I have nothing else to suggest.

---

