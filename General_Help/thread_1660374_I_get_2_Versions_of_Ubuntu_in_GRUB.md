---
title: "I get 2 Versions of Ubuntu in GRUB"
date: 2011-01-05
forum: General Help
---

### Post by Sanchenzo on 2011-01-05
I seem to be getting 2 versions of Ubuntu at startup. This happened after I updated Ubuntu. Does anyone have any ideas how I can remove the older version from GRUB?

---

### Post by philinux on 2011-01-05
> **Sanchenzo said:**
> I seem to be getting 2 versions of Ubuntu at startup. This happened after I updated Ubuntu. Does anyone have any ideas how I can remove the older version from GRUB?

There's no harm in them being there at all.  But if you want to get rid of older kernels then see this.

[http://tuxtweaks.com/2009/12/remove-old-kernels-in-ubuntu/](http://tuxtweaks.com/2009/12/remove-old-kernels-in-ubuntu/)

Or someone might suggest installing startupmanager to hide them.

---

### Post by coffeecat on 2011-01-05
This will have happened after a kernal upgrade. The older version is not removed so that if you encounter any problems with the newer kernel, you can still boot up with the older one.

My guess is that since you're running Maverick the older kernel is the 2.6.35-22 which is what came on the install CD. The latest kernel is 2.6.35-24. Is that the one you have? There was an intermediate 2.6.35-23 but you may have missed that if you installed recently.

You can uninstall the older kernel but it's generally a good idea to keep at least one older kernel in case you have problems with the newer version. Some people are reporting problems with the 2.6.35-24, but it's working just fine for me. Probably for most people I would guess - it depends on your hardware. But I would suggest leaving it for a couple of weeks to make sure the 2.6.35-24 is good for you. 

If you do want to uninstall the older kernel, open System > Adminstration > Synaptic and do a search for the string '2.6.35-22' or whichever version you want to remove. There will be 3 or 4 packages. Mark them for removal and click on apply. The grub menu will be automatically updated.

---

### Post by Sanchenzo on 2011-01-05
> **coffeecat said:**
> This will have happened after a kernal upgrade. The older version is not removed so that if you encounter any problems with the newer kernel, you can still boot up with the older one.

My guess is that since you're running Maverick the older kernel is the 2.6.35-22 which is what came on the install CD. The latest kernel is 2.6.35-24. Is that the one you have? There was an intermediate 2.6.35-23 but you may have missed that if you installed recently.

You can uninstall the older kernel but it's generally a good idea to keep at least one older kernel in case you have problems with the newer version. Some people are reporting problems with the 2.6.35-24, but it's working just fine for me. Probably for most people I would guess - it depends on your hardware. But I would suggest leaving it for a couple of weeks to make sure the 2.6.35-24 is good for you. 

If you do want to uninstall the older kernel, open System > Adminstration > Synaptic and do a search for the string '2.6.35-22' or whichever version you want to remove. There will be 3 or 4 packages. Mark them for removal and click on apply. The grub menu will be automatically updated.

Yes that is correct, but I have decided not to remove it. Thank you for telling me.

---

### Post by cgroza on 2011-01-05
Well, those things over time they pille up. I already have 3 kernels installed and plus the recovery options, 6 entries. It really annoys me, especially when you have multiple distros installed.

---

### Post by scouser73 on 2011-01-05
The best way to remove old kernels would be to install Ubuntu Tweak [http://ubuntu-tweak.com/](http://ubuntu-tweak.com/)

Once installed, you'll find it under **System Tools**, select it and it will open up then click on **Package Cleaner** and click on **Unlock** then click on **Clean Kernels** and a list of out-dated kernels will appear and then finally click on **Cleanup**.

---

