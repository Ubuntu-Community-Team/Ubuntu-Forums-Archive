---
title: "Help diagnosing random crashes in 10.10"
date: 2010-10-26
forum: General Help
---

### Post by hipnerd on 2010-10-26
I recently bought a new machine for the first time in five years or so -- a Gateway Athlon IIx4 core box with 4G of RAM.

I removed Windows and installed 10.04. Things worked pretty well. A week later or so, 10.10 came out and I upgraded. It crashed in the middle of the upgrade, but I was able to recover. 

Since then the system has been wildly unstable. I tried reformatting/reinstalling the 64-bit version of Meerkat, but I experienced frequent hang-ups and crashes out of the box. I was rebooting multiple times a day and it was getting progressively worse. I reformatted, repartitioned and installed the 32-bit version of Meerkat. 

It's more stable than the 64-bit version, but Firefox was crashing on me within an hour and the PC locked up on me multiple times.

This has never been my experience with Ubuntu. My previous two boxes were "homemade" with the cheapest parts Fry's had to offer and they were rock solid. 

So what can I do to diagnose this? If it is the computer itself, I want to return it. So I figure I can run a memory test and um. Well that's all I've thought of to do. Is there any other useful diagnostic I can run?

---

### Post by k999 on 2010-10-26
Back in the day, compiling the kernel was a great way to stress a system. It could cause hangs on computers that otherwise seemed to work ok. Maybe you should give that a go, and if it hangs regularly, it's probably some hardware issue. Not exactly a precise science, I know...

Run memtest first. And look in your logs (dmesg, /var/log/messages, /var/log/syslog) for weird messages.

---

