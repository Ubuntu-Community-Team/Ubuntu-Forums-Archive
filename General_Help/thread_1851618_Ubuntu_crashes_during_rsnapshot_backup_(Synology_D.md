---
title: "Ubuntu crashes during rsnapshot backup (Synology DS110j + DSM 3.2)"
date: 2011-09-28
forum: General Help
---

### Post by dbloom on 2011-09-28
Hi,

I have rsnapshot backing up daily/weekly/monthly to a DS110j. Rsnapshot is on the desktop and seem to suffer a massive memory leak when trying to delete the "daily.6" folder. I have 8gb of RAM and i noticed that a 100% is used just before ubuntu starts shutting itself down.

The DS110j is mapped to ubuntu using NFS. it's worked very nicely until I upgraded to DSM 3.2. After that, I noticed my mouse would stop working after some time. I honestly didn't this it was related, but recently I did a clean install and now the mouse becomes erratic as memory use gets very high. It then stops, programs start closing, and i'm backed out to a console where it simply hangs.

I thought it was hardware, but everything seems to check out ok (basic specs below). I also found that if i manually delete daily.6 prior to running rsnapshot, it works perfectly (and no subsequent crashes). I also found that if I try deleting the folder from within DSM, the processor runs at 100%. Is this normal? If i try running "rm -rf daily.6/", ram use runs up to 100% pretty quickly.

The NFS mount in my fstab looks like this:

> # mount Synology NAS NFS share
192.168.x.x:/volume1/NetBackup /media/storage nfs soft,intr,rsize=8192,wsize=8192



I found instructions in the Synology forum for setting it up.

Any ideas or help or tweaks would be greatly appreciated. My computer is becoming barely useable due to the constant crashing...

Thanks!

PC Specs:
cpu: AMD Phenom II quad-core 3.4GHz
mem: 8GB (4x2GB) -- successfully passed memtest tests
gfx: 2x nvidia in SLI mode (can't recall which cards offhand)
mb: ASUS M4N98TD EVO (nForce chipset)

---

