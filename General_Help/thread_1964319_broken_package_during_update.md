---
title: "broken package during update"
date: 2012-04-23
forum: General Help
---

### Post by vbdanl on 2012-04-23
Hi.  i was trying to get the latest updates installed. ran sudo apt-get update, then selected the update-manager.   it ran for awhile, then came back with ```
E: /var/cache/apt/archives/linux-image-2.6.32-41-generic_2.6.32-41.88_amd64.deb: unable to create `/lib/modules/2.6.32-41-generic/kernel/sound/soc/codecs/snd-soc-wm8960.ko.dpkg-new' (while processing `./lib/modules/2.6.32-41-generic/kernel/sound/soc/codecs/snd-soc-wm8960.ko')
E: /var/cache/apt/archives/linux-headers-2.6.32-41_2.6.32-41.88_all.deb: unable to create `/usr/src/linux-headers-2.6.32-41/arch/h8300/platform/h8300h/aki3068net/Makefile.dpkg-new' (while processing `./usr/src/linux-headers-2.6.32-41/arch/h8300/platform/h8300h/aki3068net/Makefile')
E: /var/cache/apt/archives/linux-headers-2.6.32-41-generic_2.6.32-41.88_amd64.deb: error creating directory `./usr/src/linux-headers-2.6.32-41-generic/include/config/hpet'
```
I selected the "Edit/Fix Broken Packages" and then got the above.  i think it is the same errors as i got the first time, but not positive.
thanks for your help.  was on 2.6.32-40 and it was trying to update to -41

---

### Post by vbdanl on 2012-04-27
i figured it out.  the messages indicated i was out of disk space.  i had ran apt-get remove linux-image-version-generic for the old versions (ususally keep the last 2 or 3 kernels), but found that does not clean up /usr/src directories.  i had about 20 of them going back to -21.  removed all of those directories, then ran the fix-broken option in synaptic edit menu. that seemed to fix the problem.  the 41 kernel is now installed.

---

### Post by mcovey on 2012-04-27
Use apt-get purge when you need to remove packages more thoroughly. Actually, I just always use purge, unless you know you will need residual config files or directories from a package, might as well just purge it.

---

### Post by vbdanl on 2012-05-15
thanks.  i will try the purge option next time.

---

