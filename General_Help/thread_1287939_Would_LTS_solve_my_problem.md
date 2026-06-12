---
title: "Would LTS solve my problem?"
date: 2009-10-10
forum: General Help
---

### Post by frito on 2009-10-10
I have all these problems with Ubuntu. Hardware keeps screwing up and it annoys me. (1 of many examples, I cant use my ath5k wifi adapter and nvidia-current, my wifi stops working... wierd). 

Would switching to the LTS release solve (or possibly solve) these hardware problems? Or does it not really have anything to do with hardware releases?

What about jumping straight to debian? they are both on slower debian trees.

---

### Post by ad_267 on 2009-10-10
No it wouldn't (well probably not).

You would be better off switching to the beta release of Ubuntu 9.10 which may have better support for your hardware. Using an older LTS release would mean you're using an older Linux kernel with older hardware drivers.

LTS has nothing to do with how well it supports hardware, it just means its supported by Canonical for longer so you don't have to upgrade often and is more suitable for businesses.

---

### Post by Iowan on 2009-10-10
Which version are you using that is causing problems?

---

### Post by frito on 2009-10-10
Upto date Kubuntu. :S
You dont  thinking having a less bleeding edge kernel would be good? Do older kernels generally have more bugs? 
My hardware is hardly new... it just doesnt work.

---

### Post by NFblaze on 2009-10-10
Always, download and install the latest release. That's what helped me. I started with 8.04 and had a new laptop that wasnt supported. The next release it was better, and more functional I didnt have a problem really. Then 9.04 actually kinda messed up my standby/hibernate. Though now 9.10 has everything working except for my standby (although, its improved). Seems to get better each release.

---

### Post by wilee-nilee on 2009-10-10
have you used a version of Ubuntu that worked for you? I suspect Karmic isn't working because of it is in development. I had wireless problems with Karmic but I just installed a 9/03 daily live Iso and switched to wicd before updating and the problems I am having are some desktop graphics.

---

### Post by 3rdalbum on 2009-10-10
If you have an Atheros card, then you definitely don't want Ubuntu 8.04.

Try installing the 9.10 beta, it's really good. I wasn't having any problems on Jaunty either, but 9.10 may solve your problems. Just make sure you apply all the updates ASAP.

---

### Post by frito on 2009-10-11
ok point taken, update. 
As a note though as I dislike issues (like everyone) and would sacrifice cutting edge packages to get away from them, so maybe I'll stick with the next LTS once it comes out... if i have no issues.
Are there any issues with just not upgrading my ubuntu for a long time? Say 1yr?

---

### Post by ad_267 on 2009-10-11
> **frito said:**
> Are there any issues with just not upgrading my ubuntu for a long time? Say 1yr?

No, as long as you still install important security updates then everything should be fine.

---

### Post by frito on 2009-10-11
how do i differentiate between security updates and non?
If I did that it would effectively make whatever version i start from an LTS version wouldn't it. I would just be piggybacking on the LTS security updates.

I suppose I would have to switch repositories. :S?

---

### Post by t0p on 2009-10-11
> **frito said:**
> how do i differentiate between security updates and non?

Security updates are labelled "Security updates" in the Update Manager.  Other updates are labelled "Other updates.

> **frito said:**
> 
If I did that it would effectively make whatever version i start from an LTS version wouldn't it. I would just be piggybacking on the LTS security updates.

I suppose I would have to switch repositories. :S?

Sorry, you've lost me there.  LTS is LTS.  Non-LTS is non-LTS.

Incidentally, I've been running 8.04, the last LTS, since its release, on my desktop machine, and it has not given me any trouble for a long while now.  It's noticeably older than Jaunty on my other computer.  But I can always depend on it.

---

### Post by frito on 2009-10-11
> Sorry, you've lost me there. LTS is LTS. Non-LTS is non-LTS.

I assumed LTS was just a different repository... you install the 8.04 build and use a different repository to update.

---

### Post by aysiu on 2009-10-11
LTS is good if you want to use the same release for a long period of time.

Non-LTS is good if you want the latest improvements in Ubuntu (which often includes hardware configuration, though there are occasionally regressions).

Try the Karmic beta .iso as a live CD and see if it detects your hardware well. If it does, upgrade to Karmic. Just keep in mind that it's still in beta so daily updates probably won't but still could break your system.

---

### Post by ad_267 on 2009-10-12
All Ubuntu releases receive security updates for a reasonable amount of time. After a new version is released, old versions are still supported but they only receive security updates, they don't get new versions of any applications.

---

