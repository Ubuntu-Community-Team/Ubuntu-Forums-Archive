---
title: "Dual boot Win7(64) - 11.10(64) Crushes Internet Connect"
date: 2012-03-15
forum: General Help
---

### Post by dasbrow on 2012-03-15
Just built a new desktop: ASUS M/B, i5 2500K cpu, 8 MB RAM, on board network and using on-chip video, 500GB H/D with 2 250GB partitions : Win7 (64) and Ubuntu 11.10 (64) in dual boot.

Ubuntu side internet connection gets crushed every time I boot into Windows.  I use FiOS.  Resetting the PC, Cable Modem and fiber conversion box temporarily resolves the problem.

Sometimes internet connection is left at 5 MBps down and .202 MBps up.  Other times it is left at 30MBps down and 5 MBps up.  In the worst cases there is no connectivity. Normal connection speeds are 25/15.

This is how it goes:  Log into Ubuntu all is well, reboot into Windows and all is fine, switch back to Ubuntu and internet conecticity is severly compromised.

Does anyone know how to fix this?

Thanks.

---

### Post by oldfred on 2012-03-17
If you reboot from Ubuntu to Ubuntu is it ok? And the same reboot from Windows to Windows is it still ok or not?

Years ago a similar issue and we all said it was impossible as each system was independent. 
But then it turned out the modem card kept a setting that really had to be reset. A warm reboot did not reset it as rebooting did not send a proper set-up to the modem.

---

### Post by Mark Phelps on 2012-03-18
I have a multi-boot desktop PC (Win7, Ubuntu 11.10) and am also using FIOS -- and have no problems switching from one OS to another.

However, I did have problems a while back BEFORE I switched to FIOS due to faulty RealTek network drivers in Win7.  Was encountering problems similar to yours.

Took three driver updates from Gigabyte to fix the problems. But after that, everything has been OK -- even with the switch to FIOS.

So, I would check your network adapter and if it's RealTek, see if there are driver updates for it -- in Win7.

---

### Post by dasbrow on 2012-03-18
> **oldfred said:**
> If you reboot from Ubuntu to Ubuntu is it ok? And the same reboot from Windows to Windows is it still ok or not?

Years ago a similar issue and we all said it was impossible as each system was independent. 
But then it turned out the modem card kept a setting that really had to be reset. A warm reboot did not reset it as rebooting did not send a proper set-up to the modem.

It works fine after a multi hour rest if I warm boot back into Ubuntu.  Windows always work fine.  However, if I warm boot from Ubuntu to Windows and back, my internet connection in Ubuntu is trashed.

I believe it's an old problem with the Realtek 8169 driver on an 8186/8111e on-board lan port.  I had difficulty upgrading/changing the driver.  The "make" routine did not complete.  So, I went to 12.04 beta 1 and no more problems.  There is a post that suggests that 12.04 will solve the few occurances of this problem and I guess it was correct.

Thank you for your response.

---

### Post by dasbrow on 2012-03-18
> **Mark Phelps said:**
> I have a multi-boot desktop PC (Win7, Ubuntu 11.10) and am also using FIOS -- and have no problems switching from one OS to another.

However, I did have problems a while back BEFORE I switched to FIOS due to faulty RealTek network drivers in Win7.  Was encountering problems similar to yours.

Took three driver updates from Gigabyte to fix the problems. But after that, everything has been OK -- even with the switch to FIOS.

So, I would check your network adapter and if it's RealTek, see if there are driver updates for it -- in Win7.

I'm sure, now, that it is/was a driver issue but I think it was an Ubuntu driver that was unstable with my particulare mother board chip set: ASUS Intel board with Realtek 8111e ethernet port.  The r8169 driver installed by default and difficult for me to change just didn't like the residue left from sharing the port with Win 7.  A cold boot waws not enough it seems.  Even a 2 hour shut down was not enough.  But, overnight and the next day a fresh boot to Ubuntu 11.10 (64) and it worked fine until I had to go to windows (photographic tonemapping and HDR processing).

However, 12.04 Beta 1 has fixed the problem and is very nice to use.  It's a bit stripped down but that's a good thing!!

Thanks for the help/input.

---

### Post by Mark Phelps on 2012-03-18
Glad to see you got it fixed.

Just so you know, until 12.04 gets released in April, please post any problems or questions you have on it in the Precise Development forum, not here.  This forum is for Released versions of Ubuntu.

thanks

---

