---
title: "scale in nvidia-settings not working (plus other stuff)"
date: 2006-05-05
forum: General Help
---

### Post by qiemem on 2006-05-05
I recently upgraded to dapper (in doing so, had some driver issues, fixed by simply updating nvidia-glx package), but since then have not been able to get fullscreen apps (most notably, games like Nexuiz and Cube) to scale properly. I have widescreen laptop (optimal resolution 1920x1200), but apps stay stubbornly either narrow (as in the case of Nexuiz) or tiny at their own resolution placed on the 1920x1200 (as in the case of Cube). 

I've tried messing around with the Flatpanel Scaling in nvidia-settings, but nothing changes. Is this the proper way to go about it?

I'm also wondering if this is a symptom of a larger problem. I can't seem to get Legends to run at all. It always crashes right after setting the screen mode (flashes black for a second then quits). Anyway, I'm wondering if there's a way I can check if my drivers are set up properly and all that. I don't know much about this stuff, so any help would be most appreciated.

Oh, and I'm currently using the drivers as installed by the package nvidia-glx.

---

### Post by louis_nichols on 2006-05-05
Your problem seems very similar to the one I encountered with dapper. I wrote about it in [this thread]("http://ubuntuforums.org/showthread.php?t=170169")

Perhaps some of the answers there will help you. I wasn't able to use xvidtune, but, as said in the last post, adding vga=792 to menu.lst had a very good result.

Hope it helps.

---

### Post by qiemem on 2006-05-05
Mmm, I'm afraid our problems are quite different. My problem only arises when using fullscreen applications like games (actually, the only time its arisen is when running Nexuiz and Cube). I had a problem earlier with my frameebuffer resolution which was fixed by setting vga= to something... I think this problem is more driver related, or openGL related, I don't know. I don't think its screen related, because X definitely fills the whole screen, as do screen savers, and movies (and the console).

But thanks anyway. It was interesting and informative to read about. 

Oh yeah, I forgot to say I my original post, my video card is a NVIDIA GeForce Go 6800.

---

### Post by Jason_25 on 2006-05-05
Some laptops have a screen scaling option in the bios.

---

