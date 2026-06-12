---
title: "Problem with kernel upgrade to 2.6.32-30"
date: 2011-03-18
forum: General Help
---

### Post by lesliek on 2011-03-18
I'm using Ubuntu 10.04 with Windows 7 via Wubi.

Until yesterday, my kernel was 2.6.32-29.

Yesterday, I was offered 2.6.32-30 by the update manager and accepted it.

However, I can't boot up using that kernel. I get no video. (I'm now choosing -29 at bootup instead of -30. It still works.)

What should I be trying in order to get -30 to work?

Thank you,

Leslie

---

### Post by antaios256 on 2011-03-18
if you are using Nvidia the drivers just need to be reinstalled

---

### Post by lesliek on 2011-03-18
Thanks for replying, antaios256.

It's not that. I'm using ATI and the radeon driver.

Thanks again,

Leslie

---

### Post by foolofatook on 2011-03-19
I think I'm seeing a similar problem. I'm still trying to figure out what's going on, but it looked to me like when I booted 2.6.32-30, no kernel modules loaded. I looked into it a bit, and it appeared that "uname -r" was returning "2.6.32-28" while the 2.6.32-30 was running, which may result in the kernel looking the wrong place for modules.

This happened on one of my computers I upgraded today. On the other one, I had no problems and 2.6.32-30 is running fine, "uname -r" works, etc.

---

### Post by foolofatook on 2011-03-19
I'm still not 100% what happened, but my problem with this new kernel seems to have been resolved with:

  sudo dpkg-reconfigure linux-image-2.6.32-30-generic

After doing this, modules load correctly when I boot into this kernel.

---

### Post by lesliek on 2011-03-19
Thanks for your replies, foolof atook.

Sorry to be so ignorant, but will I run the dpkg-reconfigure command you mentioned while booted up using 2.6.32-29?

Thanks again,

Leslie

---

