---
title: "Reboot problems related to Scroll lock"
date: 2012-09-06
forum: General Help
---

### Post by Aikidokajeff on 2012-09-06
Hi,
 
Summary: System will not reboot when scrool lock is active.
 
Details:
 
I have multiple servers running various editions of Ubuntu (and other Linux variants) and have come across a frustrating issue.
 
(I have tested this on multiple setups, not just the one I mention here)
 
We have a KVM that uses "Scroll lock" + "Scroll lock" + Spacebar to switch between screens.
 
I had a problem the other day where a scheduled reboot did not complete.
After investigating through SSH I couldn't see why this was the case.
 
Checking the console session did nothing as it wasn't responding. 
Looking further I was able to switch TTYs but not type anything.
 
I noticed that scroll lock was on, turned it off and the system promptly rebooted.
 
Basically the crontab reboot command was held as the scroll lock also holds console output.
I have only been able to find one other post through google searches where someone else has had this problem.
 
I'm wondering if anyone else has noticed this and more importantly; have they created a workaround to allow the system to shutdown even when the scroll lock is active.
 
FYI I have already used "setleds" to turn off scroll lock on all TTYs and although it does turn the scroll lock off (led and flag set to off) the session is still frozen and the reboot doesn't continue until scroll lock is pressed again.
 
If a better solution can't be found I think I might have to remap the keyboard to disable the scroll lock key in the OS, but I'd rather not as sometimes scroll lock has a use.
 
Additional info:
System described above: Ubuntu 8.04 LTS (Server install)
Seen a report of Centos 5 having the same problem:
[https://fonality.com/trixbox/forums/trixbox-forums/open-discussion/no-reboot-scroll-lock-enabled-console-keyboard](https://fonality.com/trixbox/forums/trixbox-forums/open-discussion/no-reboot-scroll-lock-enabled-console-keyboard)
 
If there is anything else you'd like to know, just ask.
 
thanks,
 
Jeff

---

