---
title: "Why every update makes kernel try to reinstall?"
date: 2009-06-26
forum: General Help
---

### Post by Lockheed on 2009-06-26
I compiled new kernel few days ago but since then every time I use Update Manager to upgrade some of the software, in the process kernel tries to install itself, too.

This is hand what Update Manager produces (most of the .... is because I omited some things during typing):
```
E: linux-image-2.6.30: subprocess post-installation script returned error exit status 2

setting up pulseaudio-modyle-..........
Processing tiggers for libc6...
ldconfig deferred processing now taking place
Errors were encountered while processing:
 linux-image-2.6.30
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install. Trying to recover:
Running depmod.
Finding valid ramdisk creators.
Using mkinitramfs-kpkg to build the ramdisk.
Not updating initrd...........
Not updaring symbolic links....
Running postinst hook script update-grub.
Searching for GRUB insallation dir....
....
.


...
Updaring menu.lst ... done
Examining /etc/kernel/postinst.d
run-parts: execuring dkms
...
..
..
Failed do process /etc/kernel/postinst.d at /var/lib/dpkg/info/linux-image-2.6.30.posinst line 1186
dpkg: error processing linux-image-2.6.30 (--configure):
 subprocess post-installation script returned error exit status 2
Errors were encountered while processing:
 linux-image-2.6.30
```

---

### Post by fragos on 2009-06-26
Compiling doesn't update the DEB package data base use by the Update Manager. That may be your problem.

---

