---
title: "make menuconfig returns an error in kernel compilation"
date: 2010-07-12
forum: General Help
---

### Post by Helios747 on 2010-07-12
Hello,

I'm simply trying to compile a vanilla kernel from Kernel.org, I've done it before, however "make menuconfig" returns an error after I've made my changes to the config file.

```
#
# using defaults found in /boot/config-2.6.32-23-generic
#
/boot/config-2.6.32-23-generic:2849:warning: symbol value 'm' invalid for MFD_WM831X
/boot/config-2.6.32-23-generic:2850:warning: symbol value 'm' invalid for MFD_WM8350
/boot/config-2.6.32-23-generic:2851:warning: symbol value 'm' invalid for MFD_WM8350_I2C
/boot/config-2.6.32-23-generic:2856:warning: symbol value 'm' invalid for AB3100_CORE
/boot/config-2.6.32-23-generic:3305:warning: symbol value 'm' invalid for FB_VESA
/boot/config-2.6.32-23-generic:3929:warning: symbol value 'm' invalid for MMC_RICOH_MMC
#
# configuration written to .config
#
((((((((((((MENUCONFIG LAUNCHES AND EVERYTHING IS GOOD SO FAR))))))))))))))

*** End of Linux kernel configuration.
*** Execute 'make' to build the kernel or try 'make help'.

scripts/kconfig/conf -s arch/x86/Kconfig
#
# configuration written to .config
#
make[1]: *** No rule to make target `fig'.  Stop.
make: *** [fig] Error 2
```


Why is make returning that error? I am using a 64-bit kernel.

fig? :p

---

### Post by anglican on 2010-07-13
> **Helios747 said:**
> Hello,

I'm simply trying to compile a vanilla kernel from Kernel.org, I've done it before, however "make menuconfig" returns an error after I've made my changes to the config file.

```
#
# using defaults found in /boot/config-2.6.32-23-generic
#
/boot/config-2.6.32-23-generic:2849:warning: symbol value 'm' invalid for MFD_WM831X
/boot/config-2.6.32-23-generic:2850:warning: symbol value 'm' invalid for MFD_WM8350
/boot/config-2.6.32-23-generic:2851:warning: symbol value 'm' invalid for MFD_WM8350_I2C
/boot/config-2.6.32-23-generic:2856:warning: symbol value 'm' invalid for AB3100_CORE
/boot/config-2.6.32-23-generic:3305:warning: symbol value 'm' invalid for FB_VESA
/boot/config-2.6.32-23-generic:3929:warning: symbol value 'm' invalid for MMC_RICOH_MMC
#
# configuration written to .config
#
((((((((((((MENUCONFIG LAUNCHES AND EVERYTHING IS GOOD SO FAR))))))))))))))

*** End of Linux kernel configuration.
*** Execute 'make' to build the kernel or try 'make help'.

scripts/kconfig/conf -s arch/x86/Kconfig
#
# configuration written to .config
#
make[1]: *** No rule to make target `fig'.  Stop.
make: *** [fig] Error 2
```
Why is make returning that error? I am using a 64-bit kernel.

fig? :p
I think you'll need to provide detail on exactly what you've done here. Did you manually edit a config file (i.e. with an editor)? It looks to me like a file somewhere has been messed up (perhaps an accidental press of [Return] while editing). Try reinstalling the kernel source and having another go.

H

---

### Post by Helios747 on 2010-07-13
Hi. I just used "make menuconfig" and let the compiler to the work.


but, I reinstalled my root partition yesterday because I goofed something up and now all is working. :D

Don't know why or how, but I'm not complaining. I'll mark this as solved.

---

