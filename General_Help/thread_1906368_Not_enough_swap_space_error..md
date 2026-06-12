---
title: "Not enough swap space error."
date: 2012-01-09
forum: General Help
---

### Post by christhehut on 2012-01-09
[COLOR=black][SIZE=3]After playing the Sims 3 for a few hours, my screen went blank and switched to an error message saying, "PH: Not enough free swap. I'm not sure what to do about this. [/SIZE][/COLOR]

---

### Post by wildmanne39 on 2012-01-09
Hi, it sounds like you do not have enough ram and that made you run out of swap space.

Please post the output of:
```
free -m
```
You may have to use the livecd and create a larger swap or create a swap file.
[http://ubuntuforums.org/showpost.php?&p=489196&postcount=3](http://ubuntuforums.org/showpost.php?&p=489196&postcount=3)
[https://help.ubuntu.com/community/SwapFaq](https://help.ubuntu.com/community/SwapFaq)
[http://mce.commsbyte.com/index.php?option=com_content&view=article&id=81:ubuntu-swap-file-instead-of-partition&catid=10:linuxmce&Itemid=68](http://mce.commsbyte.com/index.php?option=com_content&view=article&id=81:ubuntu-swap-file-instead-of-partition&catid=10:linuxmce&Itemid=68)
This thread is old but should work.
Thanks

---

### Post by christhehut on 2012-01-09
total       used       free     shared    buffers     cached
Mem:                         4020        973       3047          0         78        410
-/+ buffers/cache:       484       3536
Swap:                        1905          0       1905

It looks like there is not any swap being used. It only does this when it goes into hibernation.

---

### Post by wildmanne39 on 2012-01-09
Hi, is this reading from when you have been playing games for hours and it says you are out of swap?
Thanks

---

### Post by christhehut on 2012-01-10
No, I'll post stats after a few hours of gameplay.

---

### Post by wildmanne39 on 2012-01-10
Hi, hibernation would most likely cause that if the game was running when it went into hibernation because it would take a lot more swap then when the system is running.

When it is hibernated everything running goes into swap.
Thanks

---

### Post by christhehut on 2012-01-10
Thanks!

---

### Post by efflandt on 2012-01-10
As mentioned, RAM is saved to swap to hibernate.  But your swap is much smaller than your RAM, so your system cannot hibernate, which is the reason for the "not enough swap" error.

Suspend does not use swap, it just flushes any disk activity and puts cpu and RAM in a low power state.

---

