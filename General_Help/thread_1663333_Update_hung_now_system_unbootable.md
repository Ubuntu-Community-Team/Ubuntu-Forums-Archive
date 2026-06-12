---
title: "Update hung now system unbootable"
date: 2011-01-09
forum: General Help
---

### Post by IceblueGen3 on 2011-01-09
(Ubuntu 10.10)

I left the pc on overnight to download and install updates, which included the latest kernel update. This morning it it showed that it was still configuring the update and just seemed to be stuck there. But the power menu at the top right corner was red and said the system needs to be restarted for updates to complete. So I clicked restart and it started shutting down but then stopped and said 'checking for running unattended updates' and never moved past that point. So I did a hard reset and waited for the login screen to appear.

At the login screen I tried to login but the mouse and keyboard do not function. I then restarted again and selected recovery mode but this time the system seemed to hang at a certain point before ever getting to the login screen. If I select recovery mode for the older kernel, it also stops before getting to login screen, but not at the same point as the newer kernel stops at. When it stops I can press ctrl-alt-del and the system starts terminating processes and then reboots, but only if i boot from the recovery options. If I try a normal boot option I have to do a hard reset.

How do I get the system running again?

---

### Post by dino99 on 2011-01-09
on a cold boot, choose: "recovery mode", then "repair packages", then "continue normal boot"

if that fail, you need to boot on livecd and chroot this broken system, following this example:

[http://ubuntuforums.org/showthread.php?t=1263030&page=2](http://ubuntuforums.org/showthread.php?t=1263030&page=2)

note for future nightly update/upgrade: deactivate screensaver, suspend/hibernate (powersaving) and mostly all third apps you can

---

### Post by IceblueGen3 on 2011-01-09
How do I get to the "repair packages" option? When I select "recovery mode" it just starts loading everything and doesn't give me any options.

During the update none of the things you mentioned were active, except for the 'Blank Screen' screensaver. Out of interest (and possible future reference) would there have been a safe way to terminate the hung update?

---

### Post by IceblueGen3 on 2011-01-09
OK I managed to fix it using the chroot method

Thanks for the help!

---

