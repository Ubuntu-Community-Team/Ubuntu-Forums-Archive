---
title: "Unclean unmouting solution"
date: 2011-09-30
forum: General Help
---

### Post by dcstar on 2011-09-30
I was having issues with all my non-root filesystems never being unmounted correctly on shutdown/reboot, after much investigating the solution was incredibly simple:

[http://ubuntuforums.org/showthread.php?t=1783047](http://ubuntuforums.org/showthread.php?t=1783047)

It seems having all main shutdown (or reboot) script at the same run sequence number as many other scripts means that these are executed before these other critical scripts have completed - including unmounting these filesystems!

I know this affects 10.04 systems as a new test 10.04.3 install had the sequence set the same instead of last. It is ok in the 10.10, 11.04 & 11.10 beta systems that I have.

It seems to have been reported here: [https://bugs.launchpad.net/ubuntu/+source/sysvinit/+bug/739007](https://bugs.launchpad.net/ubuntu/+source/sysvinit/+bug/739007)

If you have issues with your root filesystem not being unmounted cleanly then you may want to check this bug:

[https://bugs.launchpad.net/ubuntu/+source/sysvinit/+bug/616287](https://bugs.launchpad.net/ubuntu/+source/sysvinit/+bug/616287)

---

