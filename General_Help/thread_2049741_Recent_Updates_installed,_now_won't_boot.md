---
title: "Recent Updates installed, now won't boot"
date: 2012-08-29
forum: General Help
---

### Post by Ditchdoc7893 on 2012-08-29
Hello all.

Tonight I received a message that I needed to install updates. This was via the Update Manager. No big deal, right? Well, I did the updates, no worries to that point. While the updates didn't specifically require a restart, I had some school work to do that had to be completed in Windows, so I rebooted to go into Windows. Still no problems. Later, I tried boot back into Ubuntu and after I selected the appropriate selection in GRUB to enter Ubuntu. All I got was a blank screen. After thinking about those updates, I remembered that there was an NVIDIA update. I have a sneaking suspicion that it is the culprit for these problems. Can anyone guide me through how to correct this problem? I'm thinking possibly remove whatever NVIDIA update this was. A little background on this system...it has multiple hard drives that I could easily set up to run another installation. It has one 2 TB  hard drive that is allocated for only Windows, plus another 2 TB drive that Ubuntu is on, and a few others with mostly just media files on them. Any help is appreciated!

---

### Post by CrusaderAD on 2012-08-29
Try popping the nvidia card out if you can and boot without it. See if you can get back in that way.

---

### Post by Ditchdoc7893 on 2012-08-30
This might be a dumb question, but if I pop the video card out and have no screen to look at, how am I going to know if it booted or not. This machine does not have onboard video on the Mobo.

---

### Post by CrusaderAD on 2012-08-30
Hm, then you can't do that... I thought you would have had on board video. Try something like [this]("http://ubuntuforums.org/showthread.php?t=1432857") to see if you can get the generic driver loaded instead of the nvidia driver.

---

### Post by Ditchdoc7893 on 2012-08-30
Fortunately, on my way home from work this morning, I had a brain storm (they occur so infrequently, I almost didn't recognize it ;)). GRUB displays all of the versions of the kernel that I can boot from, so I thought, maybe one of the older ones would boot. I was able to get in that way. From there I went to synaptic and removed nvidia current. What do you know! It worked! I'll mark this thread as solved.

---

### Post by CrusaderAD on 2012-08-30
Nice! Glad to hear you got it working.

---

