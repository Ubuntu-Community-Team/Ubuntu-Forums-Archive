---
title: "Audio/Video Sync 100-200mS"
date: 2006-04-14
forum: General Help
---

### Post by skskarda on 2006-04-14
I have had MythTV install on Breezy and I recently updated to Dapper.   Whenever I watch HDTV, I have a 100-200mS delay in audio.  MythTV reports that it IS using realtime priority.  I have tried everything I can think of including:

Things I've tried on Dapper
-Ensuring that PAM 0.79 is installed and realtime limits set.
-Turned off the ESD.

Things I tried on Breezy (mostly from Ubuntu Studio website)
-Tried compiling a prememptive vanilla kernel.
-Tried realtime LSM stuff.
-Attempting unsuccessfully to compile realtime patched kernel with Ingo's patch.
-Upgraded Alsa to CVS.
-Tried on analog and digital.
-Tried to upgrade PAM (killed my machine, thus the upgrade to Dapper).

Any ideas on how to troubleshoot this problem?  I honestly don't know if it is in the recording, MythTv, or Playback.

My current setup.
Fusion Gold 5 HDTV card
Dapper
MythTV 0.19

Any help or guidance would be appreciated.

---

