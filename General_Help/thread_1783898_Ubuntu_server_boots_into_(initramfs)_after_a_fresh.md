---
title: "Ubuntu server boots into (initramfs) after a fresh install"
date: 2011-06-16
forum: General Help
---

### Post by kingcu on 2011-06-16
I installed server 10.04.2 on a dell R410. On the first restart after the fresh install, it boots into (initramfs) with the following on console:

```

Gave up waiting for root device.  Common problems:
 - Boot args (cat /proc/cmdline)
   - Check rootdelay= (did the system wait long enought?)
   - check root= (did the system wait for the right device?)
 - Missing modules (cat /proc/modules; ls /dev)
ALERT! /dev/mapper/cecdata-root does not exist. Dropping to a shell!


BusyBox v1.13.3 (Ubuntu 1:1.13.3-1ubuntu11) built-in shell (ash)
Enter 'help' for a list of built-in commands.

(initramfs)

```
I had to type "exit" to exit (initramfs) and boot into the normal command line for login. Anyone had the same issue?

**Edit**: forgot to mention, the install was on a RAID 0 of 2 1TB HDDs, not sure if RAID 0 has anything to do with the error.

---

### Post by _Cattz_ on 2011-09-07
I'm having the same issue in a Dell server with 2 HD in RAID 1.
I've reinstalled the server several times, includding destroying and re-creating the RAID volume.

Have you managed to resolve this?

Thanks

---

