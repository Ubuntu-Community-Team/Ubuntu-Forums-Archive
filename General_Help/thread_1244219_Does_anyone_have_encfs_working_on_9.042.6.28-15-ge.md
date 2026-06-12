---
title: "Does anyone have encfs working on 9.04/2.6.28-15-generic AMD64?"
date: 2009-08-19
forum: General Help
---

### Post by Steven Edwards on 2009-08-19
I'm trying to install encfs on my laptop and I keep getting the error that I need the fuse module loaded.  sudo modprobe fuse says that fuse isn't installed, but:

```
steven@ubuntu:~$ dpkg -l | grep fuse
ii  fuse-utils                                 2.7.4-1.1ubuntu4                     Filesystem in USErspace (utilities)
ii  gvfs-fuse                                  1.2.2-0ubuntu2                       userspace virtual filesystem - fuse server
ii  libfuse-dev                                2.7.4-1.1ubuntu4                     Filesystem in USErspace (development files)
ii  libfuse2                                   2.7.4-1.1ubuntu4                     Filesystem in USErspace library
``` I've read that it has to do with FUSE being built in to the kernel now, but I have seen no solutions.

Does anyone have any?

Thanks,

Steven

p.s., I have it working on my desktop--i386 9.04/2.6.28-11-generic--so I know the general routine

---

