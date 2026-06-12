---
title: "error in 11.04 boot"
date: 2011-05-01
forum: General Help
---

### Post by tubbzor on 2011-05-01
I just updated from 10.10 to 11.04, but on start up after selecting 11.04 from the grup, a bunch of checks come up and one says
stopping automatic crash report generation...[FAIL]
and all the others are [OK]..and it freezes on this screen and does not let me proceed.
when i run the older version of ubuntu i have no menus and can't even drag windows..
someone help me please!

---

### Post by oldfred on 2011-05-01
Can you boot recovery mode from grub menu? That often gives some choices on fixes.

Upgrade Guide/Issues Including 11.04 mörgæs
[http://ubuntuforums.org/showthread.php?t=1580857](http://ubuntuforums.org/showthread.php?t=1580857)

---

### Post by tubbzor on 2011-05-01
yeah booted in recovery mode and ran some package updaters and same thing happened

---

### Post by oldfred on 2011-05-01
If you get grub menu, it is booting, perhaps a video issue?  Or some other hardware setting? What system is it?

How to set NOMODESET and other kernel boot options in grub2 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)

[https://help.ubuntu.com/community/LiveCDBootOptions](https://help.ubuntu.com/community/LiveCDBootOptions)
[http://www.mjmwired.net/kernel/Documentation/kernel-parameters.txt](http://www.mjmwired.net/kernel/Documentation/kernel-parameters.txt)
noapic nolapic noapci noirqpoll nosmp irqpoll
[http://www.kernel.org/doc/Documentation/kernel-parameters.txt](http://www.kernel.org/doc/Documentation/kernel-parameters.txt)

[https://wiki.ubuntu.com/NattyNarwhal/ReleaseNotes#Known%20Issues](https://wiki.ubuntu.com/NattyNarwhal/ReleaseNotes#Known%20Issues)
Specific Issues by machine:
[https://wiki.ubuntu.com/HardwareSupport/](https://wiki.ubuntu.com/HardwareSupport/)
[https://wiki.ubuntu.com/HardwareSupport/Machines/Netbooks/](https://wiki.ubuntu.com/HardwareSupport/Machines/Netbooks/)

---

