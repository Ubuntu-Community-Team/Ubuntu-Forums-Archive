---
title: "Random crash/restart after kernel update"
date: 2009-11-27
forum: General Help
---

### Post by luckymutt on 2009-11-27
I have been dual booting XP and Karmic for about 3 weeks and all has been good until the other day.
I ran the update manager and it wanted to update the kernel from 2.6.31-14 to 2.6.31-15
After rebooting, GRUB now listed 2.6.31-15-generic (and the recovery console) in addition to the previous kernel.
If I choose the new kernel, I wind up with a flashing screen asking for my log-in credentials, but I can't seem to type much in (it only seems to recognize every nth keystroke, making it impossible to see that I am typing the correct password)

If I choose the previous kernel, it boots into linux as per normal, however, I am getting completely random crashes/restarts...that is: without warning, everything will blink out as if I held the power button on the machine itself.
It is totally random, happening even when I try to look at the logs.
After a few attempts, I was able to get the /var/log/messages opened and saved to a storage drive that the XP install can access.
It seems the last line recorded is always:
Clocksource tsc unstable (delta = -########## ns)

(the "###...###" varies, presumably according to the machine's clock)

Is anyone else experiencing this???
Is there anyway I can undo the update???

I ran a memtest over night, and nothing is wrong there, plus I ran XP for a good portion of the day with no issues, whereas I can't seem to do anything for more than 5 mins. without a crash/restart in Ubuntu after this update that's gone awry.

Anyone, please?

---

### Post by luckymutt on 2009-11-28
OK, I *believe* I have this taken care of. 
I narrowed it down to the Nvidia driver. I wound up reinstalling the driver (190.42) and it so far *seems* to be working correctly (at least I've gone 40 minutes with no crash) although GRUB still gives me a choice between kernels to boot with.
Right now I am posting from the linux side under the new kernel 2.6.31-15-generic. 
I am curious as to what would happen if I boot by selecting kernel *-14, but not so much that I'll actually try it :)

Now that the kernel update is working, is there aome way I can get rid of the old one in the boot options?

---

### Post by santiagocajiao on 2009-11-28
Hi, I had the same problem.  I just tried to run the previous kernel (31-14) and I got to enter the Desktop...right now I'm going to reinstall the Nvidia Drivers again to see if I can solve this issue to keep the 31-15 version, otherwise I'll remove it and stay with 31-14.

---

