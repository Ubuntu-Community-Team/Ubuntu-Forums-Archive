---
title: "&quot;/lib/modules/($kernel-version)/build&quot; links to sources folder"
date: 2011-02-15
forum: General Help
---

### Post by simonbcn on 2011-02-15
I'm compiling the vanilla kernel 2.6.37 with this guide: [https://wiki.ubuntu.com/KernelTeam/GitKernelBuild](https://wiki.ubuntu.com/KernelTeam/GitKernelBuild)
I compile with 
```
fakeroot make-kpkg --initrd --append-to-version=-custom --overlay-dir=$HOME/ubuntu-package kernel_image kernel_headers
```When I install the created packages (*header and image*), it creates two links in /lib/modules/($version)/: *build* and *src*, but both point to folder with sources, from where I've compiled.

This is an error: *build* should be point to */usr/src/linux-headers-...*
How can I fix this? 

By other side, I don't want that it creates the src link, how can I change this?
Thanks.

**ADD**:
I have extracted an official kernel header package of Ubuntu and I have seen that there is a link /lib/modules/($version)/build points to /usr/src/linux-headers-$version/ 
But in my header package, this link isn't created.
And in image package there isn't /lib/modules/($version)/source nor build link.
If I'm using its scripts, What am I doing wrong? :-(

**ADD²**:
It's important because if this link isn't created correctly, *dkms* fails.

---

