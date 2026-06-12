---
title: "TD Ameritrade Control Center Java freeze (Lucid)"
date: 2010-06-18
forum: General Help
---

### Post by Mr_Bumpy on 2010-06-18
Under Lucid, the TD Ameritrade Control Center 2.0 freezes when going into the streamer settings (clicking on the little wrench icon in the main streamer window).  The settings window begins to appear, but is only partially drawn (no text), then it freezes up so badly that the system monitor cannot kill the task.  Other applications can be used and closed, but the Java app will just sit there frozen until the system is rebooted.  The settings window worked fine under Karmic.

I am using sun-java6 (I had to uninstall icedtea & openjdk since the streamer doesn't work properly with openjdk).

Running Firefox from the terminal, the only error message I get is a flood of "(firefox-bin:6030): Gdk-WARNING **: XID collision, trouble ahead" messages repeated in the terminal, although from my research, I don't believe this has anything to do with the Java freeze problem.

What further steps can I take to troubleshoot this?  I have no idea what all has changed between Karmic and Lucid that could be causing the problem.

I have reproduced this on two systems so far, but I am limited in testing, since I don't have a TD Ameritrade account--I am trying to solve this problem for a friend.

---

