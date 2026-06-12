---
title: "Ubuntu 9.04 x64 freezes"
date: 2009-07-13
forum: General Help
---

### Post by Lanrat on 2009-07-13
I have a fairly new install of Ubuntu 9.04 x64 that keeps freezing when I do various tasks. It never seems to be one application that makes it freeze. It does not seem to be a kernel panic as the caps lock light does not blink. (It just remains unresponsive)

I have looked over the logs but have not seen anything that looks like it could be a crash.

Can anyone help me figure out what might be causing this? I do know the time my computer crashes (The clock in the gnome bar)


Thanks.

---

### Post by miklcct on 2009-07-13
This is a known bug:
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/346691?comments=all](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/346691?comments=all)
The workaround is to install a newer kernel.

---

### Post by Lanrat on 2009-07-13
I installed the latest Kernel I could find (2.6.28-14) but I cant seem to be able to boot into it. It looks like it has only installed the source files and not the actual kernel. Where can I find the actual kernel that can fix this?

I am currently running 2.6.28-13, but also have 2.6.28-11 installed on my system.


Thanks for your response.

---

