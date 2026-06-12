---
title: "inner live cd workings"
date: 2010-09-12
forum: General Help
---

### Post by flyingsliverfin on 2010-09-12
i know the basics about live cd's but ive never understood how exactly they work... when i look into a (for ex 910 ubuntu) live cd that from ubuntu, i see folders casper,dists, install, etc. i looked at the sizes of the folders and found that 675 mb are in the filesystem.squashfs. when i boot the livecd, how does that become the whole structure of the normal ubuntu system? is it just a compression like a .gz?

also for a persistent usb stick (4gb) it has the seemingly same file structure, except that the isolinux folder has been replaced by syslinux, and theres a gigantic casper-rw file sitting in the middle of it all...

i read somewhere that by editing the /syslinux/text.cfg and adding a persistent somewhere u can make the whole thing persistent. so does that mean that syslinux controls the processes going on afterward? 

before it was easy to just use live cd's and usb's, but now that i take a look inside its very confusing

---

