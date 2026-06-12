---
title: "How to fix no video after kernel upgrade"
date: 2011-09-10
forum: General Help
---

### Post by ratman1 on 2011-09-10
Hi

Every time I do a kernel upgrade and forget to reinstall my graphics card (AMD 6870) drivers there is no video when I reboot, and I can't figure out how to reinstall the drivers. I have now resorted to using the default, slow, crappy drivers in case I forget again!

Now I want to do blender work but the default drivers are too slow for my liking.

My question is, what should I do in case I forget to reinstall them. I could probably do it with the terminal but there is no video to see it with. Is there a way to get the video back so I can reinstall the drivers?

Please don't say "just don't forget next time" because this is about the 6th time..... :lolflag:

---

### Post by Duncan Williams on 2011-09-10
Similar situation with my nvidia drivers and kernel updates.
My problem is outlined here:
[http://peppermintos.net/viewtopic.php?f=9&t=3893](http://peppermintos.net/viewtopic.php?f=9&t=3893)

I have not done a kernel update recently.
But next time I do I will try:

* uninstall nvidia drivers
* install nouveau drivers
* reboot
* install kernel update
* reboot
* install nvidia drivers (from xswat ppa)

hopefully this will work ok.

---

### Post by ratman1 on 2011-09-10
Thanks, but that doesn't really show me how to reinstall the drivers when there is no GUI.
But it is good to see others with the same issue as me!

---

### Post by Duncan Williams on 2011-09-10
can you get into `recovery mode' `failsafe graphics' ?
if so you may be able to do it from there.

---

