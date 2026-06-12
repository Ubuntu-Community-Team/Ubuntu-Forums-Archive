---
title: "Apparmor 2.4 Compatibility Patch"
date: 2011-01-26
forum: General Help
---

### Post by Habeouscorpus on 2011-01-26
I was trying to install apparomor-profiles, and the terminal spewed a lot of error messages. They all said, "Kernel needs 2.4 compatibility patch." 

Where is this patch, (I tried Google), and how do I install it?

---

### Post by unc0nn3ct3d on 2011-02-27
you can get patches for the mainline kernel here

[http://kernel.org/pub/linux/security/apparmor/apparmor-2.6.36-patches.tgz](http://kernel.org/pub/linux/security/apparmor/apparmor-2.6.36-patches.tgz)

just go to the source dir then

patch -p1 < patchfile (for all 3)

then check you have the compatibility option enabled.

See : [https://apparmor.wiki.kernel.org/index.php/Apparmor/upstream_release_notes](https://apparmor.wiki.kernel.org/index.php/Apparmor/upstream_release_notes)

as taken from here: [https://bugs.launchpad.net/ubuntu/+source/apparmor/+bug/680485](https://bugs.launchpad.net/ubuntu/+source/apparmor/+bug/680485)

Also see: [http://patchwork.ozlabs.org/patch/69819/](http://patchwork.ozlabs.org/patch/69819/)

---

