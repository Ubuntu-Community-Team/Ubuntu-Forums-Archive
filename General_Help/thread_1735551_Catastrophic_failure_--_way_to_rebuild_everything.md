---
title: "Catastrophic failure -- way to rebuild everything?"
date: 2011-04-21
forum: General Help
---

### Post by djgLXXII on 2011-04-21
I *think* my primary hard disk is failing because yesterday my system started acting really odd, I had to force a reboot and now some system files appear to be damaged (python being one of them).

I can't log into the desktop environment (XFCE4 login has no selectable user name)...but I can drop to a command prompt.

I attempted to run apt-get update and upgrade, but it fails half way through the upgrade process. I'm not at the PC at the moment to relay any error messages, but my question is, is there a feature in apt-get (or some other utility) that will attempt to rebuild/refetch _every_ file in the system?  I have a feeling if I go on a long chase to fix one file there will just be another waiting to pop up that has a problem.

Normally I would just say screw it and reload the system fresh.  But since 11.04 is due out next week, I'm okay with limping along until it's release.

Thanks for any suggestions.

P.S. Additionally, how do I run a full sector scan on the hard disk to mark any bad sectors?  And is there a way to see if there ARE bad sectors?  I am making the assumption that the drive is failing as I see no other way how root-only access files could get corrupted.

---

### Post by samacaster on 2011-04-21
Can you access the disk utility? If you can you could run a SMART scan of the drive and it will tell you if there are bad sectors. Even if there are bad sectors all OS's will find and try to move things off of those sectors and will not save anything to them, essentially marking them as bad.

If your really OK with limping along, I would ASAP get everything you want to save off of the system. Somewhere along the way your system files seem to have been toyed with. It does happen from time to time.

---

### Post by bodhi.zazen on 2011-04-21
Boot a live CD and run fsck ;)

---

### Post by Mark Phelps on 2011-04-22
> **djgLXXII said:**
> But since 11.04 is due out next week, I'm okay with limping along until it's release.

Don't be in a rush to jump into 11.04.  The list below is the current set of issues:

[http://www.ubuntu.com/testing/natty/beta#Known%20issues]("http://www.ubuntu.com/testing/natty/beta#Known%20issues")

Best course of action is to wait a couple of months after a new release, monitor the forums for release-related issues, and only THEN do an upgrade.

A version upgrade is only one-way.  If you run into serious problems afterward, there is no simple way to restore your current working version.  You have to wipe and reinstall from scratch.

---

