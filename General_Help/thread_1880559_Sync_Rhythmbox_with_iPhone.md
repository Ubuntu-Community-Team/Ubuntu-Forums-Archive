---
title: "Sync Rhythmbox with iPhone"
date: 2011-11-13
forum: General Help
---

### Post by altjx on 2011-11-13
Does this still work? I have an iPhone 4s and I just right clicked my iPhone > Sync device with library.

My iPhone has 234 songs, my library has 255... After syncing, my iPhone still showed 234 songs. Rebooted iPhone 4s, same thing.

Any idea if this is just broken or something?

---

### Post by rorschachwalter on 2012-02-02
Is your phone running iOS 5? If so, there is presently no software (either oss or proprietary) besides that official iTunes libraries that is capable of updating the iOS 5 database properly. In other words, you will be able to transfer music over to the device (you'll see it on the filesystem), but the device will not know those files are there, so they will be inaccessible and invisible.

If your phone is running iOS 4, you should be able to sync. You may need to update packages such as libimobiledevice2 and libgpod to the latest versions. Try the Debian repos for more up-to-date packages than what Ubuntu has to offer.

---

