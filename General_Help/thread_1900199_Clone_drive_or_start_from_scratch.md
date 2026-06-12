---
title: "Clone drive or start from scratch?"
date: 2011-12-25
forum: General Help
---

### Post by Luxx on 2011-12-25
I had my computer all set up exactly the way I wanted it, all the configurations, software, settings, etc. and the motherboard went out on me. I have another system now that is entirely different. I can't just plug in my hdd and turn it on. I tried it anyway, it showed the bios and start options and flashed what looked like the purple background of the splash screen and then went to no signal. 

I tried installing a new Ubuntu, but I can't work with Gnome-3 or Unity and I really want MY computer back. I don't know how long it will take me to remember what I installed on it or if I can figure out how I configured most of it again. It seems my options are to install the LTS 10.04 and upgrade to 10.10 again and then add and tweak everything to get it close to where I had it, or I can look for another distro that I can work with as smoothly as what I have enjoyed up until now and start over with the software, profiles, and other stuff -- but is there a way I can clone the hdd so it will boot on a new system or can I get the current hdd to reconfigure drivers and such for the new system?

Any advice greatly appreciated. Thanks.

---

### Post by wildmanne39 on 2011-12-25
Hi, linux hard drives can be taken out and put in another computer with out much trouble the problem you are having is you did not remove the video card driver before you removed it from your old computer, you maybe able to use nomodeset to boot ubuntu then remove the old driver and install the new one if it needs a new one.
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
Thanks

---

### Post by Luxx on 2011-12-26
Thanks for your reply. I wasn't able to get it, though because I managed to deactivate the boot partition on the Windows 7 HDD on the new system. I had my old HDD plugged into the next SATA port and selected it in the boot menu. This time I didn't disconnect the other [windows] HDD.

I got a menu that gave me boot options, several kernels listed with the recovery mode for each. I chose the first recovery mode option (whatever it's called in the menu), let it do it's thing, and restarted and selected the second HDD again in the boot menu -- and it booted right up into my old desktop!

All I needed was a little patience with the recovery option and a reboot.

---

### Post by wildmanne39 on 2011-12-26
Hi, that is great! that is just another reason I love ubuntu, you can switch drives to a new computer without much trouble but you can not do that with windows.
Thanks

---

### Post by Luxx on 2011-12-26
I never would have thought moving my HDD to a system with a COMPLETELY different chipset (ASUS AM3/ATI-Radeon to Gigabyte Intel/NVidea) could be so easy!

---

### Post by wildmanne39 on 2011-12-26
Hi, neither did I until a few months ago, I was working on an old computer for a friend and it would not install ubuntu no matter what I did so I put the hard drive in my computer and installed ubuntu then put it back into there computer and it booted perfectly the first time.
Thanks

---

