---
title: "Distressingly ancient system recovery"
date: 2011-06-30
forum: General Help
---

### Post by merely on 2011-06-30
Greetings to you all. Apologises if I sound a bit newbieish - I have very little understanding of the subsystems of   computers.

I switched to ubuntu around two months ago, and have found it wonderfully superior to Windows, which is all I had used until then. In that time, I have had only two problems, each sufficient to throw me into something of a panic. The first occurred a month ago, when Windows mysteriously hid ubuntu's root.disk. Not that I realised this (or knew what it meant) until [Rubi1200]("http://ubuntuforums.org/member.php?u=1040746"), on this forum, enlightened me, and told me how to fix it (ie. find the file and put it back with the swap.disk). And everything was as it had been.

A month later - just now - this happened a second time. I was doing what I usually do when ubuntu crashed, and when I rebooted it seemed to be missing its root.disk. This time I did not panic, but, remembering Rubi1200's sage advice, booted up Windows, found the root.file, and put it in its orthodox place.

This was only a partial success, however, for when I then rebooted ubuntu all of my files for the last few weeks prove to be missing. Everything - my files, settings, etc - is back to a more primitive stage. This...is distressing, and I curse myself yet again for not more being more cautious in backing things up. This time, as I said last time, I will never again be so foolish.

Is anyone able to provide hope, or explain what happened? Why was everything restored the first time, and only a version from some weeks ago saved the second time? Is it all merely lost, irretrievable, timewarped? I would be very grateful for any suggestions.

---

### Post by oldos2er on 2011-06-30
This doesn't directly answer your questions, but have you considered installing Ubuntu on its own partition? A Wubi install is really only meant to be a demo, and not a permanent situation. It could've been a "hiccup" with NTFS that caused your original problem.

---

### Post by bcbc on 2011-06-30
Have you had to do a hard poweroff lately? e.g. when you shutdown Ubuntu seems to be hanging so you just hold down the power key?

This is one way that you can corrupt the root.disk in a way that windows removes it. Instead you could use Alt+SysRq R-E-I-S-U-B to try to force a restart.

oldos2er is correct that a direct install is better for long term use - and it sounds like you are intending to keep using Ubuntu. 
However, this problem shouldn't happen either - and you are definitely not alone - there are a small, but steady number of people that lose the root.disk.

You could also make sure that your ntfs host partition is clean by running chkdsk on it. Defragging is a good idea to but that's more useful prior to installing Wubi - since defrag will often ignore large files like the root.disk.

So... from what I know there is no clear answer, but you should know whether you've been forcing poweroffs - and if so, that's probably the cause.

If you want to migrate wubi to a partitioned install - keeping files and settings - you can use this guide: [http://ubuntuforums.org/showthread.php?t=1519354](http://ubuntuforums.org/showthread.php?t=1519354)

---

