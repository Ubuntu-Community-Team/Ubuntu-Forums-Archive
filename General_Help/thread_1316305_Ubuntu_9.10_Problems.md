---
title: "Ubuntu 9.10 Problems"
date: 2009-11-05
forum: General Help
---

### Post by Dnyce2k6 on 2009-11-05
Hey guys, I would really appreciate some help. I recently booted Ubuntu (I was running Jaunty) and was prompted that there was a system update available to 9.10. After installing, my computer rebooted Ubuntu failed to run. Whenever I try to run Ubuntu, I just get a screen with some text that flashes over and over. I'm back on Vista again, but I really would like to have Ubuntu back again. Idk what went wrong. I'd appreciate any help any of you can offer. Thanks.

-Dave

---

### Post by JillSwift on 2009-11-06
Your best bet is to download a copy of the 9.10 install disk and make a fresh install.

You can back up your /home data (assuming it's not on its own partition) from the liveCD session.

---

### Post by Ian Sinclair on 2009-11-07
I had endless problems with 9.10 - Grisbi had segmentation errors, F-spot printed rubbish instead of selected photos, sound was missing ... each time I tried an application something else went wrong, and the boot up was surprisingly slow.
Solved all of the problems by making a clean install of 9.04, and configuring Update Manager not to accept new versions.

---

### Post by loxxs on 2009-11-07
Hi Ian

I tried both upgrade from 9.04 to 9.10 and clean install of 9.10.

System froze with busy cursor stuck on the screen, wiped hard drive performed clean install of 8.10 (worked fine), tried upgrade to 9.04 (worked fine).

Think like you will wait for 9.10.1 or an alpha of 10.04.

---

### Post by mr_steve on 2009-11-08
> **Dnyce2k6 said:**
> Hey guys, I would really appreciate some help. I recently booted Ubuntu (I was running Jaunty) and was prompted that there was a system update available to 9.10. After installing, my computer rebooted Ubuntu failed to run. Whenever I try to run Ubuntu, I just get a screen with some text that flashes over and over. I'm back on Vista again, but I really would like to have Ubuntu back again. Idk what went wrong. I'd appreciate any help any of you can offer. Thanks.

-Dave

This is bug #[lpbug]403408[/lpbug]. See the comments there for some solutions. In short, you can make your system boot by doing the following:

1. Hold down the shift key while booting, this will allow you to access the grub menu.
2. Hit 'E' to edit the boot options
3. Delete the entire line starting with "search"
4. Press Ctrl-X to boot.

Hopefully this will be fixed soon. It's absolutely obnoxious that new Ubuntu users are running into such a major issue right out of the box.

---

### Post by vexorian on 2009-11-09
> **Ian Sinclair said:**
> I had endless problems with 9.10 - Grisbi had segmentation errors, F-spot printed rubbish instead of selected photos, sound was missing ... each time I tried an application something else went wrong, and the boot up was surprisingly slow.
Solved all of the problems by making a clean install of 9.04, and configuring Update Manager not to accept new versions.
Those are way too many issues, I would check the integrity of your install disk.

I have an issue with karmic in my netbook, ever odd time I boot the computer, grub freezes with just a blinking text cursor.

---

