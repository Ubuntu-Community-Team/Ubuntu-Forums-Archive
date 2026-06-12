---
title: "Slow resume from hibernate"
date: 2010-05-03
forum: General Help
---

### Post by merike on 2010-05-03
I'm experiencing very slow resume from hibernation. Last one was nearly 3 minutes. Sure, there is 2GB of RAM to read from disk (no SSD) to memory but that long?

What could I check/do?

---

### Post by merike on 2010-05-05
Managed to run iotop while waiting for login dialog. Apparently Nepomuk was causing most of IO. After disabling that I'm down to slow (ca 90s) but more usable resume.

---

### Post by nortexoid on 2010-06-25
I've replaced the default hibernation utility with uswsusp and it works great now. I'm running Kubuntu 10.04. The default pm-utils suspend utility is fine, it's just the hibernate one.

It's used to take around 3 minutes to resume from hibernate, with s2disk (part of uswsusp) it now takes less than 20 seconds! To hibernate just run "sudo s2disk". To have it be the default (e.g. when you hibernate from Kickoff's menu) you need to edit the hibernate script.

Replace ALL the text in /usr/lib/hal/scripts/linux/hal-system-power-hibernate-linux with the following two lines:

#!/usr/bin/env bash
/usr/sbin/s2disk

You should first backup the file, of course.

Good luck!

---

### Post by merike on 2010-06-28
Indeed that seems to make a small difference to the better. But it also displays desktop before unlocking session and sometimes it fails to lock session completely.

What I've also found is that clean hibernate/resume with no programs is actually fast for me even with default hibernation script. What seems to happen is that my open programs steal the resources (mostly disk access) from login prompt. So while I'm still waiting for login prompt to appear I can already see wireless light blinking and after login my email is already fetched. It's just that I have no way to get logged in and change the active program.

What is unclear to me is if it's something wrong with Kubuntu giving resources to wrong programs too early in wakeup process or it's because Thunderbird is being more disk expensive on resume than it should be. The latter is likely at least half the cause because when I monitored with iotop then Thunderbird was the most disk-hungry program for about 20 seconds during resume.

---

### Post by adityavpratap on 2010-12-16
> **nortexoid said:**
> I've replaced the default hibernation utility with uswsusp and it works great now. I'm running Kubuntu 10.04. The default pm-utils suspend utility is fine, it's just the hibernate one.

It's used to take around 3 minutes to resume from hibernate, with s2disk (part of uswsusp) it now takes less than 20 seconds! To hibernate just run "sudo s2disk". To have it be the default (e.g. when you hibernate from Kickoff's menu) you need to edit the hibernate script.

Replace ALL the text in /usr/lib/hal/scripts/linux/hal-system-power-hibernate-linux with the following two lines:

#!/usr/bin/env bash
/usr/sbin/s2disk

You should first backup the file, of course.

Good luck!

Hi,
Thank you for you useful tip. I found that hibernate/resume process has become very fast when I use s2disk.
However, I do not find hal-system-power-hibernate-linux on my Ubuntu 10.10 install. Any idea where the hibernate script located?

---

