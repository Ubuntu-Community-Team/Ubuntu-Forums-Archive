---
title: "After crash, can't restart firefox"
date: 2010-01-29
forum: General Help
---

### Post by jmerkin on 2010-01-29
This has happened multiple times. I'd be running firefox and it would crash for whatever reason. I'd try to restart it and it would tell me that it's "already running as another process." 

ps and top show no firefox. killall can't kill it. I found a few forum postings saying to delete the .parentlock file in the firefox directory. That allows me to start it, but all my personalizations and settings are gone. I have to each time create a new profile and copy everything over.

Kubuntu 9.04, all up to date, 2.6.28-13, 64-bit.

Any thoughts?

---

### Post by raktarok on 2010-01-29
Maybe some extension/plugin in causing firefox to crash? Try starting firefox in safemode and see if it still crashes,

```
firefox -safe-mode

```
Also, does it crash when you open a specific webpage? Have you noticed any patterns?

---

### Post by lidex on 2010-01-29
What version of Firefox is this? Did you install from a repository or a download from Mozilla? I would agree with raktarok, probably something in your profile. Since you are copying everything over from your old profile it would make sense that the problem persists. I would rename the default profile and move it just to be certain, then uninstall Firefox completely. Now re-install and try it with the new default profile. If that works OK, then start adding extensions one-at-a-time until it borks. Then you'll know the culprit.

Firefox help:
[http://ubuntuforums.org/showthread.php?t=1193567]("http://ubuntuforums.org/showthread.php?t=1193567")

Profiles:
[http://kb.mozillazine.org/Profile_Manager]("http://kb.mozillazine.org/Profile_Manager")
and here:
[http://support.mozilla.com/en-US/kb/Profiles]("http://support.mozilla.com/en-US/kb/Profiles")

---

