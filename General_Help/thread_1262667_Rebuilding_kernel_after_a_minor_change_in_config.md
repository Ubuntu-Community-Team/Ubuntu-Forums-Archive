---
title: "Rebuilding kernel after a minor change in config"
date: 2009-09-10
forum: General Help
---

### Post by szilva on 2009-09-10
Hi All,

I am trying to refine my running kernel. The way is similar to this, except I use a vanilla kernel from kernel.org (the relevant steps are from the step number 5), I use "menuconfig" to choose my kernel options:
[https://wiki.ubuntu.com/KernelTeam/GitKernelBuild](https://wiki.ubuntu.com/KernelTeam/GitKernelBuild)

The first make runs well (but very long time), I can install new-built kernel, everithing is OK.

My problem starts with the second attempt to build a kernel:
- I restart the procedure from step 6, applying minor changes (eg. changing a driver to be built into the kernel instead of building a module)
- the next step (make-kpkg clean) I jump over, because I do not want to recompile all of the kernel
- the step 8, building the packages executes very shortly and says that everything is up to date:

root@szilva-laptop:/usr/src/linux# fakeroot make-kpkg --initrd
--append-to-version=-custom-2 kernel_image kernel_headers
exec debian/rules  DEBIAN_REVISION=2.6.30.6-custom2-10.00.Custom
APPEND_TO_VERSION=-custom-2  INITRD=YES  kernel_image kernel_headers
/usr/bin/make -f ./debian/rules
        debian/stamp/binary/pre-linux-image-2.6.30.6-custom2
make[1]: Entering directory `/usr/src/linux-2.6.30.6'
make[1]: `debian/stamp/binary/pre-linux-image-2.6.30.6-custom2' is up to date.
make[1]: Leaving directory `/usr/src/linux-2.6.30.6'
/usr/bin/make -f ./debian/rules
debian/stamp/binary/pre-linux-headers-2.6.30.6-custom2
make[1]: Entering directory `/usr/src/linux-2.6.30.6'
make[1]: `debian/stamp/binary/pre-linux-headers-2.6.30.6-custom2' is up to date.
make[1]: Leaving directory `/usr/src/linux-2.6.30.6'
root@szilva-laptop:/usr/src/linux#


Please help me, what command should I use in place of step 7 (instead of make-kpkg clean) if I want to rebuild my newly modified kernel, but I don't want to recompile all of it? 

Regards,
Zoltan

---

