---
title: "Intel 855GM Fix Help?"
date: 2010-07-29
forum: General Help
---

### Post by boarder2 on 2010-07-29
[https://wiki.ubuntu.com/X/Bugs/Lucidi8xxFreezes](https://wiki.ubuntu.com/X/Bugs/Lucidi8xxFreezes)

I have been able to boot using Workaround A (Enabling KMS), however when I try to add the apt sources to install the updated driver, it's failing to get the new packages:

I've run 
```
sudo apt-add-repository ppa:glasen/intel-driver
sudo add-apt-repository ppa:glasen/855gm-fix
``` (Because I saw it somewhere else, 855gm-fix might not be needed??)
They successfully imported and added the sources.

Running apt-get update errors with 
```

W: Failed to fetch http://ppa.launchpad.net//glasen/ubuntu/dists/lucid/main/binary-i386/Packages.gz  404  Not Found

W: Failed to fetch http://ppa.launchpad.net/glasen/libdrm/ubuntu/dists/lucid/main/binary-i386/Packages.gz  404  Not Found

E: Some index files failed to download, they have been ignored, or old ones used instead.

```Any help would be appreciated!  It's been a while since I've used linux, but I'd love to get this Inspiron 700m up and running well for my brother.

---

### Post by boarder2 on 2010-08-01
Wiki still says the same thing and I'm still getting the same errors.  Anyone have any suggestions?

---

### Post by boarder2 on 2010-08-01
Never mind, it appears I had some weird entries in my software sources.  Removed duplicates and other stuff and everything's installed now.

---

