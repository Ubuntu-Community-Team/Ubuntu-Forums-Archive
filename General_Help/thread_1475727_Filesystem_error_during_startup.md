---
title: "Filesystem error during startup"
date: 2010-05-07
forum: General Help
---

### Post by TheAlien on 2010-05-07
I recently installed Ubuntu 10.04 and ran the update manger to get the latest updates right after the install was completed. I was prompted to boot after the update was done, and during that boot it reported an error on my separate /boot/ partition. I chose F to fix the problem, and I was then able to complete the boot without any further problems.

Does anyone know what this could be, and are there any ways for a newbie like me to check what went wrong?

Any sort of help is much appreciated! Thanks! :)

---

### Post by dino99 on 2010-05-07
well there are thousands random reasons  ;)

sudo apt-get update
sudo apt-get install -f
sudo dpkg --configure -a

---

### Post by TheAlien on 2010-05-08
I think I've solved the issue. I was using only 100MB for the /boot. I repartitioned my HDD and gave /boot 2.5GB of space and reinstalled, and everything works fine now. I see now that the /boot has over 100MB of used space, so it seems like that caused the error.

---

