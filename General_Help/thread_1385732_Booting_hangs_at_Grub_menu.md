---
title: "Booting hangs at Grub menu"
date: 2010-01-19
forum: General Help
---

### Post by ant2ne on 2010-01-19
not related to this thread
[http://ubuntuforums.org/showthread.php?t=1385725]("http://ubuntuforums.org/showthread.php?t=1385725")

On a few VMs. Sometimes, when powering them on I get the GNU GRUB menu...
```

GNU GRUB version 1.97~beta4

Ubuntu, Linux 2.6.31-14-generic
ubuntu, Linux 2.6.31-14-generic (recovery mode)
Memory test (memtest86+)
Memory test (memtest86+, serial console 115200)
etc

```But there is no countdown for a default boot. It just hangs here. Indefinitely. Until I make a choice by pressing the enter key with "Ubuntu, Linux 2.6.31-14-generic" highlighted (default). I don't know if this is because the VM may not have been shutdown properly or what the case is, but this is unacceptable as I need these systems to continue to boot and get back on line regardless of the reason they were powered off.

I'm hoping that this is a grub configuration that I can easily set.

---

### Post by meierfra. on 2010-01-19
Try this

[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:recordfail](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:recordfail)

---

### Post by ant2ne on 2010-01-19
this maybe not the best solution. 
I edited /boot/grub/grub.cfg and removed all references to timeout=-1 or timeout=0 to timeout=10. I wonder if that will work.

---

### Post by meierfra. on 2010-01-20
That will work. But grub.cfg gets overwritten any time "update-grub" is run (for example during kernel  updates).  The link I posted contains a permanent solution.

---

