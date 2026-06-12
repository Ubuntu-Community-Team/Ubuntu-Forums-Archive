---
title: "Mouse does not work on Ubuntu 10.04 &amp; 10.10"
date: 2010-09-04
forum: General Help
---

### Post by pmalvr on 2010-09-04
Hello,

I had Ubuntu 9.10 on my second PC working great. After the upgrade to version 10.04 my mouse stopped working. Even with Ubuntu 10.10 beta it freezes after login. I also noticed that after some reboots, sometimes the mouse works, but then, it is the keyboard that stops working.

P.S: With Fedora 14 alpha I can use the mouse without problems (It wasn't working also with Fedora 13)

Can someone help me with this issue?

Thanks

---

### Post by pmalvr on 2010-09-04
> **pmalvr said:**
> Hello,

I had Ubuntu 9.10 on my second PC working great. After the upgrade to version 10.04 my mouse stopped working. Even with Ubuntu 10.10 beta it freezes after login. I also noticed that after some reboots, sometimes the mouse works, but then, it is the keyboard that stops working.

P.S: With Fedora 14 alpha I can use the mouse without problems (It wasn't working also with Fedora 13)

Can someone help me with this issue?

Thanks


Well,

After a long search I made, I found a workaround that for now does the job.

Here it is:

Edit **/etc/default/grub**, go to the line that begins like:
**GRUB_CMDLINE_LINUX_DEFAULT=**

Change it to:
**GRUB_CMDLINE_LINUX_DEFAULT="quiet splash acpi=off"**

After that, run this command:
**sudo update-grub** 

**Reboot** and that's it. 

The only thing I noticed is that the PC doesn't shutdown by itself completely, I have to press the button to shut it down.

I hope this bug can became fixed in the next builds.

---

