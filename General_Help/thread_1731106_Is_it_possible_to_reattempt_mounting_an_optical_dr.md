---
title: "Is it possible to reattempt mounting an optical drive without ejecting it?"
date: 2011-04-16
forum: General Help
---

### Post by jwbrase on 2011-04-16
I've got either a laptop with a flaky DVD drive, a flaky DVD, or both. I'm running a Lucid install upgraded from Jaunty. When all goes well the DVD will mount at boot (if already in the drive), or when it is inserted (if not). Otherwise, the drive will spin up to try to read the disk, fail, and stop.

At this point, if I try to use mount to mount the disk, it will pause for a second and respond with "mount: no medium found on /dev/sr0", without spinning the disk up for another read attempt (apparently it just remembers that it didn't find any medium in the drive when the tray was closed and doesn't attempt to check when mount is used afterwards). As a result, I have to open and close the drive tray for each retry.

I'd like to figure out a way to force the system to spinup and recheck the drive from the command line. That way I could write a shell script that would implement the following pseudocode:

```
while notMounted
forceMediumRecheck
mount /dev/sr0
```

Is there any way to do this, either in terms of a command other than mount that can be used to force a recheck of the DVD drive or else a configuration option in some file somewhere that will cause the system to do this automatically when an attempt is made to mount an optical drive?

---

