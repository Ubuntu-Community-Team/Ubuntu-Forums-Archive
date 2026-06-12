---
title: "Complete system freezes (Like kernel panic) Need help finding the cause"
date: 2012-05-21
forum: General Help
---

### Post by J V on 2012-05-21
I overclocked my Ivy Bridge 3570k to 4.6 Ghz, with a vcore of 1.290. It passed a 12 hour mprime torture test (Windows users know it as prime95) so I don't think this is the cause of the following problem.

Since then I've had occasional freezes: The image on screen freezes and whatever sound byte was playing in the last second or so loops indefinitely.

SysReq REISUB does nothing, and sometimes the reset button doesn't even work and I need to hold the power button to reboot.

Unlike when I knew the system was unstable, these freezes give no kernel panic error message, and I've since upped the vcore to 1.315 to no avail (Right now it should be stable at 4.7 Ghz never mind 4.6)

I would assume this is a kernel panic but there is no syslog available of the last boot (Presumably syslog.0? If it was syslog.1 there are some acpi notices but they're several minutes before the crash) I must assume something else is causing it.

Either I have faulty hardware or faulty sofware (The Nvidia proprietary drivers v295.49 being the only likely culprit)

I need help diagnosing the problem because I've never had regular full system lockups on linux before. Help!

**Edit: **My bad, didn't stress test properly

---

