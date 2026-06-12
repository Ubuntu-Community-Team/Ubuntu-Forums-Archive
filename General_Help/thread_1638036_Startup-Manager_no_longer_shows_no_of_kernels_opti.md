---
title: "Startup-Manager no longer shows no of kernels option"
date: 2010-12-05
forum: General Help
---

### Post by Mad-Halfling on 2010-12-05
Hi folks, I've used the startup-manager on my old laptop, also running ubuntu, to control the number of kernel options shown in the grub menu, as per this how-to:-
[http://www.ubuntugeek.com/startup-manager-change-settings-in-grub-grub2-and-usplash.html](http://www.ubuntugeek.com/startup-manager-change-settings-in-grub-grub2-and-usplash.html)
see the last screenshot on the page.  I've got a new laptop and am trying to do the same, but on the advanced tab I no longer have this "Limit the number of kernels in the boot menu" option, all I have is "Bootloader menu resolution" and [Create rescue floppy].  Is this because I am now running 64 bit or has this changed in 10.10 (I probably haven't looked at that on my old laptop since before 10.04)?

Thanks

MH

---

### Post by sikander3786 on 2010-12-05
I don't know if that has changed in Maverick or not.

But as a workaround, you can see this great guide by drs305.

[http://ubuntuforums.org/showthread.php?t=1587462](http://ubuntuforums.org/showthread.php?t=1587462)

For more info on Grub, see **drs305's** signature ;-)

---

### Post by Mad-Halfling on 2010-12-07
It's got it on my 32-bit 10.10 system (but this has been upgraded over several versions, so it may, possibly, be a setting/facility from an old version) so I'm guessing it's maybe not implemented on the 64-bit version?

---

### Post by sikander3786 on 2010-12-08
> **Mad-Halfling said:**
> It's got it on my 32-bit 10.10 system (but this has been upgraded over several versions, so it may, possibly, be a setting/facility from an old version) so I'm guessing it's maybe not implemented on the 64-bit version?
Starup Manager should be the same in both 32-bit and 64-bit Ubuntu. Don't know why it is not showing same options in both the OS.

---

### Post by Mad-Halfling on 2010-12-13
> **sikander3786 said:**
> Starup Manager should be the same in both 32-bit and 64-bit Ubuntu. Don't know why it is not showing same options in both the OS.

Think I may have cracked it - I just had another look through that thread you kindly posted and I noticed it doesn't support GRUB 2 - I'll bet my bottom dollar that's the difference between the systems.  My old laptop has always been updated since about Ubuntu 6 and hasn't had a fresh install, so I'm guessing it may be on GRUB 1, whereas my new latop has had a fresh install and so I'm guessing 10.10 will have installed GRUB 2 (does this sound about right?)

I'll look into this and post back

---

