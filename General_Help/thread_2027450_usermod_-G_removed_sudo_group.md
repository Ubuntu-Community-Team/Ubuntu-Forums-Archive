---
title: "usermod -G removed sudo group"
date: 2012-07-16
forum: General Help
---

### Post by jony121 on 2012-07-16
I set up a system with one user with sudo.
I then used "sudo usermod -G" rather than "sudo usermod -a -G" and now my user is no longer a member of the sudo group.

How can I manually add a user to a group? I am guessing I will have to use a livecd but which files do I alter?

TIA

---

### Post by steeldriver on 2012-07-16
unless you set a root password and have forgotten it, there should be no need to boot from a livecd - just reboot to the recovery console and add your user back to sudo from there

on newer installations you will likely need to remount the root filesystem read-write first

```
# mount -o remount,rw /
# usermod -aG sudo *user*
# exit
```

---

### Post by jony121 on 2012-07-16
You fixed it! I never would have thought of recovery mode.

You == Diamond

:)

---

