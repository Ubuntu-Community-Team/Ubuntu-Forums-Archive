---
title: "Why does Ubuntu 11.10 run an FSCK on every boot?"
date: 2011-12-29
forum: General Help
---

### Post by CoolBreeze47 on 2011-12-29
Hi everyone

Using the Ubuntu 11.10 alternate CD, I set up a LUKS encrypted LVM with  the home and swap folders encrypted as well. I've done this many times  and never had any issues.

However, with the last 4-5 installs I've found it necessary to run sudo  touch /forcefsck due to the system freezing during an update. I just  wanted to force a system check on the next reboot to make sure  everything was ok since I had to shut my PC down manually.

In doing this however, now each time I boot, the system runs an FSCK (rather than every 30 days like it's supposed to).

Is there any relatively easy way I can resolve this?.

Thanks so much for any help, CB

---

### Post by guestolo on 2011-12-29
"sudo  touch /forcefsck"
should of created an empty file in the root file system as
/forcefsck

Maybe that file is not being deleted on bootup?

---

### Post by CoolBreeze47 on 2011-12-30
Hi

Just wanted to say thanks!. I had no idea that file was there. Deleted it and then rebooted and all was well :)

- CB

---

### Post by dcstar on 2011-12-30
> **guestolo said:**
> "sudo  touch /forcefsck"
should of created an empty file in the root file system as
/forcefsck

Maybe that file is not being deleted on bootup?

Possibly the encryption is not allowing writes to the "/" folder until further along the boot process so the early fsck can never delete that file?

This should really be reported as a bug.

---

### Post by CoolBreeze47 on 2011-12-30
Good point. You know, I thought about that myself. With an unencrypted setup this would have been a complete non-issue.

My desktop boots up now without running an FSCK each time but the other thing I've noticed is that I'm not getting that "wait..." message while the drive partitions are being decrypted. Kind of strange but at least it's not running FSCK on each boot and it seems a little faster.

- CB

---

