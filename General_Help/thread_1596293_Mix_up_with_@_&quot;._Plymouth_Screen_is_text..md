---
title: "Mix up with @ &quot;. Plymouth Screen is text."
date: 2010-10-14
forum: General Help
---

### Post by mg1234 on 2010-10-14
Two things.

First off, since 10.04, no matter how many times I try to change the keyboard layout to United Kingdom, when I log back in the @ and " signs are ALWAYS in the wrong place.
Second off, I installed the NVIDIA proprietary driver to allow Compiz to work, except now my Plymouth Screen is a lot of ugly text.

These are both small issues, but, annoying. :)

---

### Post by garvinrick4 on 2010-10-14
> **mg1234 said:**
> Two things.

First off, since 10.04, no matter how many times I try to change the keyboard layout to United Kingdom, when I log back in the @ and " signs are ALWAYS in the wrong place.
Second off, I installed the NVIDIA proprietary driver to allow Compiz to work, except now my Plymouth Screen is a lot of ugly text.

These are both small issues, but, annoying. :) Do you mean you are getting a text boot with no plymouth at all? If you are not getting your
graphic drivers to hit so plymouth starts before your / mounts then there is a fix for that but I do not know what ugly text is.
Start graphic drivers first in boot #540801 launchpad 
```
sudo -i
```
```
echo FRAMEBUFFER=y > /etc/initramfs-tools/conf.d/splash 
update-initramfs -u
```

---

### Post by mg1234 on 2010-10-16
No, the background is still purple, just instead of the logo, I get big text saying Ubuntu 10.10, and then some terminal stuff underneath it.

---

### Post by keithy on 2010-10-16
i get the same. even after adding the framebuffer command :(

---

