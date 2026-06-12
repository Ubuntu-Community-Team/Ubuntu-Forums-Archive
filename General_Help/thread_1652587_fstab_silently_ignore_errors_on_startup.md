---
title: "fstab: silently ignore errors on startup"
date: 2010-12-25
forum: General Help
---

### Post by vbSteve on 2010-12-25
Hi,


I have an external USB hard drive configured in fstab to mount using UUID. Everything mounts fine, but when I unplug the drive and the server starts up again, it's telling me that the drive is not ready or present (obviously, because it's unplugged), but the startup sequence gets stuck on that error.

How do I make it so that it ignores that error automatically if it's not present.  It's not a vital drive,  just user data and i have to unplug the drive because otherwise it keeps spinning and it will wear too much over time. I also want the drive to get automatically mounted when I plug it back in, so that i don't have to loggon to my server first.

Anyway, here are the lines that I have in my fstab:
UUID=3253b05f-ce8f-4ea0-afb8-1bb212be1e45 /home/store/usb-store ext4 defaults,user 0 0


Anyone got a solution for this?
Thanks.

---

### Post by Morbius1 on 2010-12-25
> Anyway, here are the lines that I have in my fstab:
UUID=3253b05f-ce8f-4ea0-afb8-1bb212be1e45 /home/store/usb-store ext4 defaults,user 0 0


Anyone got a solution for this?Add one more option to the fstab line: noauto
>  UUID=3253b05f-ce8f-4ea0-afb8-1bb212be1e45 /home/store/usb-store ext4 defaults,user,[COLOR=Blue]noauto[/COLOR] 0 0

---

### Post by vanadium on 2010-12-25
"noauto" just won't automatically mount the drive. You need to mount it when logged in.
You probably want to use the "nofail" option.

---

### Post by dcstar on 2010-12-27
> **vanadium said:**
> "noauto" just won't automatically mount the drive. You need to mount it when logged in.
You probably want to use the "**nofail**" option.

Don't bet on it:

[https://bugs.launchpad.net/ubuntu/+source/mountall/+bug/610869](https://bugs.launchpad.net/ubuntu/+source/mountall/+bug/610869)

---

