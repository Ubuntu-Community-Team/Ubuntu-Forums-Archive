---
title: "Ubuntu crashing randomly (related to xrdp?)"
date: 2012-03-01
forum: General Help
---

### Post by Only1KW on 2012-03-01
I'm currently having an issue where Ubuntu 11.10 is crashing on me at what appeared to be random times (when I wasn't using the system at all).  By crash I mean that I cannot interact with my desktop, cannot switch to a different terminal (including text-based terminals), my network connection dies and cannot be pinged, hitting Caps Lock on the keyboard no longer causes the Caps Lock light on my keyboard to light up, etc.  In short, system is unusable without a hard power down and power back on.  I just installed Ubuntu for the first time about a week ago, and performed my last clean install (hoping that would fix my problem) yesterday morning.

I've been following the steps at [https://help.ubuntu.com/community/DebuggingSystemCrash](https://help.ubuntu.com/community/DebuggingSystemCrash) and can say that a few passes of memtest86 all complete successfully.  I also got the following text printed into /var/log/syslog at or shortly before the last crash:

Mar  1 16:43:43 ayla kernel: [10725.503284] composite sync not supported
Mar  1 16:43:43 ayla kernel: [10725.503296] composite sync not supported
Mar  1 16:43:43 ayla kernel: [10725.503303] composite sync not supported

I *think* at this point that it is crashing once (1) I connect to the console using x11vnc via xrdp and (2) the GUI console screen locks and the physical monitor power saving kicks in (both things in (2) appear to occur simultaneously).  Just connecting to the GUI from the physical terminal and letting (2) occur does not cause the issue.  I have yet to try connecting to the console GUI via a vanilla VNC client.

Any ideas on how to fix this or where to look for additional information?  A Google search didn't seem to find anyone else hitting this same issue.

---

