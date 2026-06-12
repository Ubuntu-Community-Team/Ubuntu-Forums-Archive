---
title: "Ubuntu 9.10 - Incorrect Kernel after Upgrade"
date: 2010-01-19
forum: General Help
---

### Post by tnkie on 2010-01-19
After upgrading to ubuntu 9.10 from 9.04 this morning I noticed my sound wasn't working. After trying a few different fixes I noticed a reoccurring comment.

"But then I figured out that my kernel was incorrect.
So if anyone still keeps having this problem, look if you've got the right kernel."

and

"Edited my menu.lst to load the new kernel, removed new linux video driver, the installed the new NVidia driver from the Nvidia website (190 version). Rebooted. Now I had beautiful compositing, still no sound."

This last comment also talks about his video card, and presumably I will need to do a similar thing?

I had a feeling that I shouldn't have pressed "keep my current menu.lst" during the upgrade!

Thanks in advance,
and greetings to all fellow Ubuntu'ers

---

### Post by tnkie on 2010-01-19
Well I figured it out, changed the kernel version to the lastest one I could see installed in synaptic manager in the menu.lst

But I only have mono sound, probably due to something I did when I was trying to fix the sound earlier. I don't think I'll be able to figure this one out. 

I followed this guide earlier:

[http://ubuntuforums.org/showthread.php?t=1316634](http://ubuntuforums.org/showthread.php?t=1316634)

And I'd installed pavucontroller whilst i was still using 9.04 to route my sound into some usb speakers I'm using, all sound is mono.

Thanks in advance.

EDIT: OK it was hard to tell if the sound was mono on the laptop speakers, but it is. So it's just the USB speakers that are coming through the 1 speaker.

---

