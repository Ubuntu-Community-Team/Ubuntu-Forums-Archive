---
title: "What log file can I check to see why my machine sometimes freezes during boot?"
date: 2010-03-23
forum: General Help
---

### Post by sofakng on 2010-03-23
I've installed Ubuntu Server 9.10 x64 on my Acer Revo 1600 and 50% of the time it freezes during boot.

Grub appears to process successfully and I see an fsck message (looks normal), and then I see that the acer-wmi module is not supported on my system.

The system then freezes. If I press ctrl-alt-delete it will reboot (and I will see Ubuntu shutdown messages so it's still responding but SSHD never starts, I don't get a login prompt, etc).

The other 50% of the time, I still see the acer-wmi warning/message but then the system will still boot fine.

What log files can I check to see when a boot attempt fails/locks up?

---

### Post by doas777 on 2010-03-23
well, dmesg is usually a good boot log, and often important boot stuff ends up in xorg.0.log

the wmi error is probably not the cause here, if it works fine half the time but still produces that error.
hth

---

### Post by sofakng on 2010-03-23
Thanks for the reply.

Yeah, I don't think the acer-wmi message is the problem (because it does show-up even when it works).  I think it's just a warning telling me it tried to load but my machine is unsupported.

How can I check dmesg for a previous boot?  (eg. I have to reboot several times until it "randomly" works)

Also, is Xorg.log for XF86?  I'm using Ubuntu Server and XF86 is installed but it doesn't start automatically or anything like that.

---

### Post by doas777 on 2010-03-23
it's my understanding that dmesg.0 contains info about the previous boot. if your not using X then no, i imagine that that log will not be present or hold important info. 
I got into linux after the xfree thing, so, never worked with it.

---

