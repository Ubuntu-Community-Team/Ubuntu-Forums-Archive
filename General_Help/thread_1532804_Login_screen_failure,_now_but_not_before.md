---
title: "Login screen failure, now but not before"
date: 2010-07-17
forum: General Help
---

### Post by Rallg on 2010-07-17
Not sure where to put this question. I am an experienced Ubuntu user, but not a guru. Using Ubuntu 10.04 on ASUS EEE 1005HA, 32-bit, with a pile of added software.

I had not experienced any problems until a couple of days ago. Then, I could not get to the login screen. Boot got as far as the nice purple background image, then stopped. Using CTRL+ALT+F1 I dropped to prompt, and attempted manual startx. This returned to the background image, but there was an intermittent cursor and no login screen.

I re-booted to rescue mode. There, I was told that there were file system problems, and I should run fsck manually. So I re-booted to the Ubuntu live CD, and ran fsck for my hard drive installation from there. The problems were located and fixed. A re-run of fsck showed no more problems.

However, re-boot to Ubuntu had the same problem as before: no login screen. Dropping to prompt then using startx also failed.

I did not see any messages that would help me narrow the problem. Re-booting to the earlier kernel did not help; same behavior.

Being sporting, I re-installed Ubuntu from the beginning, even re-formatting its partition. I also added some software that ought to be reliable. The new installation worked properly for a few boots. But then, for no apparent reason, it exhibited the same boot failure as before.

Has anyone else seen this lately? I don't normally have problems with Ubuntu, and nothing else on this dual-boot system suggests that the hard drive might be failing.

---

