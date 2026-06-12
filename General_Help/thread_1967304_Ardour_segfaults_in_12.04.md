---
title: "Ardour segfaults in 12.04"
date: 2012-04-28
forum: General Help
---

### Post by lykwydchykyn on 2012-04-28
After updating my DAW computer to precise from oneiric, ardour no longer launches.  Instead, it segfaults every time it runs.

I've tried both ardour and ardour-i686.  I've purge and reinstalled, and even compiled it from source using apt-src.  

It was working great in oneiric (actually, the same version of ardour was working in oneiric, because I'd backported it from precise).  I can't get past the segfault for the life of me.

Anyone else experiencing this?

---

### Post by poonjabi on 2012-04-28
> **lykwydchykyn said:**
> After updating my DAW computer to precise from oneiric, ardour no longer launches.  Instead, it segfaults every time it runs.

I've tried both ardour and ardour-i686.  I've purge and reinstalled, and even compiled it from source using apt-src.  

It was working great in oneiric (actually, the same version of ardour was working in oneiric, because I'd backported it from precise).  I can't get past the segfault for the life of me.

Anyone else experiencing this?

I'm on Ubuntu 12.04, and it is installing just fine. Let me test it.

---

### Post by poonjabi on 2012-04-28
Nope, no segfaults here.  Running a freshly installed (today) Ubuntu 12.04 64-bit Intel system. MSI MB in the ATX case. Bought it a couple of months ago too. Nothing fancy. Default everything. I'm even running a Nvidea in Ubuntu 3D (video on-board not pci-express mind you), and still no trouble today. Smooth as silk. jockey-gtk even installed the video driver perfectly for me. No issues.

---

### Post by lykwydchykyn on 2012-04-28
Maybe I need to do a fresh install.  I had installed a lot of third-party things on Oneiric from some PPAs, medibuntu, etc.  I thought I got rid of it all on upgrade, but maybe not.

---

### Post by lykwydchykyn on 2012-04-28
I was remembering how much of a chore it was to get certain pieces of hardware working on this (which are still working post upgrade), so I want to fix this if possible.

Ardour, Audacity, and Hydrogen all segfault, and all with the same error:

```

Program received signal SIGSEGV, Segmentation fault.
lk0x023c6e78 in __strcpy_chk () from /lib/i386-linux-gnu/libc.so.6

```

Does anyone have an idea what this might be?  I reinstalled libc6 and libc6-bin from the repositories, made sure to purge all non-official packages, etc.  The only unofficial stuff I'm running is a lowlatency kernel, from abogani's ppa.

Edit:  Here's the crash after I installed libc6-dbg
```

Program received signal SIGSEGV, Segmentation fault.
__strcpy_chk (dest=0xbfffed4c "", src=0x0, destlen=1024) at strcpy_chk.c:38
38      strcpy_chk.c: No such file or directory.

```

---

### Post by denisbathome on 2012-05-05
Possible answer: [https://bugs.launchpad.net/ubuntu/+source/audacity/+bug/990683](https://bugs.launchpad.net/ubuntu/+source/audacity/+bug/990683)

---

