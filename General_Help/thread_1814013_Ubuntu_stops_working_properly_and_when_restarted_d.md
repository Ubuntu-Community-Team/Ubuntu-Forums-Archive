---
title: "Ubuntu stops working properly and when restarted doesn't boot."
date: 2011-07-28
forum: General Help
---

### Post by buzboy123 on 2011-07-28
I have recently experienced a problem that occurred after an automatic update. After the update it said restart system. So I did and proceeded as  normal. when after the reboot Firefox suddenly stopped working, crashed and upon clicking it again only a blank box appeared. Then my other apps followed and i soon couldn't do anything so i shut down my computer. Upon restart I got a black screen with tons of text and something around the lines of 

mount: mounting /dev on /root/dev failed: No such file or directory
mount: mounting / sys/ on root/sys failed: No such file or directory
mount: mounting /proc on /root/proc failed: No such file or dirctory
Target filesystem doesn't have requested /sbin/init.
No init found. Try passing init= boot arg

So I rebooted and pressed shift to open that grub thing and booted  from an earlier kernel. This time it said checking HD for errors and after booted normally. Everything seemed fine but next day it did it again. Starting with Firefox crashing and then everything else. I again booted from a previous kernel and it worked but upon checking with uname -a it did not list the kernel i chose to boot from. So I decided to upgrade 10.04 to 10.10. This upgraded my kernel and deleted the old ones so i am hoping i am good now. Any idea what this was? How this happened? and if it will happen again?

---

### Post by lkjoel on 2011-07-28
> **buzboy123 said:**
> I have recently experienced a problem that occurred after an automatic update. After the update it said restart system. So I did and proceeded as  normal. when after the reboot Firefox suddenly stopped working, crashed and upon clicking it again only a blank box appeared. Then my other apps followed and i soon couldn't do anything so i shut down my computer. Upon restart I got a black screen with tons of text and something around the lines of 

mount: mounting /dev on /root/dev failed: No such file or directory
mount: mounting / sys/ on root/sys failed: No such file or directory
mount: mounting /proc on /root/proc failed: No such file or dirctory
Target filesystem doesn't have requested /sbin/init.
No init found. Try passing init= boot arg

So I rebooted and pressed shift to open that grub thing and booted  from an earlier kernel. This time it said checking HD for errors and after booted normally. Everything seemed fine but next day it did it again. Starting with Firefox crashing and then everything else. I again booted from a previous kernel and it worked but upon checking with uname -a it did not list the kernel i chose to boot from. So I decided to upgrade 10.04 to 10.10. This upgraded my kernel and deleted the old ones so i am hoping i am good now. Any idea what this was? How this happened? and if it will happen again?
I think that it is weird that it tried to mount /dev, /sys, and /proc in /root.
I think that it was just a (major) bug in the kernel.

---

