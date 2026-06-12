---
title: "dpkg -l '*fglrx*' says fglrx not fully installed, will this fix it?"
date: 2011-05-10
forum: General Help
---

### Post by maddbaron on 2011-05-10
Ran dpkg -l '*fglrx*'
got this
```
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Conf-files/Unpacked/halF-conf/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name           Version        Description
+++-==============-==============-============================================
ii  fglrx          2:8.801-0ubunt Video driver for the ATI graphics accelerato
ii  fglrx-amdcccle 2:8.801-0ubunt Catalyst Control Center for the ATI graphics
un  fglrx-control  <none>         (no description available)
un  fglrx-control- <none>         (no description available)
un  fglrx-dev      <none>         (no description available)
un  fglrx-driver   <none>         (no description available)
un  fglrx-driver-d <none>         (no description available)
un  fglrx-kernel-s <none>         (no description available)
ii  fglrx-modalias 2:8.821-0ubunt Identifiers supported by the ATI graphics dr
un  xfree86-driver <none>         (no description available)
un  xfree86-driver <none>         (no description available)
un  xorg-driver-fg <none>         (no description available)
un  xorg-driver-fg <none>         (no description available)

```

then ran 
```
 locate fglrx
/etc/X11/xorg.conf.fglrx-0
/etc/X11/xorg.conf.fglrx-1
/etc/X11/Xsession.d/10fglrx
/etc/acpi/fglrx-powermode.sh
/etc/acpi/events/fglrx-ac-aticonfig
/etc/acpi/events/fglrx-lid-aticonfig
/etc/alternatives/10fglrx
/etc/alternatives/fglrx_dri
/etc/alternatives/fglrx_drv
/etc/alternatives/fglrx_modconf
/etc/alternatives/fglrxinfo
/etc/modprobe.d/fglrx.conf
/lib/fglrx
/lib/fglrx/modprobe.conf
/lib/modules/2.6.35-27-generic/updates/dkms/fglrx.ko
/lib/modules/2.6.35-28-generic/updates/dkms/fglrx.ko
/usr/bin/fglrxinfo
/usr/lib/fglrx
/usr/lib/dri/fglrx_dri.so
/usr/lib/fglrx/10fglrx
/usr/lib/fglrx/bin
/usr/lib/fglrx/dri
/usr/lib/fglrx/etc
/usr/lib/fglrx/ld.so.conf
/usr/lib/fglrx/libAMDXvBA.cap
/usr/lib/fglrx/libAMDXvBA.so.1
/usr/lib/fglrx/libAMDXvBA.so.1.0
/usr/lib/fglrx/libGL.so
/usr/lib/fglrx/libGL.so.1
/usr/lib/fglrx/libGL.so.1.2
/usr/lib/fglrx/libXvBAW.so.1
/usr/lib/fglrx/libXvBAW.so.1.0
/usr/lib/fglrx/libatiadlxx.so
/usr/lib/fglrx/libaticalcl.so
/usr/lib/fglrx/libaticaldd.so
/usr/lib/fglrx/libaticalrt.so
/usr/lib/fglrx/libatiuki.so.1
/usr/lib/fglrx/libatiuki.so.1.0
/usr/lib/fglrx/libfglrx_dm.so.1
/usr/lib/fglrx/libfglrx_dm.so.1.0
/usr/lib/fglrx/libfglrx_gamma.so.1
/usr/lib/fglrx/libfglrx_gamma.so.1.0
/usr/lib/fglrx/xorg
/usr/lib/fglrx/bin/amdcccle
/usr/lib/fglrx/bin/amdnotifyui
/usr/lib/fglrx/bin/amdupdaterandrconfig
/usr/lib/fglrx/bin/amdxdg-su
/usr/lib/fglrx/bin/aticonfig
/usr/lib/fglrx/bin/atieventsd
/usr/lib/fglrx/bin/atiodcli
/usr/lib/fglrx/bin/atiode
/usr/lib/fglrx/bin/fgl_glxgears
/usr/lib/fglrx/bin/fglrx_xgamma
/usr/lib/fglrx/bin/fglrxinfo
/usr/lib/fglrx/dri/fglrx_dri.so
/usr/lib/fglrx/etc/ati
/usr/lib/fglrx/etc/ati/amdpcsdb
/usr/lib/fglrx/etc/ati/amdpcsdb.default
/usr/lib/fglrx/etc/ati/atiogl.xml
/usr/lib/fglrx/etc/ati/authatieventsd.sh
/usr/lib/fglrx/etc/ati/control
/usr/lib/fglrx/etc/ati/logo.xbm.example
/usr/lib/fglrx/etc/ati/logo_mask.xbm.example
/usr/lib/fglrx/etc/ati/signature
/usr/lib/fglrx/xorg/modules
/usr/lib/fglrx/xorg/modules/amdxmm.so
/usr/lib/fglrx/xorg/modules/drivers
/usr/lib/fglrx/xorg/modules/extensions
/usr/lib/fglrx/xorg/modules/glesx.so
/usr/lib/fglrx/xorg/modules/linux
/usr/lib/fglrx/xorg/modules/drivers/fglrx_drv.so
/usr/lib/fglrx/xorg/modules/extensions/libglx.so
/usr/lib/fglrx/xorg/modules/linux/libfglrxdrm.so
/usr/lib/xorg/modules/drivers/fglrx_drv.so
/usr/share/fglrx
/usr/share/app-install/desktop/fglrx-driver.desktop
/usr/share/apport/package-hooks/source_fglrx-installer.py
/usr/share/doc/fglrx
/usr/share/doc/fglrx-amdcccle
/usr/share/doc/fglrx-modaliases
/usr/share/doc/fglrx/README.Debian
/usr/share/doc/fglrx/articles
/usr/share/doc/fglrx/changelog.Debian.gz
/usr/share/doc/fglrx/configure.html
/usr/share/doc/fglrx/copyright
/usr/share/doc/fglrx/driverfaq.html
/usr/share/doc/fglrx/examples
/usr/share/doc/fglrx/index.html
/usr/share/doc/fglrx/installer.html
/usr/share/doc/fglrx/issues.html
/usr/share/doc/fglrx/linuxfaq.html
/usr/share/doc/fglrx/tips-linux.html
/usr/share/doc/fglrx/user-manual
/usr/share/doc/fglrx/articles/1gbhang.html
/usr/share/doc/fglrx/articles/4461.html
/usr/share/doc/fglrx/articles/4462.html
/usr/share/doc/fglrx/articles/4463.html
/usr/share/doc/fglrx/articles/4464.html
/usr/share/doc/fglrx/articles/4469.html
/usr/share/doc/fglrx/articles/4470.html
/usr/share/doc/fglrx/articles/4475.html
/usr/share/doc/fglrx/articles/4478.html
/usr/share/doc/fglrx/articles/4479.html
/usr/share/doc/fglrx/articles/4480.html
/usr/share/doc/fglrx/articles/4481.html
/usr/share/doc/fglrx/articles/4482.html
/usr/share/doc/fglrx/articles/4483.html
/usr/share/doc/fglrx/articles/4484.html
/usr/share/doc/fglrx/articles/4485.html
/usr/share/doc/fglrx/articles/corruptstereo.html
/usr/share/doc/fglrx/articles/corruptvtswitch.html
/usr/share/doc/fglrx/articles/devshm.html
/usr/share/doc/fglrx/articles/dga3dhang.html
/usr/share/doc/fglrx/articles/doom3corrupt.html
/usr/share/doc/fglrx/articles/dualheadvideo.html
/usr/share/doc/fglrx/articles/laptopsuspend.html
/usr/share/doc/fglrx/articles/missingdrmheaders.html
/usr/share/doc/fglrx/articles/mousecursorhang.html
/usr/share/doc/fglrx/articles/no3d-aiw8500dv.html
/usr/share/doc/fglrx/articles/no3d-kt400.html
/usr/share/doc/fglrx/articles/nomembercount.html
/usr/share/doc/fglrx/articles/pcie3dmemoryleak.html
/usr/share/doc/fglrx/articles/r420blankdisplay.html
/usr/share/doc/fglrx/articles/rv280dviblankdisplay.html
/usr/share/doc/fglrx/articles/rv350springdale.html
/usr/share/doc/fglrx/articles/secondheadcorruption.html
/usr/share/doc/fglrx/articles/xf86_enodev.html
/usr/share/doc/fglrx/articles/xrestartpcie.html
/usr/share/doc/fglrx/articles/xvsatshift.html
/usr/share/doc/fglrx/examples/etc
/usr/share/doc/fglrx/examples/etc/acpi
/usr/share/doc/fglrx/examples/etc/init.d
/usr/share/doc/fglrx/examples/etc/acpi/ati-powermode.sh
/usr/share/doc/fglrx/examples/etc/acpi/events
/usr/share/doc/fglrx/examples/etc/acpi/events/a-ac-aticonfig
/usr/share/doc/fglrx/examples/etc/acpi/events/a-lid-aticonfig
/usr/share/doc/fglrx/examples/etc/init.d/atieventsd.sh
/usr/share/doc/fglrx/user-manual/index.html
/usr/share/doc/fglrx-amdcccle/changelog.Debian.gz
/usr/share/doc/fglrx-amdcccle/copyright
/usr/share/doc/fglrx-modaliases/changelog.Debian.gz
/usr/share/doc/fglrx-modaliases/copyright
/usr/share/fglrx/amdcccle.desktop
/usr/share/fglrx/amdccclesu.desktop
/usr/share/fglrx/atigetsysteminfo.sh
/usr/share/icons/AwOken/clear/128x128/apps/fglrx-amdcccle.png
/usr/share/icons/AwOken/clear/24x24/apps/fglrx-amdcccle.png
/usr/share/icons/AwOkenDark/clear/128x128/apps/fglrx-amdcccle.png
/usr/share/icons/AwOkenDark/clear/24x24/apps/fglrx-amdcccle.png
/usr/share/icons/Elegant-AwOken/clear/128x128/apps/fglrx-amdcccle.png
/usr/share/icons/Elegant-AwOken/clear/16x16/apps/fglrx-amdcccle.png
/usr/share/icons/Elegant-AwOken/clear/22x22/apps/fglrx-amdcccle.png
/usr/share/icons/Elegant-AwOken/clear/24x24/apps/fglrx-amdcccle.png
/usr/share/jockey/handlers/fglrx.py
/usr/share/jockey/handlers/fglrx.pyc
/usr/share/jockey/modaliases/fglrx-modules.alias.override
/usr/share/lintian/overrides/fglrx
/usr/share/lintian/overrides/fglrx-amdcccle
/usr/src/fglrx-8.801
/usr/src/fglrx-8.801/2.6.x
/usr/src/fglrx-8.801/dkms.conf
/usr/src/fglrx-8.801/drm.h
/usr/src/fglrx-8.801/drmP.h
/usr/src/fglrx-8.801/drm_compat.h
/usr/src/fglrx-8.801/drm_os_linux.h
/usr/src/fglrx-8.801/drm_proc.h
/usr/src/fglrx-8.801/fglrxko_pci_ids.h
/usr/src/fglrx-8.801/firegl_public.c
/usr/src/fglrx-8.801/firegl_public.h
/usr/src/fglrx-8.801/kcl_acpi.c
/usr/src/fglrx-8.801/kcl_acpi.h
/usr/src/fglrx-8.801/kcl_agp.c
/usr/src/fglrx-8.801/kcl_agp.h
/usr/src/fglrx-8.801/kcl_config.h
/usr/src/fglrx-8.801/kcl_debug.c
/usr/src/fglrx-8.801/kcl_debug.h
/usr/src/fglrx-8.801/kcl_io.c
/usr/src/fglrx-8.801/kcl_io.h
/usr/src/fglrx-8.801/kcl_ioctl.c
/usr/src/fglrx-8.801/kcl_ioctl.h
/usr/src/fglrx-8.801/kcl_osconfig.h
/usr/src/fglrx-8.801/kcl_pci.c
/usr/src/fglrx-8.801/kcl_pci.h
/usr/src/fglrx-8.801/kcl_str.c
/usr/src/fglrx-8.801/kcl_str.h
/usr/src/fglrx-8.801/kcl_type.h
/usr/src/fglrx-8.801/kcl_wait.c
/usr/src/fglrx-8.801/kcl_wait.h
/usr/src/fglrx-8.801/libfglrx_ip.a.GCC3
/usr/src/fglrx-8.801/libfglrx_ip.a.GCC4
/usr/src/fglrx-8.801/make.sh
/usr/src/fglrx-8.801/patches
/usr/src/fglrx-8.801/2.6.x/Makefile
/usr/src/fglrx-8.801/patches/add-compatibility-with-2.6.36-kernels.patch
/usr/src/fglrx-8.801/patches/fglrx-2.6.37.patch
/usr/src/fglrx-8.801/patches/rt_preempt_28.patch
/usr/src/fglrx-8.801/patches/rt_preempt_31.patch
/usr/src/fglrx-8.801/patches/use-cflags_module-together-with-modflags.patch
/var/cache/jockey/fglrx.noconf
/var/lib/dkms/fglrx
/var/lib/dkms/fglrx/8.801
/var/lib/dkms/fglrx/kernel-2.6.35-27-generic-i686
/var/lib/dkms/fglrx/kernel-2.6.35-28-generic-i686
/var/lib/dkms/fglrx/8.801/2.6.35-27-generic
/var/lib/dkms/fglrx/8.801/2.6.35-28-generic
/var/lib/dkms/fglrx/8.801/build
/var/lib/dkms/fglrx/8.801/source
/var/lib/dkms/fglrx/8.801/2.6.35-27-generic/i686
/var/lib/dkms/fglrx/8.801/2.6.35-27-generic/i686/log
/var/lib/dkms/fglrx/8.801/2.6.35-27-generic/i686/module
/var/lib/dkms/fglrx/8.801/2.6.35-27-generic/i686/log/make.log
/var/lib/dkms/fglrx/8.801/2.6.35-27-generic/i686/module/fglrx.ko
/var/lib/dkms/fglrx/8.801/2.6.35-28-generic/i686
/var/lib/dkms/fglrx/8.801/2.6.35-28-generic/i686/log
/var/lib/dkms/fglrx/8.801/2.6.35-28-generic/i686/module
/var/lib/dkms/fglrx/8.801/2.6.35-28-generic/i686/log/make.log
/var/lib/dkms/fglrx/8.801/2.6.35-28-generic/i686/module/fglrx.ko
/var/lib/dkms/fglrx/8.801/build/2.6.x
/var/lib/dkms/fglrx/8.801/build/dkms.conf
/var/lib/dkms/fglrx/8.801/build/drm.h
/var/lib/dkms/fglrx/8.801/build/drmP.h
/var/lib/dkms/fglrx/8.801/build/drm_compat.h
/var/lib/dkms/fglrx/8.801/build/drm_os_linux.h
/var/lib/dkms/fglrx/8.801/build/drm_proc.h
/var/lib/dkms/fglrx/8.801/build/fglrxko_pci_ids.h
/var/lib/dkms/fglrx/8.801/build/firegl_public.c
/var/lib/dkms/fglrx/8.801/build/firegl_public.h
/var/lib/dkms/fglrx/8.801/build/kcl_acpi.c
/var/lib/dkms/fglrx/8.801/build/kcl_acpi.h
/var/lib/dkms/fglrx/8.801/build/kcl_agp.c
/var/lib/dkms/fglrx/8.801/build/kcl_agp.h
/var/lib/dkms/fglrx/8.801/build/kcl_config.h
/var/lib/dkms/fglrx/8.801/build/kcl_debug.c
/var/lib/dkms/fglrx/8.801/build/kcl_debug.h
/var/lib/dkms/fglrx/8.801/build/kcl_io.c
/var/lib/dkms/fglrx/8.801/build/kcl_io.h
/var/lib/dkms/fglrx/8.801/build/kcl_ioctl.c
/var/lib/dkms/fglrx/8.801/build/kcl_ioctl.h
/var/lib/dkms/fglrx/8.801/build/kcl_osconfig.h
/var/lib/dkms/fglrx/8.801/build/kcl_pci.c
/var/lib/dkms/fglrx/8.801/build/kcl_pci.h
/var/lib/dkms/fglrx/8.801/build/kcl_str.c
/var/lib/dkms/fglrx/8.801/build/kcl_str.h
/var/lib/dkms/fglrx/8.801/build/kcl_type.h
/var/lib/dkms/fglrx/8.801/build/kcl_wait.c
/var/lib/dkms/fglrx/8.801/build/kcl_wait.h
/var/lib/dkms/fglrx/8.801/build/libfglrx_ip.a.GCC3
/var/lib/dkms/fglrx/8.801/build/libfglrx_ip.a.GCC4
/var/lib/dkms/fglrx/8.801/build/make.sh
/var/lib/dkms/fglrx/8.801/build/make.sh.log
/var/lib/dkms/fglrx/8.801/build/make.sh.orig
/var/lib/dkms/fglrx/8.801/build/patches
/var/lib/dkms/fglrx/8.801/build/2.6.x/.fglrx.ko.cmd
/var/lib/dkms/fglrx/8.801/build/2.6.x/.fglrx.mod.o.cmd
/var/lib/dkms/fglrx/8.801/build/2.6.x/.fglrx.o.cmd
/var/lib/dkms/fglrx/8.801/build/2.6.x/.firegl_public.o.cmd
/var/lib/dkms/fglrx/8.801/build/2.6.x/.kcl_acpi.o.cmd
/var/lib/dkms/fglrx/8.801/build/2.6.x/.kcl_agp.o.cmd
/var/lib/dkms/fglrx/8.801/build/2.6.x/.kcl_debug.o.cmd
/var/lib/dkms/fglrx/8.801/build/2.6.x/.kcl_io.o.cmd
/var/lib/dkms/fglrx/8.801/build/2.6.x/.kcl_ioctl.o.cmd
/var/lib/dkms/fglrx/8.801/build/2.6.x/.kcl_pci.o.cmd
/var/lib/dkms/fglrx/8.801/build/2.6.x/.kcl_str.o.cmd
/var/lib/dkms/fglrx/8.801/build/2.6.x/.kcl_wait.o.cmd
/var/lib/dkms/fglrx/8.801/build/2.6.x/.libfglrx_ip.a.GCC4.cmd
/var/lib/dkms/fglrx/8.801/build/2.6.x/.tmp_versions
/var/lib/dkms/fglrx/8.801/build/2.6.x/Makefile
/var/lib/dkms/fglrx/8.801/build/2.6.x/Module.symvers
/var/lib/dkms/fglrx/8.801/build/2.6.x/drm.h
/var/lib/dkms/fglrx/8.801/build/2.6.x/drmP.h
/var/lib/dkms/fglrx/8.801/build/2.6.x/drm_compat.h
/var/lib/dkms/fglrx/8.801/build/2.6.x/drm_os_linux.h
/var/lib/dkms/fglrx/8.801/build/2.6.x/drm_proc.h
/var/lib/dkms/fglrx/8.801/build/2.6.x/fglrx.ko
/var/lib/dkms/fglrx/8.801/build/2.6.x/fglrx.mod.c
/var/lib/dkms/fglrx/8.801/build/2.6.x/fglrx.mod.o
/var/lib/dkms/fglrx/8.801/build/2.6.x/fglrx.o
/var/lib/dkms/fglrx/8.801/build/2.6.x/fglrxko_pci_ids.h
/var/lib/dkms/fglrx/8.801/build/2.6.x/firegl_public.c
/var/lib/dkms/fglrx/8.801/build/2.6.x/firegl_public.h
/var/lib/dkms/fglrx/8.801/build/2.6.x/firegl_public.o
/var/lib/dkms/fglrx/8.801/build/2.6.x/kcl_acpi.c
/var/lib/dkms/fglrx/8.801/build/2.6.x/kcl_acpi.h
/var/lib/dkms/fglrx/8.801/build/2.6.x/kcl_acpi.o
/var/lib/dkms/fglrx/8.801/build/2.6.x/kcl_agp.c
/var/lib/dkms/fglrx/8.801/build/2.6.x/kcl_agp.h
/var/lib/dkms/fglrx/8.801/build/2.6.x/kcl_agp.o
/var/lib/dkms/fglrx/8.801/build/2.6.x/kcl_config.h
/var/lib/dkms/fglrx/8.801/build/2.6.x/kcl_debug.c
/var/lib/dkms/fglrx/8.801/build/2.6.x/kcl_debug.h
/var/lib/dkms/fglrx/8.801/build/2.6.x/kcl_debug.o
/var/lib/dkms/fglrx/8.801/build/2.6.x/kcl_io.c
/var/lib/dkms/fglrx/8.801/build/2.6.x/kcl_io.h
/var/lib/dkms/fglrx/8.801/build/2.6.x/kcl_io.o
/var/lib/dkms/fglrx/8.801/build/2.6.x/kcl_ioctl.c
/var/lib/dkms/fglrx/8.801/build/2.6.x/kcl_ioctl.h
/var/lib/dkms/fglrx/8.801/build/2.6.x/kcl_ioctl.o
/var/lib/dkms/fglrx/8.801/build/2.6.x/kcl_osconfig.h
/var/lib/dkms/fglrx/8.801/build/2.6.x/kcl_pci.c
/var/lib/dkms/fglrx/8.801/build/2.6.x/kcl_pci.h
/var/lib/dkms/fglrx/8.801/build/2.6.x/kcl_pci.o
/var/lib/dkms/fglrx/8.801/build/2.6.x/kcl_str.c
/var/lib/dkms/fglrx/8.801/build/2.6.x/kcl_str.h
/var/lib/dkms/fglrx/8.801/build/2.6.x/kcl_str.o
/var/lib/dkms/fglrx/8.801/build/2.6.x/kcl_type.h
/var/lib/dkms/fglrx/8.801/build/2.6.x/kcl_wait.c
/var/lib/dkms/fglrx/8.801/build/2.6.x/kcl_wait.h
/var/lib/dkms/fglrx/8.801/build/2.6.x/kcl_wait.o
/var/lib/dkms/fglrx/8.801/build/2.6.x/libfglrx_ip.a.GCC4
/var/lib/dkms/fglrx/8.801/build/2.6.x/modules.order
/var/lib/dkms/fglrx/8.801/build/2.6.x/.tmp_versions/fglrx.mod
/var/lib/dkms/fglrx/8.801/build/patches/add-compatibility-with-2.6.36-kernels.patch
/var/lib/dkms/fglrx/8.801/build/patches/fglrx-2.6.37.patch
/var/lib/dkms/fglrx/8.801/build/patches/rt_preempt_28.patch
/var/lib/dkms/fglrx/8.801/build/patches/rt_preempt_31.patch
/var/lib/dkms/fglrx/8.801/build/patches/use-cflags_module-together-with-modflags.patch
/var/lib/dpkg/info/fglrx-amdcccle.list
/var/lib/dpkg/info/fglrx-amdcccle.md5sums
/var/lib/dpkg/info/fglrx-modaliases.list
/var/lib/dpkg/info/fglrx-modaliases.md5sums
/var/lib/dpkg/info/fglrx.conffiles
/var/lib/dpkg/info/fglrx.list
/var/lib/dpkg/info/fglrx.md5sums
/var/lib/dpkg/info/fglrx.postinst
/var/lib/dpkg/info/fglrx.postrm
/var/lib/dpkg/info/fglrx.preinst
/var/lib/dpkg/info/fglrx.prerm
/var/lib/dpkg/info/fglrx.shlibs

```

I read on this site
[https://wiki.ubuntu.com/X/Troubleshooting/FglrxInteferesWithRadeonDriver#Problem:%20%20Need%20to%20fully%20remove%20-fglrx%20and%20reinstall%20-ati%20from%20scratch](https://wiki.ubuntu.com/X/Troubleshooting/FglrxInteferesWithRadeonDriver#Problem:%20%20Need%20to%20fully%20remove%20-fglrx%20and%20reinstall%20-ati%20from%20scratch)

I may need to purge then reinstall fglrx... I did this already but I guess it didnt install correctly... is there another way or is the instructions in the link the only way? 

I want to be able to enable desktop effects & get compiz working b4 upgrading to Natty.

Help Please

Thanks in advance

---

### Post by maddbaron on 2011-05-10
anyone?

---

