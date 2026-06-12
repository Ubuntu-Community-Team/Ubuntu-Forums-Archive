---
title: "compile kernel 2.6.31-20-generic-pae"
date: 2010-02-24
forum: General Help
---

### Post by kenjiru on 2010-02-24
Hello,

I want to compile a custom kernel, because I need a path for a device. Here is what I've done:

```

$ cd /media/work/temp/
$ apt-get build-dep --no-install-recommends linux-image-$(uname -r)
$ apt-get source linux-image-$(uname -r)
$ cd linux-2.6.31
$ cp /boot/config-`uname -r` ./.config
$ make menuconfig
HOSTCC  scripts/basic/fixdep
/bin/sh: scripts/basic/fixdep: Permission denied
make[1]: *** [scripts/basic/fixdep] Error 126
make: *** [scripts_basic] Error 2

```

What did I do wrong?

---

### Post by kenjiru on 2010-03-05
Solved it. I didn't have the exec flag set for the partition with the source code.

---

