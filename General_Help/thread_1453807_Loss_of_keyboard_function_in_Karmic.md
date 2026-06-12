---
title: "Loss of keyboard function in Karmic"
date: 2010-04-13
forum: General Help
---

### Post by akuthor on 2010-04-13
I've used ubuntu for years now and had numerous problems (usually with upgrades) all of which I've been able to overcome (and learn something interesting in the process); this new one, however, has me stuck.  I'm sure I'm just missing something simple.

I'm running 64-bit ubuntu on an Dell XPS M1730: this may not be relevant but since it was a major factor during my last serious problem, I figure it might still be related.

I recently upgraded to 9.10 (late, I know, but I had such a hard time with the upgrade to 9.04, that I was reluctant to do this one).  The upgrade process did terminate unexpectedly with a warning that something could not be completed and my system might be unstable.  That was two weeks ago, and everything has been running (just fine) for some time.

A package update 4 or 5 days ago failed with the message that rsyslog could not be configured (and therefore neither could ubuntu-minimal which depends upon it).  Everything seemed OK except for that recurrent message anytime a package manager ran.

2 days ago several a couple of different programs began reporting that my X server didn't support utf-8 or some similar messages when they were started.

As of yesterday any time I logged into an Xsession I recieved a dialog warning that XKB wasn't functioning properly and there might be a library issue.

And finally today, I tried to boot Matlab and received an error about desktop compatibility so I rebooted; upon reboot all keyboard input had stopped responding at the login screen.

I've spent quite a bit of time now booting to terminal and checking various packages and everything is installed and configured (except for rsyslog and ubuntu-minimal).

Anyone have an idea what's going on?

---

