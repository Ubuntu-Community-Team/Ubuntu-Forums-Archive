---
title: "Not possible to boot after hibernation"
date: 2010-02-12
forum: General Help
---

### Post by OxTubu on 2010-02-12
After hibernating my HP NC4200, a laptop which otherwise works like a charm with ubuntu (Karmic koala), I now can't restart ubuntu properly. I think that I closed the lid before hibernation was completed so when I boot, the computer look to a non-completed hibernation file.  

I got similar screens (which I cant show you since I cant take screen dumps) as in this thread (initramfs + busybox)

[http://ubuntuforums.org/showthread.php?t=765195&page=40](http://ubuntuforums.org/showthread.php?t=765195&page=40)

but the important difference from all I've read so far is that I DO NOT have dual boot in any way, and I'm not trying to install anything. I can boot from USB, but is simply to inexperienced to know how solve this problem. 

Please, what should I do, and what do you need to know in order to help me? :sad:


PS. I've spent the last 24 hours trying to find a solution to this problem by myself by reading several threads on this forum, but so far I've not been able to find anyone with THE same problem, nor a solution which has been described in a way suitable for a Ubuntu user only in his third month (thus I'm still a newbie, but don't recon that my problem is related to this). DS

---

### Post by OxTubu on 2010-02-17
Sooo,I am still stuck! 

After manually mounting according to several different sources I always encounter something like 

FATAL: Could not load /lib/modules

The support Ive found for this is over 5 years old, and thus doesn't apply to neither GRUB2, nor the current versions of initramfs. 

Any ideas? I've also tried several of the methods suggested in the wubi- and update-parts of the forum without any breakthrough.

This is now a bug, can be found on

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/523360](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/523360)

---

