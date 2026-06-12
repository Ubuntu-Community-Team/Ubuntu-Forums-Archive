---
title: "Can't connect with UltraVNC Viewer after upgrade."
date: 2009-09-20
forum: General Help
---

### Post by KillrBuckeye on 2009-09-20
I upgraded from 6.06 to 8.04 yesterday (not a fresh install).  Before the upgrade, I could connect to my Ubuntu machine from my Windows machines using UltraVNC Viewer without any problems.  However, now that I have upgraded Ubuntu to 8.04 it is no longer working.  I get the following message in UltraVNC Viewer on the Windows machine:

Connection failed - Error reading Protocal Version
Possible causes:
-You've forgotten to select a DSMPlugin and the Server uses a DSMPlugin
-Viewer and Server are not compatible (they use different RFB protocols)
-Bad connection


Meanwhile, I can still connect using PuTTY over SSH.  What has changed with the upgrade that could be causing the problem?  I have tried to follow a couple guides for setting up VNC, but they have not helped.

---

### Post by PerfectReign on 2009-09-20
I don't know 8.04 very well (just started with 9.04) but in general, you can assume that there are firewall rules in place which most likely will prohibit vnc (port 5900?) connections unless you explicitly allow them.

My initial reaction is that there are firewall rules in 8.x that weren't present in 6.x maybe.

Here: [http://ubuntuforums.org/showthread.php?t=795036](http://ubuntuforums.org/showthread.php?t=795036)

---

### Post by KillrBuckeye on 2009-09-20
> **PerfectReign said:**
> I don't know 8.04 very well (just started with 9.04) but in general, you can assume that there are firewall rules in place which most likely will prohibit vnc (port 5900?) connections unless you explicitly allow them.

My initial reaction is that there are firewall rules in 8.x that weren't present in 6.x maybe.

Here: [http://ubuntuforums.org/showthread.php?t=795036](http://ubuntuforums.org/showthread.php?t=795036)
Got it working with the guide you linked!  Thank you so much.

---

