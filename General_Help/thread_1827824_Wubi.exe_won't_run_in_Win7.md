---
title: "Wubi.exe won't run in Win7"
date: 2011-08-18
forum: General Help
---

### Post by DownrangeFuture on 2011-08-18
So, I searched around here and didn't see a solution. Although, I'm slowly coming to the conclusion that I'm just SOL. I found some HDDs while we were moving and so I popped them in my computer to see if they worked. The 250GB was DOA, but my 500GB drive scanned and ran fine. Although windows complained about a non-member disk installed (I have a serialATA RAID0), it ran the tests on it okay and they came back clean.

I decided that I'd use wubi to install it on my extra disk then. Wubi had a Crash to Desktop right after it started. I can open task manager and watch the wubi process start and then end. No errors thrown at all.
 
Well, no harm, no foul, I just rebooted and tried to install Ubuntu from the CD. It tells me that it can't mount partition #5 for some reason. If I continue the install and look at the thrown errors it's getting some kind of link fail when it tries to access /dev/sdc. Then it sits there for awhile and reboots. It does the same thing with my 500GB USB drive since my comuter can boot from a removable device. Except it can't access /dev/ext/hd1.

I'm not entirely sure what that's all about, although I think it might be related to the RAID setup. Maybe the controller can't handle that kind of setup? (ASUS HDP55D PRO) It's my first RAID setup, so maybe none of them can?
 
Anyway, so I tried fooling around with Wubi again. I'm having trouble locating my Win7 disk (and the corresponding license #) and while I've never had a partition move screw any data, I just want to make sure first. Ya know? If I could at least get my license number then I'd just break the RAID and split up the 2 HDD in the RAID for my various OS installs. RAID0 with 2 disks doesn't seem to make much of a difference in performance anyway.

But if I can't, what's up with wubi?

---

### Post by DownrangeFuture on 2011-08-18
Well, so I found a key finder that should extract the Win7 key. I'll do that when I get home.

Still there's something going on with Wubi, and I'd like to know what you guys need so hopefully you can replicate it.

---

### Post by bcbc on 2011-08-18
Do you have python installed? Removing python path from the environment variables is a Wubi solution if you do (symptom is that wubi doesn't run, no message, no log file).

as far as Raid0, there was someone recently who had issues with that (although that was installing wubi on raid0 and you're trying to install on the other drive). 
[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/828330](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/828330)

---

