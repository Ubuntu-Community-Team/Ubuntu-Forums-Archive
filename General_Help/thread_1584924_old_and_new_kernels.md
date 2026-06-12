---
title: "old and new kernels"
date: 2010-09-29
forum: General Help
---

### Post by U_buntu on 2010-09-29
Would anything happen if i downloaded a kernel upgrade thats older than mine current kernel? and this download is VIA update manager.

---

### Post by TBABill on 2010-09-29
Normally when you download another kernel and then reboot, that kernel and the previous kernel are both available in Grub2 to choose between. I would expect installing an older one would be no different than installing a newer one (so long as it's an appropriate kernel for the version of Ubuntu you are running! - meaning if you are using 10.04 you download a previous 10.04 kernel, not an older 9.10 kernel, for example). Then choose between them at startup. If the older works better than the newer, just remove the newer later (after you are certain the one you choose meets your needs).

It won't hurt anything to try. It's your choice which you use and if you don't like the new (old) kernel after installing, just remove via Synaptic.

---

### Post by U_buntu on 2010-09-29
Well i dont get the grub on boot at all. But i've been having issues with updates. after the reboot, the computers pretty much useless till a reinstall. Thought possibly the two may have clashed

---

### Post by Frogs Hair on 2010-09-29
If you chose to use an old kernel keep and eye on your updates so you don't install a newer kernel when kernel updates come.

---

### Post by U_buntu on 2010-09-29
Yea i just got 10.04 three days ago. tryed the update after install and the lock up issue started. Trying to pin point the problem

---

### Post by TBABill on 2010-09-29
Did you happen to install a video driver manually instead of through Synaptic when you installed? I have seen several posts of people having issues after updates, but then find out they installed video drivers directly from nVidia or ATi and then the new kernel update and other updates borked the system. Just a thought, but probably not your issue.

---

### Post by U_buntu on 2010-09-29
no I havent installed any video drivers. thought you stopped needing to manual install that years ago?

---

### Post by Quackers on 2010-09-29
During the upgrade did the Update Manager say that only a Partial Upgrade was possible?

---

### Post by U_buntu on 2010-09-29
No I did a complete install for the system 10.04.    And during the software update, it had said nothing at all, just went on with the dl and install

---

