---
title: "NVIDIA Proprietary Driver won't build on 2.6.32.24"
date: 2010-09-01
forum: General Help
---

### Post by wd5gnr on 2010-09-01
I have used the NVidia proprietary drivers for awhile. Yes, I know about nv and I even know about the prepackaged ones, but I've never minded getting the latest from NVidia, dropping out of X, and running the install which automatically rebuilds everything.

I recently took the synaptic update to 2.6.32-24. It worked fine and -- I guess -- migrated my driver. I didn't think about it. For no particular reason today I tried to build the latest NVIDIA driver (256.53 -- had been on an earlier 256 series). The build failed with some conftest failures. Even trying to rebuild the working driver failed.

Reverting to 2.6.32-23 allowed both to be built and they work. So something the NVIDIA installer is expecting headerwise must be different between 2.6.32-23 and -24.

Any ideas?

---

### Post by btown1987 on 2010-09-01
[http://ubuntuforums.org/showthread.php?t=1467074](http://ubuntuforums.org/showthread.php?t=1467074)

this got it installed for me.

---

### Post by realzippy on 2010-09-01
*the build failed with some conftest failures*

might be interesting which...

---

### Post by wd5gnr on 2010-09-01
Well I didn't include them because frankly they are bogus. If you look at how conftest.h is set up in the build process it is clearly misidentifying something and then populating conftest.h with #error statements, so as a developer that's not really interesting. Its a symptom not a cause (did I mention I've been doing C and C++ development for 25 years?).

However, to satiate your curiosity:
```

   /tmp/selfgz4181/NVIDIA-Linux-x86_64-256.53/kernel/conftest.h:1:2: error: #er
   ror remap_page_range() conftest failed!
   /tmp/selfgz4181/NVIDIA-Linux-x86_64-256.53/kernel/conftest.h:3:2: error: #er
   ror vmap() conftest failed!
   /tmp/selfgz4181/NVIDIA-Linux-x86_64-256.53/kernel/conftest.h:4:2: error: #er
   ror agp_backend_acquire() conftest failed!
   /tmp/selfgz4181/NVIDIA-Linux-x86_64-256.53/kernel/conftest.h:23:2: error: #e
   rror kmem_cache_create() conftest failed!
   /tmp/selfgz4181/NVIDIA-Linux-x86_64-256.53/kernel/conftest.h:24:2: error: #e
   rror on_each_cpu() conftest failed!
   /tmp/selfgz4181/NVIDIA-Linux-x86_64-256.53/kernel/conftest.h:25:2: error: #e
   rror smp_call_function() conftest failed!
   /tmp/selfgz4181/NVIDIA-Linux-x86_64-256.53/kernel/conftest.h:31:2: error: #e
   rror INIT_WORK() conftest failed!
   /tmp/selfgz4181/NVIDIA-Linux-x86_64-256.53/kernel/conftest.h:32:2: error: #e
   rror acpi_walk_namespace() conftest failed!


```

---

### Post by wd5gnr on 2010-09-01
> **btown1987 said:**
> [http://ubuntuforums.org/showthread.php?t=1467074](http://ubuntuforums.org/showthread.php?t=1467074)

this got it installed for me.

Thanks, but this seems to describe the normal way you do this. That works on every kernel except the latest. 

So yeah I made sure /usr/src/linux was the right link and the headers all all there etc. It is a build error, not a loading error. So even if the other modules were loading, the NVidia module would still build.

Right now I'm just back one kernel rev -- rebuilt the driver and no worries. But it also means I can't upgrade the kernel until I resolve this.

---

### Post by wd5gnr on 2010-09-03
What I did for now -- and yes, I know the risks of doing so -- was to temporarily rename /usr/src/linux-headers-2.6.32-24 out of the way and then made a symlink so that 2.6.32-23 stood in for it. Works fine. So there is definitely some difference between the headers that is causing several of the conftest.sh tests to fail.

It is odd that no one else is reporting this, yet the fact that I can install on an older kernel makes me think it is NOT related to my specific setup.

---

