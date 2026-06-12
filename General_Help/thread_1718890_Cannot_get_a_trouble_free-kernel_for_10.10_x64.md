---
title: "Cannot get a trouble free-kernel for 10.10 x64"
date: 2011-04-01
forum: General Help
---

### Post by Veazer on 2011-04-01
I've been having problems with the 2.6.35.x kernels where the system occasionally becomes very sluggish and unresponsive despite showing low cpu usage. Running top shows several instances of kslowd00x (kslowd001, kslowd002, etc) and everything on the screen updates at about 5 frames per second and behaves very choppy (turning compiz off does not effect the problem) This issue has been described by others here:
[http://ubuntuforums.org/showthread.php?t=1594239]("http://ubuntuforums.org/showthread.php?t=1594239")

I tried upgrading to later kernels 2.6.36+ but the problem is still there. I even tried the 2.6.38 natty kernel which performs much better in general but still has the issue under a different process name: kworker  This issues has been described in this thread:
[http://forums.gentoo.org/viewtopic-p-6545191.html]("http://forums.gentoo.org/viewtopic-p-6545191.html")

Some user from that thread seem to think that people with this problem should stick to pre 2.6.35+ kernels but when I do that I get another issue. After a 5-10 minutes of uptime, i noticed that udevd is using ~50% of cpu time and the system starts warming up, but never becomes nearly as sluggish as the later kernels. I've tried updating udevd, no effect. I've tried 'killall udevd' and it restarts immediately at the same cpu usage. This issue is described here:
[http://ubuntuforums.org/showthread.php?t=450206]("http://ubuntuforums.org/showthread.php?t=450206")

I'm really feeling stuck now, each bootup I stare at grub and decide which issue i feel like dealing with that day. Any suggestions?

Machine is Asus U20a  (Intel SU7300 / 4500MHD)

---

