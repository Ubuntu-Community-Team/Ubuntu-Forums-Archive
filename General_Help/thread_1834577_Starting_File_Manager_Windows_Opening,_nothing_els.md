---
title: "Starting File Manager Windows Opening, nothing else works"
date: 2011-08-27
forum: General Help
---

### Post by hg6789 on 2011-08-27
Hi,

I have Ubuntu a three partition disk with one partition as Ubuntu which I mostly use. A few hours ago, when the system was idle, I moved my mouse but after some time also I was stuck on the black screen and there was no prompt for password. I finally powered it off after some time.

When powered on back, I found the following error:

mount: mounting /dev on /root/dev failed: No such file or directory
mount: mounting / sys/ on root/sys failed: No such file or directory
mount: mounting /proc on /root/proc failed: No such file or dirctory
Target filesystem doesn't have /sbin/init.
No init found. Try passing init= boot arg

BusyBox v1.10.2 (Ubuntu 1:1.10.2.2ubuntu7) built-in shell (ash)

(initramfs)

This was something regular, or at least a seen n solved thing. But further when I tried to boot with Live CD, I was hitting a strange issue. There is a window that says 'Starting File Manager' comes up, and then there are hundreds of such windows in a minute. Then they start disappearing, and then whatever I am trying to open (Terminal here, so that I can try something else) also gets closed.

Please help.

---

### Post by scott_g on 2011-08-29
If there's a problem with both the installed version, and live CD, it may be a hardware issue?  Have you tried starting up with either a) your hard drives unplugged to rule them out as an interference issue, or b) with a different live CD?

Scott

---

