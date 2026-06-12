---
title: "boot up failure"
date: 2010-08-19
forum: General Help
---

### Post by bradhaack on 2010-08-19
ubuntu 9.10 
Won't boot.  Not a new installation, no new hardware.
When I boot it up into 2.5.31-22-generic safemode it says:
One or more of the mounts listed in etc/fstab cannot yet be mounted:
/home: wating for UUID...

Booted up w/ live CD, fsck says that /dev/sda3 is clean
I have a 320 GB hard drive, 20 GB is the linux boot, 2 GB is swap, and the rest is /home.  Palimpset Disk Utility can recognize the 20 & swap, but says the rest is unrecognized.

Can I recover this?  Any help is appreciated

Attached is the output from boot_info_script

---

### Post by bradhaack on 2010-08-19
I found that if I booted up from a 10.04 live CD it could see the disk no problem.  I installed 10.04 and am now up and running.  

I would like to know what happened, so if anyone has any ideas ...

---

