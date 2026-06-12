---
title: "Purple/black boot screen, no plymouth."
date: 2011-05-01
forum: General Help
---

### Post by _Pipo_ on 2011-05-01
I already had Plymouth issues on 10.10, which was solved by this script [http://kyleabaker.com/2010/07/11/how-to-fix-your-ubuntu-boot-screen/](http://kyleabaker.com/2010/07/11/how-to-fix-your-ubuntu-boot-screen/)

After upgrade, boot only gave me a blank, purple screen, so I used his revert script then tried this : [http://ubuntuforums.org/showthread.php?t=1742944](http://ubuntuforums.org/showthread.php?t=1742944)

But I'm only getting a black screen. Removing vga=795 option only make it stay purple. It might be because of the multiples workarounds I tried back in 10.10, but I don't know how to clean that up. I have an ATI HD Radeon Pro 2400 card with free drivers (but I was using the proprietary ones during upgrade).
Does someone know how to fix this? Thank you.

---

### Post by timgood on 2011-05-01
[http://ubuntuforums.org/showthread.php?t=1742944](http://ubuntuforums.org/showthread.php?t=1742944) worked for me and others. Give it a try. But first, boot from a live CD and purge and re-install grub. Instructions [here]("http://ubuntuforums.org/showthread.php?t=1581099").

This also works: [http://paolobernardi.wordpress.com/2011/05/01/fix-plymouth-on-ubuntu-after-installing-nvidia-or-ati-proprietary-drivers-for-ubuntu-11-04-natty/](http://paolobernardi.wordpress.com/2011/05/01/fix-plymouth-on-ubuntu-after-installing-nvidia-or-ati-proprietary-drivers-for-ubuntu-11-04-natty/)

Edit: in fact the second solution works better.

---

### Post by _Pipo_ on 2011-05-01
Thanks, the second link I gave was actually your thread (and it didn't work for me), but the improved script did !
However, for some reason, the nomodeset parameter prevents unity from loading, but plymouth works just as well without it.

---

