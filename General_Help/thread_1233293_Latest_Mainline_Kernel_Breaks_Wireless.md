---
title: "Latest Mainline Kernel Breaks Wireless"
date: 2009-08-06
forum: General Help
---

### Post by jlacroix on 2009-08-06
Hello all, I have a Dell Inspiron 15n (the one that ships with Ubuntu preinstalled) and I am having some issues with the Intel driver as many others are.

I was told that the new kernels fix the Intel glitches, so I upgraded to the latest mainline kernel 2.6.30. Everything graphically is improved, but no more wireless. I know that mainline kernels break restricted drivers, but I wouldn't think that a machine that ships with Ubuntu would have restricted hardware. At the very least, I don't have to do anything special with the Ubuntu stock kernel to get wireless working.

Is there any way you guys might know of that will let me use the latest mainline kernel and then still have wireless? One person told me that there may be a conflicting module. My laptop has a Broadcom chip in it, I believe the model is 4311 rev01 but I'd have to check when I get home to be sure.

Thank you guys!

---

### Post by v41 on 2009-08-21
> **jlacroix said:**
> Hello all, I have a Dell Inspiron 15n (the one that ships with Ubuntu preinstalled) and I am having some issues with the Intel driver as many others are.

I was told that the new kernels fix the Intel glitches, so I upgraded to the latest mainline kernel 2.6.30. Everything graphically is improved, but no more wireless. I know that mainline kernels break restricted drivers, but I wouldn't think that a machine that ships with Ubuntu would have restricted hardware. At the very least, I don't have to do anything special with the Ubuntu stock kernel to get wireless working.

Is there any way you guys might know of that will let me use the latest mainline kernel and then still have wireless? One person told me that there may be a conflicting module. My laptop has a Broadcom chip in it, I believe the model is 4311 rev01 but I'd have to check when I get home to be sure.

Thank you guys!
I had exactly the same problem.    The mainline kernel contains the b43 opensource wireless driver which only supports older broadcom wireless cards.  If you've got a newer card, such as the bcm4328 from early 2008, then the b43 driver doesn't work.   Broadcom has posted a  driver on their website that works with newer cards,

[http://www.broadcom.com/support/802.11/linux_sta.php](http://www.broadcom.com/support/802.11/linux_sta.php)

but the installation requires compiling some code for the driver.  So it's doable if you're comfortable compiling code.

---

