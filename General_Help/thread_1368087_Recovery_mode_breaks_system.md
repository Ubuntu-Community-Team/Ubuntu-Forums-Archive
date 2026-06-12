---
title: "Recovery mode breaks system"
date: 2009-12-30
forum: General Help
---

### Post by peterdm on 2009-12-30
Linux kampala 2.6.31-16-generic #53-Ubuntu SMP Tue Dec 8 04:01:29 UTC 2009 i686 GNU/Linux

Hi,

After having gone into recovery mode once, the system is broken. When I say broken I mean
[LIST]
[*]runlevel is unknown
[*]some services not running (cups etc.)
[*]multi-user not working (CTRL-ALT-F1 etc.)
[/LIST]

I was trying to help a friend with the exact same system as mine, at first we didn't realize the recovery mode actually caused the problem. This is the way to reproduce it:

[LIST=1]
[*]start from a sane system, check that the runlevel is "N 2"
[*]reboot in recovery mode
[*]recovery mode gets stuck for some reason (in my case: after/when trying to start NTP, in my friend's case for another reason)
[*]Reboot again by doing CTRL-ALT-DEL (remember there is no recovery prompt at this point since recovery mode got stuck)
[*]let the system start, check the runlevel, it is unknown!
[*]apparently the system failed to enter runlevel 2 (even though X started fine)
[/LIST]

The workaround is to manually enter

```
sudo telinit 2
```

after every reboot, but there seems to be something seriously wrong here. We've been skimming the web looking for solutions all day but found nothing.

Any help or suggestions please?

Peter

---

