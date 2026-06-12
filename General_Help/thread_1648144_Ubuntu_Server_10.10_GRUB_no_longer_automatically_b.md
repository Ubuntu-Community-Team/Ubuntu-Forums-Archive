---
title: "Ubuntu Server 10.10 GRUB no longer automatically boots"
date: 2010-12-18
forum: General Help
---

### Post by shadowwyvernx on 2010-12-18
Hello,

I rebooted a headless system running Ubuntu Server 10.10 x64 today, and for some reason could not access it from the network.  Further investigation showed that for whatever reason grub was no automatically selecting a option.  This occurred quite suddenly, I had successfully rebooted the system only minutes earlier.

Manually selecting the default option resulted in the system booting perfectly normally.  I subsequently fixed the problem by running "apt-get update" then "apt-get upgrade" which appeared to get some kernel related updates.  A reboot sowed grub to automatically make a selection again.

However, I am very concerned by the fact that there was no readily apparent reason for this to occur.  All I did was reboot a system - I had not even run apt-get between the last working reboot and the failed one.

So: 

1) Why did this happen?  Sure, it seems to be fixed, but it was fixed with essentially blind luck, and since I had to set up a head for the system to even do this, if this continues to occur it will prove untenable and very annoying.
2) Since updating the system fixed the issue, it seems logical an update might have cause the breakage.  However, I should have automatic updates disabled.  Is there a way to verify this?  I saw [http://www.uluga.ubuntuforums.org/showthread.php?t=1274168](http://www.uluga.ubuntuforums.org/showthread.php?t=1274168) but the file "/etc/apt/apt.conf.d/50unattended-upgrades" does not exist on my system.  I'm uneasy about accepting a truth based on a file not existing...

Thanks for your time :)

---

### Post by xhunter on 2010-12-20
I have the same problem.
I tried everything but i still have this problem...

Hope somebody will help us..

Thanks!

---

### Post by shadowwyvernx on 2010-12-20
You may try this: [http://ubuntuforums.org/showthread.php?t=1346305](http://ubuntuforums.org/showthread.php?t=1346305)

I suspect that with the kernel update I think happened when I ran "apt-get upgrade", a new grub.cfg was generated.  That link discusses that and a possible other solution.  I will be using it myself if the issue returns, but I would really enjoy an explanation, a bug report, something to provide a reason for why it happened, and why an update-like event even occurred on a system that should be explicitly configured to not auto-update (I think that's even the default for Server...)

Good luck :)

---

### Post by drs305 on 2010-12-20
If Grub 2 detects a problem during a boot it sets a 'recordfail' flag. This forces a manual selection on the next boot. 

The link *shadowwyvernx* provided shows how to modify the /etc/grub.d/00_header file to permanently disable the recordfail event. Modifying it in this manner will survive "update-grub" commands and will continue to work until the 00_header file is updated by a package update to Grub2. Depending on how critical it is, you could even lock the grub-pc package so that it isn't updated.

---

