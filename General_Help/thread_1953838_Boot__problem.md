---
title: "Boot  problem"
date: 2012-04-07
forum: General Help
---

### Post by leecom89 on 2012-04-07
My laptop is using Ubuntu and Windows, Ubuntu is installed using wubi. Yesterday my laptop was not able to shut down normally in Ubuntu (it stopped working after I chose to shut down for a while), so I had to press the power button for several seconds to do hard shut down. 
Today when I open my laptop again, I can't boot to Ubuntu. The following message appears:
"Try (hd0 0) ntfs5 no wubildr..." and then
Cannot find GRLDR

I logged in to Windows and check. The two files wubildr and wubildr.mbr are in drive C as normally.

So what is wrong here? How can I solve this issue?

---

### Post by bcbc on 2012-04-07
Try running 'chkdsk /f'.

Avoid hard shutdowns - use Alt+SysRq R-E-I-S-U-B instead.

---

