---
title: "Kernel questions"
date: 2010-09-21
forum: General Help
---

### Post by fmouse on 2010-09-21
I have a number of questions regarding the Ubuntu linux kernels and the kernel source code.  If there's a HOWTO or a FAQ page which covers these, please give me a reference.

*  I note that my upgrade to lucid lynx has 2 different kernels, both of them referenced in the grub menu.lst file.  Each of these has its own initrd file and module tree.  One version ends in "-386" and the other ends in "-generic".  The system boots the "generic" kernel by default, although in previous versions the "386" kernel booted by default.  What's the difference between these kernels?

*  The linux-source package installs the latest kernel source "with Ubuntu patches".  Is this source patched so that the same capabilities and modules are enabled/built by default as is the case for the running (pre-built binary "generic") kernel?

*  Since the drive holding the root filesystem in /etc/fstab is specified by a UUID, I assume I'll need a custom initrd in /boot for any custom kernel I build.  Is there a tool, a script and/or other resources for building this?  I've built initrd files before but it's been a while, and I recall that it was a lot of hassle.  I assume Ubuntu probably has a tool to make it relatively easy.

---

### Post by Enigmapond on 2010-09-21
Maybe this will give some answers...
[http://en.wikipedia.org/wiki/Linux_kernel](http://en.wikipedia.org/wiki/Linux_kernel)

---

### Post by fmouse on 2010-09-21
> **Enigmapond said:**
> Maybe this will give some answers...
[http://en.wikipedia.org/wiki/Linux_kernel](http://en.wikipedia.org/wiki/Linux_kernel)

Not really, Enigmapond, but thanks anyway :)  I've been compiling Linux kernels since 1.x and know probably a good deal more than the average user about the subject in general, but I'm looking for information on Ubuntu-specific tools and resources, and information on what's up with the different pre-compiled Ubuntu kernels which I have installed.

---

