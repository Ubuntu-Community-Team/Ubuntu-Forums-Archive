---
title: "Plymouth randomly stalling at boot. Fsck issues?"
date: 2010-05-14
forum: General Help
---

### Post by Surlent777 on 2010-05-14
Quite simply, I am very discouraged. I hate trying to reboot, because it can take anywhere from 2-10 tries to actually get a working system. When I reboot, often it will stay at the plymouth screen, which, even though I have the proprietary Nvidia drivers, looks absolutely normal. Go figure. I'm not sure if I can hear hard drive activity or if it's simply my fans. There's no terminal output, even with "quiet" removed from GRUB, aside from a message about setting up the framebuffer. I've left it alone for up to twenty minutes during these fits, and nothing happens. I have to keep REISUB-ing or even just B-ing until it decides to work, in which case the boot is pleasantly quick, as expected. I do not like how an LTS release is unpredictable in its booting--this and the random crashing to vertical bars (as with [http://ubuntuforums.org/showthread.php?p=9277101](http://ubuntuforums.org/showthread.php?p=9277101)) on my other computer (as well as a garbled plymouth on its intel chipset) have me very reluctant to recommend this to others right now, and that bothers me too. But I digress. I've heard that sometimes fsck runs in the background doing a scan, but I'm not sure that is what's happening in this case because one time I actually saw a message telling me it was doing that, and it proceeded fairly normally. Except for that one time, I have seen no messages. Any advice would be greatly appreciated. If it's relevant, it was an upgrade from what was once a fresh install of Karmic. Thanks in advance.

---

### Post by TeoBigusGeekus on 2010-05-14
Not sure what your problem is, but I'll tell you from my experience that I've never done an upgrade that ended well (i.e. a stable system). 
I've learned (the hard way) to keep a separate /home partition and always reinstall new versions of Ubuntu.

---

### Post by Surlent777 on 2010-05-14
The obvious problem with that is that it's quite simply easier to keep everything on one partition because then I never have to worry about size constraints, and it makes dual-booting with 7 that much simpler. What I really need is a worthwhile solution to this issue so I can go on to fixing the other, much more minor, annoyances such as GNOME not wanting to launch either Metacity or Compiz without me explicitly telling it or Nautilus and its actions taking over in KDE in inappropriate times...

---

### Post by Surlent777 on 2010-05-26
Alright, I thought this so significant that it warranted a renaming of the topic, so here it is: I finally noticed that for whatever reason I had two "splash" options going in GRUB. They don't seem to interfere with each other, and this isn't my point. My point is that after I removed both of them + quiet, I finally got a text-only boot telling me what was going on. I did three trials. The first two were failures, and the third successful. Both started out by telling me that /dev/sda5 was mounting, but then the first two wait a bit and threw out some stuff about a device I've never heard of before, /dev/shm, I believe. It claims that it can't find it or it doesn't exist (forget exact wording) and then it tells me that my root filesystem can't be mounted and drops me into a maintenance shell. This has got to be where Plymouth is hanging. On the third try, it had the usual message about /dev/sda5 mounting, then it told me it had to clean up slightly on that partition, did so, and then mounted the root filesystem and booted normally. The question we have now is "what is /dev/shm, and how does it affect system boot-up?"

---

### Post by Surlent777 on 2010-05-26
According to [http://www.cyberciti.biz/tips/what-is-devshm-and-its-practical-usage.html](http://www.cyberciti.biz/tips/what-is-devshm-and-its-practical-usage.html) /dev/shm is tied to tmpfs, if I am understanding correctly. That at least answers the first part of my question. Now, what is the significance of this not wanting to show up? I've already checked my RAM several times...it seems fine. Two 2GB sticks at 800MHz.

---

### Post by bikeboy on 2010-05-26
What version of 'mountall' are you running? There was an issue between that and Plymouth that was fixed in mountall 2.15, which is in lucid-updates

---

### Post by Surlent777 on 2010-05-26
> **bikeboy said:**
> What version of 'mountall' are you running? There was an issue between that and Plymouth that was fixed in mountall 2.15, which is in lucid-updates

I seem to be running mountall 2.15, and I update my system every day or two anyway. Also just noticed that my topic rename only renamed the first post. Either way. =/

---

### Post by Surlent777 on 2010-06-05
Well, I think I solved it by giving up. I erased my backup hard drive, of which the primary is based on (I cloned/expanded it) to make one big Ext4 partition so I could do my backups. In the processes, I noticed that GParted kept claiming that the backup's Karmic partition was mounted at /. Seeing this, I quickly made a Lucid LiveUSB and was able to successfully do my partitioning. Since then, every single boot has been successful, even after changing Plymouth themes. I didn't have issues booting in Karmic, but somehow during the upgrade GRUB or fstab or something decided that both drives should be mounted at the same time, but since the primary hard drive was mounted last, I never noticed. This must have confused the system, which might explain why /dev/shm didn't load half the time. Total madness. Moral of the story is "don't backup your kernels, just your data. Otherwise things go crazy and make you cry".

---

