---
title: "Errors after upgrading from 11.10 to 12.04 - Lenovo T410"
date: 2012-04-28
forum: General Help
---

### Post by benb3342 on 2012-04-28
Hi,

Ran thte upgrade last night and all seemed to go fine. When I rebooted and the log in screen is missing icons and when I logged in to Unity nothing happens - just a blank screen. 

If I log into Gnome Classic I get the top menu bar, but with no icons, no wireless etc.

Laptop is a Lenovo Thinkpad T410 (one of these: [http://www.zdnet.com/reviews/product/laptops/lenovo-thinkpad-t410-2537-141-core-i5-520m-windows-7-pro-2-gb-ram-320-gb-hdd/33949431](http://www.zdnet.com/reviews/product/laptops/lenovo-thinkpad-t410-2537-141-core-i5-520m-windows-7-pro-2-gb-ram-320-gb-hdd/33949431))

Any ideas?

Thanks for any help,

Ben

---

### Post by benb3342 on 2012-04-29
Have sorted this out.

Something happened and the libjpeg didn't install correctly, due to missing dependencies.

Booted into recovery mode, started networking then went into the root command prompt.

Ran **apt-get update** then **apt-get upgrade** which gave some errors. I ran **apt-get -f install** which fixed all the problems with the missing dependencies - a took a while to run.

Rebooted and all worked.

Ben

---

