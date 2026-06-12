---
title: "Youtube problem."
date: 2010-01-24
forum: General Help
---

### Post by connorh123 on 2010-01-24
Hey guys.
I usually don't post here, unless I really have a problem. And I do.
I installed about 127 updates in update manager and it might have started this problem. I tried to check out a Youtube video and it said something about I don't have the latest Adobe version, even though it worked the other day. I'm using Google chrome beta, not Mozilla Firefox.
So my question is:
What should I do to fix this problem. I can't update the latest version of Adobe, because it only applies to Mozilla, not Google Chrome. Plus Mozilla is slow enough anyway that's why I use Google Chrome. HELP!

---

### Post by Jackzor on 2010-01-24
Um..Reinstall chrome and the plugin in the Synaptic manager. This worked for me.

---

### Post by mikewhatever on 2010-01-24
> **connorh123 said:**
> Hey guys.
I usually don't post here, unless I really have a problem. And I do.
I installed about 127 updates in update manager and it might have started this problem. I tried to check out a Youtube video and it said something about I don't have the latest Adobe version, even though it worked the other day. I'm using Google chrome beta, not Mozilla Firefox.
So my question is:
What should I do to fix this problem. I can't update the latest version of Adobe, because it only applies to Mozilla, not Google Chrome. Plus Mozilla is slow enough anyway that's why I use Google Chrome. HELP!

What version of Ubuntu are you running?
If installed from the repositories, flash should work on any browser, including Chrome. Can you post the output of the following command to verify what version of flash is installed:

dpkg -l | grep flash

---

### Post by connorh123 on 2010-01-25
I'm running 9.04.
I got this when I typed that code in:
connor@connor-laptop:~$ dpkg -l | grep flash
ii  flashplugin-installer                      10.0.42.34ubuntu0.9.04.1                Adobe Flash Player plugin installer
ii  flashplugin-nonfree                        10.0.42.34ubuntu0.9.04.1                Adobe Flash Player plugin installer (transit
connor@connor-laptop:~$

---

### Post by connorh123 on 2010-01-26
> **Jackzor said:**
> Um..Reinstall chrome and the plugin in the Synaptic manager. This worked for me.
Bump.
I re-installed chrome, and the plugin for synaptic is already  there. Still, no sound. Anybody else please?

---

### Post by connorh123 on 2010-01-27
> **alexevans said:**
> I guess you should completely remove adobe flash and chrome thru synaptic package manager and then reinstall both.
Thanks! This worked!
If a moderator would mark this as solved, that would be greatly appreciated.

---

