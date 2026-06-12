---
title: "Help with GRUB"
date: 2006-05-27
forum: General Help
---

### Post by RaisedFist on 2006-05-27
After installing Ubuntu on my computer it couldn't boot windows anymore, so I booted the windows xp install CD and in recovery console I ran fixmbr and fixboot. This didn't solve my problem and now I can't even get to boot my Ubuntu.
My Ubuntu partition is /dev/hda2 or (hd0.1) in grub, but I don't know how to install grub again on the MBR. Can someone help me, please?

---

### Post by localzuk on 2006-05-27
What happens now? If you have ran fixmbr and fixboot, you will have wiped grub from the MBR, so won't be able to load ubuntu.

To re-install grub, take a look at [https://wiki.ubuntu.com/RecoveringUbuntuAfterInstallingWindows](https://wiki.ubuntu.com/RecoveringUbuntuAfterInstallingWindows)

---

### Post by Klaidas on 2006-05-27
How come it could boot windows anymore? :-k 
It didn't detect the partition or some error?

---

