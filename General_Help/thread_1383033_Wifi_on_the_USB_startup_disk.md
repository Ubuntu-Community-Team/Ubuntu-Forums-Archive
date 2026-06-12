---
title: "Wifi on the USB startup disk"
date: 2010-01-16
forum: General Help
---

### Post by diligence400 on 2010-01-16
I'm running Ubuntu on a USB startup disk I created on a USB stick for recovery purposes. I cannot use wifi on my netbook if I boot from he USB. Why is this? Is there any way I can make it work again? (wifi is fine when I boot normally) 

Thanks in advance!

---

### Post by efflandt on 2010-01-16
It depends whether you created a persistent file on the USB Startup Disk and which driver you need for wireless.  For example for BCM4311 or BCM4312 I had to activate Broadcom STA driver and it said to reboot.  I rebooted and then the driver said "activated, but not in use".  On a whim I started searching module directories and found "wl".  So I did **sudo modprobe -v wl** (small L) and it worked.  For a normal installation it works automatically during boot, but from USB live iso you need to modprobe it after boot for it to work.

But other Broadcom wireless devices might need something else, for example BCM4318 needs Broadcom B43 driver.

---

### Post by diligence400 on 2010-01-16
I'm pretty new to Ubuntu; could you explain what a 'persistent file' is, and what modprobe does? Also, how would I go about checking what drivers I need for my wireless?

---

