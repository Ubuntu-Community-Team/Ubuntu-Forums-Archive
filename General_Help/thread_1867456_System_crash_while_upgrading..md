---
title: "System crash while upgrading."
date: 2011-10-23
forum: General Help
---

### Post by UniversalBreakdown on 2011-10-23
My apologies if this is in the wrong section. A while ago I tried to upgrade an old PC I have from 8.04 to 10.04 and since then have not been able to get it running. Just wondering if the best option would be to re install ubuntu and what would be the best method of doing this? Also my root password seems doesn't work anymore. 

init: ureadahead man process (2496) terminated with status 5
libudev: udev_monitor_new_from_netlink: error getting socket : Invalid argument
mountall:mountall.c:3204: Assertion failed in main: udev_monitor = uder_monitor_new_from_netlink (udev, "udev")
init:montall main process (2499) killed by ABRT signal 
General error mounting filesystems.
A maintenance shell will now be started. 
control-D will terminate this shell and reboot the.....ect ect ect....

I'm lost. I can start in recovery mode and get to command line.
any help is good help. 

thanks.

---

### Post by Ralph Hinkley on 2011-10-23
Are you able to boot up using a live cd? If so, I'd use the live  cd to grab any important files I want to salvage, then do a fresh install from the cd. apologies if you've already tried that.

---

