---
title: "Resume From Suspend on ThinkPad X220 Spotty &amp; Strange!"
date: 2011-12-29
forum: General Help
---

### Post by steevven1 on 2011-12-29
When I suspend either of my two ThinkPad X220's under Xubuntu, they fail to properly wake up about 1 in 15-25 times. What happens is very strange though, and I believe that it sheds light on the problem, which I need some help deciphering:

When I open the lid after suspend and it fails to wake up, I get an LCD with a black screen (powered on, backlight on, but nothing displayed). However, the computer operates 100% normally. That is, I can type my password to unlock the screensaver that SHOULD be displayed, hit return, then start typing commands (I always have a Terminal open), and they happen! For example, I can type "sudo reboot" followed by my password, and the computer reboots!

Any suggestions?

---

### Post by pretty_whistle on 2011-12-29
What you did by putting in the password to reach the desktop IS the workaround.  This is a bug they're working on.  I didn't save the link to it though.

If I can find the bug report I'll post it.

---

### Post by steevven1 on 2011-12-29
> **pretty_whistle said:**
> What you did by putting in the password to reach the desktop IS the workaround.  This is a bug they're working on.  I didn't save the link to it though.

If I can find the bug report I'll post it.

I'm not sure how that's really a workaround...It doesn't bring my screen back without rebooting. Doing SysRq + REISUB is equally good (but still awful). Please do post a link to a bug report if you have it. Thanks!

---

### Post by steevven1 on 2011-12-30
Can anyone else chime in on this? Thanks.

---

### Post by steevven1 on 2012-01-12
I have filed a bug here: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/915730](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/915730)

---

