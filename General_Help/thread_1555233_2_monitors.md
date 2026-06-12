---
title: "2 monitors"
date: 2010-08-17
forum: General Help
---

### Post by Sk8er72 on 2010-08-17
Sorry for my English, I'm from Russia. 
I have many questions, but I have not found the answers. Please help me in them. 

1. I have a laptop and second monitor. Resolution of laptop 1280 * 800, the second monitor resolution 1366 * 768. Help properly configure them. I have the latest driver from Nvidia. One of the problems that my second monitor is now not determined by the second monitor. The picture is show on second monitor, but the computer shows that I have a monitor. Screen:
[IMG]http://i.imgur.com/BfV5f.png[/IMG]

Just when the system boots, login screen for some reason is shown on the second monitor, although the main monitor is selected first (on laptop). 
Screen:
[IMG]http://i.imgur.com/6MHvV.jpg[/IMG]

Please give me simple instructions on how to properly configure / etc/X11/xorg.konf.


2. And now i have another problem. Compiz don't work. It's appeared when i have problem with second monitor. If i wright "compiz" in terminal i see this:
```
compiz (core) - Fatal: glXCreateContext failed
compiz (core) - Error: Failed to manage screen: 0
compiz (core) - Fatal: No managebla screens found on display :0.0

Launching fallback window manager
&#1055;&#1088;&#1077;&#1076;&#1091;&#1087;&#1088;&#1077;&#1078;&#1076;&#1077;&#1085;&#1080;&#1077; &#1084;&#1077;&#1085;&#1077;&#1076;&#1078;&#1077;&#1088;&#1072; &#1086;&#1082;&#1086;&#1085;: &#1059;&#1089;&#1090;&#1088;&#1072;&#1085;&#1077;&#1085;&#1080;&#1077; &#1085;&#1077;&#1076;&#1086;&#1076;&#1077;&#1083;&#1086;&#1082; &#1076;&#1083;&#1103; &#1089;&#1083;&#1086;&#1084;&#1072;&#1085;&#1085;&#1099;&#1093; &#1087;&#1088;&#1080;&#1083;&#1086;&#1078;&#1077;&#1085;&#1080;&#1081; &#1086;&#1090;&#1082;&#1083;&#1102;&#1095;&#1077;&#1085;&#1086;. &#1053;&#1077;&#1082;&#1086;&#1090;&#1086;&#1088;&#1099;&#1077; &#1087;&#1088;&#1080;&#1083;&#1086;&#1078;&#1077;&#1085;&#1080;&#1103; &#1084;&#1086;&#1075;&#1091;&#1090; &#1088;&#1072;&#1073;&#1086;&#1090;&#1072;&#1090;&#1100; &#1085;&#1077; &#1087;&#1088;&#1072;&#1074;&#1080;&#1083;&#1100;&#1085;&#1086;.
```


Please help me. I don't want use windows :)

---

### Post by earthpigg on 2010-08-17
hi,

i suspect that fixing your first problem will resolve your second one, so let's focus on that.

can you show us a screenshot displaying the "X Server Display Configuration", like my attachment below?

next thing: if you want nvidia settings to save the changes you make when you reboot, you have to run it as root and ***not*** from the icon in system -> administration -> NVIDIA X Server Settings.

to change nvidia's settings and ***have the changes saved when you reboot***, you need to start nvidia-settings with this command from a terminal:

```
sudo nvidia-settings
```

---

### Post by Sk8er72 on 2010-08-18
> can you show us a screenshot displaying the "X Server Display Configuration", like my attachment below?
[IMG]http://i.imgur.com/zlHx4.png[/IMG]

> next thing: if you want nvidia settings to save the changes you make when you reboot, you have to run it as root and not from the icon in system -> administration -> NVIDIA X Server Settings.
i know it, and do it :)

---

### Post by Sk8er72 on 2010-08-18
i mended compiz. it's easy, i only reinstall my nvidia video driver.
but now i have other problem. when i write in terminal this:
```
sudo nvidia-settings
```
i have many mistakes:
```
ERROR: Cannot open display 'notebook:0.0'.


ERROR: Unable to assign attribute CursorShadow specified on line 22 of
       configuration file '/home/sk8er/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute CursorShadowAlpha specified on line 23 of
       configuration file '/home/sk8er/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute CursorShadowRed specified on line 24 of
       configuration file '/home/sk8er/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute CursorShadowGreen specified on line 25 of
       configuration file '/home/sk8er/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute CursorShadowBlue specified on line 26 of
       configuration file '/home/sk8er/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute CursorShadowXOffset specified on line 27 of
       configuration file '/home/sk8er/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute CursorShadowYOffset specified on line 28 of
       configuration file '/home/sk8er/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute SyncToVBlank specified on line 29 of
       configuration file '/home/sk8er/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute LogAniso specified on line 30 of
       configuration file '/home/sk8er/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute FSAA specified on line 31 of configuration
       file '/home/sk8er/.nvidia-settings-rc' (no Display connection).


ERROR: Unable to assign attribute TextureSharpen specified on line 32 of
       configuration file '/home/sk8er/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute AllowFlipping specified on line 33 of
       configuration file '/home/sk8er/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute FSAAAppControlled specified on line 34 of
       configuration file '/home/sk8er/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute LogAnisoAppControlled specified on line 35 of
       configuration file '/home/sk8er/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute OpenGLImageSettings specified on line 36 of
       configuration file '/home/sk8er/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute FSAAAppEnhanced specified on line 37 of
       configuration file '/home/sk8er/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute RedBrightness specified on line 38 of
       configuration file '/home/sk8er/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute GreenBrightness specified on line 39 of
       configuration file '/home/sk8er/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute BlueBrightness specified on line 40 of
       configuration file '/home/sk8er/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute RedContrast specified on line 41 of
       configuration file '/home/sk8er/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute GreenContrast specified on line 42 of
       configuration file '/home/sk8er/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute BlueContrast specified on line 43 of
       configuration file '/home/sk8er/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute RedGamma specified on line 44 of
       configuration file '/home/sk8er/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute GreenGamma specified on line 45 of
       configuration file '/home/sk8er/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute BlueGamma specified on line 46 of
       configuration file '/home/sk8er/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute DigitalVibrance specified on line 47 of
       configuration file '/home/sk8er/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute DigitalVibrance specified on line 48 of
       configuration file '/home/sk8er/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute OverscanCompensation specified on line 49 of
       configuration file '/home/sk8er/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute OverscanCompensation specified on line 50 of
       configuration file '/home/sk8er/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute XVideoTextureBrightness specified on line 51
       of configuration file '/home/sk8er/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute XVideoTextureContrast specified on line 52 of
       configuration file '/home/sk8er/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute XVideoTextureHue specified on line 53 of
       configuration file '/home/sk8er/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute XVideoTextureSaturation specified on line 54
       of configuration file '/home/sk8er/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute XVideoTextureSyncToVBlank specified on line
       55 of configuration file '/home/sk8er/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute XVideoSyncToDisplay specified on line 56 of
       configuration file '/home/sk8er/.nvidia-settings-rc' (no Display
       connection).

```
what is this? how i can fix it?

and I have the problem with login screen:
[IMG]http://i.imgur.com/6MHvV.jpg[/IMG]

Please help!

---

### Post by earthpigg on 2010-08-18
can you look again at the example screenshot i provided? that's the screenshot i'd like to see, if possible.

---

### Post by Sk8er72 on 2010-08-19
[IMG]http://i.imgur.com/PITQY.png[/IMG]

---

### Post by realzippy on 2010-08-19
Maybe it helps if you post your *xorg.conf* and your */.nvidia-settings-rc*  also.



```
sudo nvidia-bug-report.sh
```

creates a error log file which you should post also...

---

### Post by Sk8er72 on 2010-08-19
Ok. my xorg.conf
```
# nvidia-settings: X configuration file generated by nvidia-settings
# nvidia-settings:  version 256.44  (buildmeister@builder103.nvidia.com)  Thu Jul 29 01:52:36 PDT 2010


Section "ServerLayout"
    Identifier     "Layout0"
    Screen      0  "Screen0" 0 0
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
    Option         "Xinerama" "0"
EndSection

Section "Files"
EndSection

Section "InputDevice"

    # generated from default
    Identifier     "Mouse0"
    Driver         "mouse"
    Option         "Protocol" "auto"
    Option         "Device" "/dev/psaux"
    Option         "Emulate3Buttons" "no"
    Option         "ZAxisMapping" "4 5"
EndSection

Section "InputDevice"

    # generated from default
    Identifier     "Keyboard0"
    Driver         "kbd"
EndSection

Section "Monitor"

    # HorizSync source: edid, VertRefresh source: edid
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "EMA E192HQ"
    HorizSync       31.0 - 83.0
    VertRefresh     56.0 - 76.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 9600M GT"
    Option         "NoLogo" "1"
EndSection

Section "Screen"
# Removed Option "metamodes" "DFP: nvidia-auto-select +0+0, CRT: nvidia-auto-select +1280+0"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "TwinView" "1"
    Option         "TwinViewXineramaInfoOrder" "DFP-0"
    Option         "metamodes" "CRT: 1366x768_60 +1280+0, DFP: 1280x800_60 +0+0"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection

```

and nvidia log:
```
____________________________________________

Start of NVIDIA bug report log file.  Please include this file
when reporting a graphics driver bug via the nV News NVIDIA
Linux forum (see www.nvnews.net) or by sending email to
'linux-bugs@nvidia.com'.

nvidia-bug-report.sh Version: 6194179

Date: &#1055;&#1090;&#1085; &#1040;&#1074;&#1075; 20 05:50:20 YEKST 2010
uname: Linux notebook 2.6.32-24-generic #39-Ubuntu SMP Wed Jul 28 05:14:15 UTC 2010 x86_64 GNU/Linux

____________________________________________

/etc/issue
Ubuntu 10.04.1 LTS \n \l


____________________________________________

/etc/debian_version
squeeze/sid

____________________________________________

/var/log/nvidia-installer.log
nvidia-installer log file '/var/log/nvidia-installer.log'
creation time: Wed Aug 18 21:51:37 2010
installer version: 256.44

option status:
  license pre-accepted    : false
  update                  : false
  force update            : false
  expert                  : false
  uninstall               : false
  driver info             : false
  precompiled interfaces  : true
  no ncurses color        : false
  query latest version    : false
  OpenGL header files     : true
  no questions            : false
  silent                  : false
  no recursion            : false
  no backup               : false
  kernel module only      : false
  sanity                  : false
  add this kernel         : false
  no runlevel check       : false
  no network              : false
  no ABI note             : false
  no RPMs                 : false
  no kernel module        : false
  force SELinux           : default
  no X server check       : false
  no cc version check     : false
  force tls               : (not specified)
  force compat32 tls      : (not specified)
  X install prefix        : (not specified)
  X library install path  : (not specified)
  X module install path   : (not specified)
  OpenGL install prefix   : (not specified)
  OpenGL install libdir   : (not specified)
  compat32 install chroot : (not specified)
  compat32 install prefix : (not specified)
  compat32 install libdir : (not specified)
  utility install prefix  : (not specified)
  utility install libdir  : (not specified)
  doc install prefix      : (not specified)
  kernel name             : (not specified)
  kernel include path     : (not specified)
  kernel source path      : (not specified)
  kernel output path      : (not specified)
  kernel install path     : (not specified)
  proc mount point        : /proc
  ui                      : (not specified)
  tmpdir                  : /tmp
  ftp mirror              : ftp://download.nvidia.com
  RPM file list           : (not specified)

Using: nvidia-installer ncurses user interface
-> License accepted.
-> Installing NVIDIA driver version 256.44.
-> There appears to already be a driver installed on your system (version: 256.
   44).  As part of installing this driver (version: 256.44), the existing driv
   er will be uninstalled.  Are you sure you want to continue? ('no' will abort
   installation) (Answer: Yes)
-> Performing CC sanity check with CC="cc".
-> Performing CC version check with CC="cc".
-> Kernel source path: '/lib/modules/2.6.32-24-generic/build'
-> Kernel output path: '/lib/modules/2.6.32-24-generic/build'
-> Performing rivafb check.
-> Performing nvidiafb check.
-> Performing Xen check.
-> Cleaning kernel module build directory.
   executing: 'cd ./kernel; make clean'...
-> Building kernel module:
   executing: 'cd ./kernel; make module SYSSRC=/lib/modules/2.6.32-24-generic/b
   uild SYSOUT=/lib/modules/2.6.32-24-generic/build'...
   NVIDIA: calling KBUILD...
   test -e include/linux/autoconf.h -a -e include/config/auto.conf || (		\
   	echo;								\
   	echo "  ERROR: Kernel configuration is invalid.";		\
   	echo "         include/linux/autoconf.h or include/config/auto.conf are mis
   sing.";	\
   	echo "         Run 'make oldconfig && make prepare' on kernel src to fix it
   .";	\
   	echo;								\
   	/bin/false)
   mkdir -p /tmp/selfgz2940/NVIDIA-Linux-x86_64-256.44/kernel/.tmp_versions ; r
   m -f /tmp/selfgz2940/NVIDIA-Linux-x86_64-256.44/kernel/.tmp_versions/*
   make -f scripts/Makefile.build obj=/tmp/selfgz2940/NVIDIA-Linux-x86_64-256.4
   4/kernel
     cc -Wp,-MD,/tmp/selfgz2940/NVIDIA-Linux-x86_64-256.44/kernel/.nv.o.d  -nos
   tdinc -isystem /usr/lib/gcc/x86_64-linux-gnu/4.4.3/include  -Iinclude  -I/us
   r/src/linux-headers-2.6.32-24-generic/arch/x86/include -include include/linu
   x/autoconf.h -Iubuntu/include  -D__KERNEL__ -Wall -Wundef -Wstrict-prototype
   s -Wno-trigraphs -fno-strict-aliasing -fno-common -Werror-implicit-function-
   declaration -Wno-format-security -fno-delete-n
   ull-pointer-checks -O2 -m64 -mtune=generic -mno-red-zone -mcmodel=kernel -fu
   nit-at-a-time -maccumulate-outgoing-args -fstack-protector -DCONFIG_AS_CFI=1
   -DCONFIG_AS_CFI_SIGNAL_FRAME=1 -pipe -Wno-sign-compare -fno-asynchronous-unw
   ind-tables -mno-sse -mno-mmx -mno-sse2 -mno-3dnow -Wframe-larger-than=1024 -
   fno-omit-frame-pointer -fno-optimize-sibling-calls -pg -Wdeclaration-after-s
   tatement -Wno-pointer-sign -fno-strict-overflow -fno-dwarf2-cfi-asm -fconser
   ve-stack -I/tmp/selfgz2940/NVIDIA-Linux-x86_64-256.44/kernel -Wall -MD -Wsig
   n-compare -Wno-cast-qual -Wno-error -D__KERNEL__ -DMODULE -DNVRM -DNV_VERSIO
   N_STRING=\"256.44\" -mcmodel=kernel -mno-red-zone -UDEBUG -U_DEBUG -DNDEBUG 
   -DMODULE -D"KBUILD_STR(s)=#s" -D"KBUILD_BASENAME=KBUILD_STR(nv)"  -D"KBUILD_
   MODNAME=KBUILD_STR(nvidia)"  -c -o /tmp/selfgz2940/NVIDIA-Linux-x86_64-256.4
   4/kernel/.tmp_nv.o /tmp/selfgz2940/NVIDIA-Linux-x86_64-256.44/kernel/nv.c
     set -e ; perl /usr/src/linux-headers-2.6.32-24-generic/scripts/recordmcoun
   t.pl "x86_64" "64" "objdump" "objcopy" "cc" "ld" "nm" "" "" "1" "/tmp/selfgz
   2940/NVIDIA-Linux-x86_64-256.44/kernel/nv.o";
     cc -Wp,-MD,/tmp/selfgz2940/NVIDIA-Linux-x86_64-256.44/kernel/.nv_gvi.o.d  
   -nostdinc -isystem /usr/lib/gcc/x86_64-linux-gnu/4.4.3/include  -Iinclude  -
   I/usr/src/linux-headers-2.6.32-24-generic/arch/x86/include -include include/
   linux/autoconf.h -Iubuntu/include  -D__KERNEL__ -Wall -Wundef -Wstrict-proto
   types -Wno-trigraphs -fno-strict-aliasing -fno-common -Werror-implicit-funct
   ion-declaration -Wno-format-security -fno-delete-null-pointer-checks -O2 -m6
   4 -mtune=generic -mno-red-zone -mcmodel=kernel -funit-at-a-time -maccumulate
   -outgoing-args -fstack-protector -DCONFIG_AS_CFI=1 -DCONFIG_AS_CFI_SIGNAL_FR
   AME=1 -pipe -Wno-sign-compare -fno-asynchronous-unwind-tables -mno-sse -mno-
   mmx -mno-sse2 -mno-3dnow -Wframe-larger-than=1024 -fno-omit-frame-pointer -f
   no-optimize-sibling-calls -pg -Wdeclaration-after-statement -Wno-pointer-sig
   n -fno-strict-overflow -fno-dwarf2-cfi-asm -fconserve-stack -I/tmp/selfgz294
   0/NVIDIA-Linux-x86_64-256.
   44/kernel -Wall -MD -Wsign-compare -Wno-cast-qual -Wno-error -D__KERNEL__ -D
   MODULE -DNVRM -DNV_VERSION_STRING=\"256.44\" -mcmodel=kernel -mno-red-zone -
   UDEBUG -U_DEBUG -DNDEBUG  -DMODULE -D"KBUILD_STR(s)=#s" -D"KBUILD_BASENAME=K
   BUILD_STR(nv_gvi)"  -D"KBUILD_MODNAME=KBUILD_STR(nvidia)"  -c -o /tmp/selfgz
   2940/NVIDIA-Linux-x86_64-256.44/kernel/.tmp_nv_gvi.o /tmp/selfgz2940/NVIDIA-
   Linux-x86_64-256.44/kernel/nv_gvi.c
     set -e ; perl /usr/src/linux-headers-2.6.32-24-generic/scripts/recordmcoun
   t.pl "x86_64" "64" "objdump" "objcopy" "cc" "ld" "nm" "" "" "1" "/tmp/selfgz
   2940/NVIDIA-Linux-x86_64-256.44/kernel/nv_gvi.o";
     cc -Wp,-MD,/tmp/selfgz2940/NVIDIA-Linux-x86_64-256.44/kernel/.nv-vm.o.d  -
   nostdinc -isystem /usr/lib/gcc/x86_64-linux-gnu/4.4.3/include  -Iinclude  -I
   /usr/src/linux-headers-2.6.32-24-generic/arch/x86/include -include include/l
   inux/autoconf.h -Iubuntu/include  -D__KERNEL__ -Wall -Wundef -Wstrict-protot
   ypes -Wno-trigraphs -fno-strict-aliasing -fno-common -Werror-implicit-functi
   on-declaration -Wno-format
   -security -fno-delete-null-pointer-checks -O2 -m64 -mtune=generic -mno-red-z
   one -mcmodel=kernel -funit-at-a-time -maccumulate-outgoing-args -fstack-prot
   ector -DCONFIG_AS_CFI=1 -DCONFIG_AS_CFI_SIGNAL_FRAME=1 -pipe -Wno-sign-compa
   re -fno-asynchronous-unwind-tables -mno-sse -mno-mmx -mno-sse2 -mno-3dnow -W
   frame-larger-than=1024 -fno-omit-frame-pointer -fno-optimize-sibling-calls -
   pg -Wdeclaration-after-statement -Wno-pointer-sign -fno-strict-overflow -fno
   -dwarf2-cfi-asm -fconserve-stack -I/tmp/selfgz2940/NVIDIA-Linux-x86_64-256.4
   4/kernel -Wall -MD -Wsign-compare -Wno-cast-qual -Wno-error -D__KERNEL__ -DM
   ODULE -DNVRM -DNV_VERSION_STRING=\"256.44\" -mcmodel=kernel -mno-red-zone -U
   DEBUG -U_DEBUG -DNDEBUG  -DMODULE -D"KBUILD_STR(s)=#s" -D"KBUILD_BASENAME=KB
   UILD_STR(nv_vm)"  -D"KBUILD_MODNAME=KBUILD_STR(nvidia)"  -c -o /tmp/selfgz29
   40/NVIDIA-Linux-x86_64-256.44/kernel/.tmp_nv-vm.o /tmp/selfgz2940/NVIDIA-Lin
   ux-x86_64-256.44/kernel/nv-vm.c
     set -e ; perl /usr/src/linux-headers-2.6.32-24-generic/scripts/recordmcoun
   t.pl "x86_64" "64" "objdump" "objcopy" "cc" "ld" "nm" "" "" "1" "/tmp/selfgz
   2940/NVIDIA-Linux-x86_64-256.44/kernel/nv-vm.o";
     cc -Wp,-MD,/tmp/selfgz2940/NVIDIA-Linux-x86_64-256.44/kernel/.os-agp.o.d  
   -nostdinc -isystem /usr/lib/gcc/x86_64-linux-gnu/4.4.3/include  -Iinclude  -
   I/usr/src/linux-headers-2.6.32-24-generic/arch/x86/include -include include/
   linux/autoconf.h -Iubuntu/include  -D__KERNEL__ -Wall -Wundef -Wstrict-proto
   types -Wno-trigraphs -fno-strict-aliasing -fno-common -Werror-implicit-funct
   ion-declaration -Wno-format-security -fno-delete-null-pointer-checks -O2 -m6
   4 -mtune=generic -mno-red-zone -mcmodel=kernel -funit-at-a-time -maccumulate
   -outgoing-args -fstack-protector -DCONFIG_AS_CFI=1 -DCONFIG_AS_CFI_SIGNAL_FR
   AME=1 -pipe -Wno-sign-compare -fno-asynchronous-unwind-tables -mno-sse -mno-
   mmx -mno-sse2 -mno-3dnow -Wframe-larger-than=1024 -fno-omit-frame-pointer -f
   no-optimize-sibling-calls -pg -Wdeclaration-after-statement -Wno-pointer-sig
   n -fno-strict-overflow -fno-dwarf2-cfi-asm -fconserve-stack -I/tmp/
   selfgz2940/NVIDIA-Linux-x86_64-256.44/kernel -Wall -MD -Wsign-compare -Wno-c
   ast-qual -Wno-error -D__KERNEL__ -DMODULE -DNVRM -DNV_VERSION_STRING=\"256.4
   4\" -mcmodel=kernel -mno-red-zone -UDEBUG -U_DEBUG -DNDEBUG  -DMODULE -D"KBU
   ILD_STR(s)=#s" -D"KBUILD_BASENAME=KBUILD_STR(os_agp)"  -D"KBUILD_MODNAME=KBU
   ILD_STR(nvidia)"  -c -o /tmp/selfgz2940/NVIDIA-Linux-x86_64-256.44/kernel/.t
   mp_os-agp.o /tmp/selfgz2940/NVIDIA-Linux-x86_64-256.44/kernel/os-agp.c
     set -e ; perl /usr/src/linux-headers-2.6.32-24-generic/scripts/recordmcoun
   t.pl "x86_64" "64" "objdump" "objcopy" "cc" "ld" "nm" "" "" "1" "/tmp/selfgz
   2940/NVIDIA-Linux-x86_64-256.44/kernel/os-agp.o";
     cc -Wp,-MD,/tmp/selfgz2940/NVIDIA-Linux-x86_64-256.44/kernel/.os-interface
   .o.d  -nostdinc -isystem /usr/lib/gcc/x86_64-linux-gnu/4.4.3/include  -Iincl
   ude  -I/usr/src/linux-headers-2.6.32-24-generic/arch/x86/include -include in
   clude/linux/autoconf.h -Iubuntu/include  -D__KERNEL__ -Wall -Wundef -Wstrict
   -prototypes -Wno-trigraphs -fno-strict-aliasing -fno-common -Werror
   -implicit-function-declaration -Wno-format-security -fno-delete-null-pointer
   -checks -O2 -m64 -mtune=generic -mno-red-zone -mcmodel=kernel -funit-at-a-ti
   me -maccumulate-outgoing-args -fstack-protector -DCONFIG_AS_CFI=1 -DCONFIG_A
   S_CFI_SIGNAL_FRAME=1 -pipe -Wno-sign-compare -fno-asynchronous-unwind-tables
   -mno-sse -mno-mmx -mno-sse2 -mno-3dnow -Wframe-larger-than=1024 -fno-omit-fr
   ame-pointer -fno-optimize-sibling-calls -pg -Wdeclaration-after-statement -W
   no-pointer-sign -fno-strict-overflow -fno-dwarf2-cfi-asm -fconserve-stack -I
   /tmp/selfgz2940/NVIDIA-Linux-x86_64-256.44/kernel -Wall -MD -Wsign-compare -
   Wno-cast-qual -Wno-error -D__KERNEL__ -DMODULE -DNVRM -DNV_VERSION_STRING=\"
   256.44\" -mcmodel=kernel -mno-red-zone -UDEBUG -U_DEBUG -DNDEBUG  -DMODULE -
   D"KBUILD_STR(s)=#s" -D"KBUILD_BASENAME=KBUILD_STR(os_interface)"  -D"KBUILD_
   MODNAME=KBUILD_STR(nvidia)"  -c -o /tmp/selfgz2940/NVIDIA-Linux-x86_64-256.4
   4/kernel/.tmp_os-interface.o /tmp/selfgz2940/NVIDIA-Linux-x86_64-256.44/kern
   el/os-interface.c
     set -e ; perl /usr/src/linux-headers-2.6.32-24-generic/scripts/recordmcoun
   t.pl "x86_64" "64" "objdump" "objcopy" "cc" "ld" "nm" "" "" "1" "/tmp/selfgz
   2940/NVIDIA-Linux-x86_64-256.44/kernel/os-interface.o";
     cc -Wp,-MD,/tmp/selfgz2940/NVIDIA-Linux-x86_64-256.44/kernel/.os-registry.
   o.d  -nostdinc -isystem /usr/lib/gcc/x86_64-linux-gnu/4.4.3/include  -Iinclu
   de  -I/usr/src/linux-headers-2.6.32-24-generic/arch/x86/include -include inc
   lude/linux/autoconf.h -Iubuntu/include  -D__KERNEL__ -Wall -Wundef -Wstrict-
   prototypes -Wno-trigraphs -fno-strict-aliasing -fno-common -Werror-implicit-
   function-declaration -Wno-format-security -fno-delete-null-pointer-checks -O
   2 -m64 -mtune=generic -mno-red-zone -mcmodel=kernel -funit-at-a-time -maccum
   ulate-outgoing-args -fstack-protector -DCONFIG_AS_CFI=1 -DCONFIG_AS_CFI_SIGN
   AL_FRAME=1 -pipe -Wno-sign-compare -fno-asynchronous-unwind-tables -mno-sse 
   -mno-mmx -mno-sse2 -mno-3dnow -Wframe-larger-than=1024 -fno-omit-frame-point
   er -fno-optimize-sibling-calls -pg -Wdeclaration-after-statement -Wno-poi
   nter-sign -fno-strict-overflow -fno-dwarf2-cfi-asm -fconserve-stack -I/tmp/s
   elfgz2940/NVIDIA-Linux-x86_64-256.44/kernel -Wall -MD -Wsign-compare -Wno-ca
   st-qual -Wno-error -D__KERNEL__ -DMODULE -DNVRM -DNV_VERSION_STRING=\"256.44
   \" -mcmodel=kernel -mno-red-zone -UDEBUG -U_DEBUG -DNDEBUG  -DMODULE -D"KBUI
   LD_STR(s)=#s" -D"KBUILD_BASENAME=KBUILD_STR(os_registry)"  -D"KBUILD_MODNAME
   =KBUILD_STR(nvidia)"  -c -o /tmp/selfgz2940/NVIDIA-Linux-x86_64-256.44/kerne
   l/.tmp_os-registry.o /tmp/selfgz2940/NVIDIA-Linux-x86_64-256.44/kernel/os-re
   gistry.c
     set -e ; perl /usr/src/linux-headers-2.6.32-24-generic/scripts/recordmcoun
   t.pl "x86_64" "64" "objdump" "objcopy" "cc" "ld" "nm" "" "" "1" "/tmp/selfgz
   2940/NVIDIA-Linux-x86_64-256.44/kernel/os-registry.o";
     cc -Wp,-MD,/tmp/selfgz2940/NVIDIA-Linux-x86_64-256.44/kernel/.nv-i2c.o.d  
   -nostdinc -isystem /usr/lib/gcc/x86_64-linux-gnu/4.4.3/include  -Iinclude  -
   I/usr/src/linux-headers-2.6.32-24-generic/arch/x86/include -include include/
   linux/autoconf.h -Iubuntu/include  -D__KERNEL__ 
   -Wall -Wundef -Wstrict-prototypes -Wno-trigraphs -fno-strict-aliasing -fno-c
   ommon -Werror-implicit-function-declaration -Wno-format-security -fno-delete
   -null-pointer-checks -O2 -m64 -mtune=generic -mno-red-zone -mcmodel=kernel -
   funit-at-a-time -maccumulate-outgoing-args -fstack-protector -DCONFIG_AS_CFI
   =1 -DCONFIG_AS_CFI_SIGNAL_FRAME=1 -pipe -Wno-sign-compare -fno-asynchronous-
   unwind-tables -mno-sse -mno-mmx -mno-sse2 -mno-3dnow -Wframe-larger-than=102
   4 -fno-omit-frame-pointer -fno-optimize-sibling-calls -pg -Wdeclaration-afte
   r-statement -Wno-pointer-sign -fno-strict-overflow -fno-dwarf2-cfi-asm -fcon
   serve-stack -I/tmp/selfgz2940/NVIDIA-Linux-x86_64-256.44/kernel -Wall -MD -W
   sign-compare -Wno-cast-qual -Wno-error -D__KERNEL__ -DMODULE -DNVRM -DNV_VER
   SION_STRING=\"256.44\" -mcmodel=kernel -mno-red-zone -UDEBUG -U_DEBUG -DNDEB
   UG  -DMODULE -D"KBUILD_STR(s)=#s" -D"KBUILD_BASENAME=KBUILD_STR(nv_i2c)"  -D
   "KBUILD_MODNAME=KBUILD_STR(nvidia)"  -c -o /tmp/selfgz2940/NVIDIA-Linux-x86_
   64-256.44/kernel/.tmp_nv-i2c.o /tmp/
   selfgz2940/NVIDIA-Linux-x86_64-256.44/kernel/nv-i2c.c
     set -e ; perl /usr/src/linux-headers-2.6.32-24-generic/scripts/recordmcoun
   t.pl "x86_64" "64" "objdump" "objcopy" "cc" "ld" "nm" "" "" "1" "/tmp/selfgz
   2940/NVIDIA-Linux-x86_64-256.44/kernel/nv-i2c.o";
     cc -Wp,-MD,/tmp/selfgz2940/NVIDIA-Linux-x86_64-256.44/kernel/.nvacpi.o.d  
   -nostdinc -isystem /usr/lib/gcc/x86_64-linux-gnu/4.4.3/include  -Iinclude  -
   I/usr/src/linux-headers-2.6.32-24-generic/arch/x86/include -include include/
   linux/autoconf.h -Iubuntu/include  -D__KERNEL__ -Wall -Wundef -Wstrict-proto
   types -Wno-trigraphs -fno-strict-aliasing -fno-common -Werror-implicit-funct
   ion-declaration -Wno-format-security -fno-delete-null-pointer-checks -O2 -m6
   4 -mtune=generic -mno-red-zone -mcmodel=kernel -funit-at-a-time -maccumulate
   -outgoing-args -fstack-protector -DCONFIG_AS_CFI=1 -DCONFIG_AS_CFI_SIGNAL_FR
   AME=1 -pipe -Wno-sign-compare -fno-asynchronous-unwind-tables -mno-sse -mno-
   mmx -mno-sse2 -mno-3dnow -Wframe-larger-than=1024 -fno-omit-frame-pointer -f
   no-optim
   ize-sibling-calls -pg -Wdeclaration-after-statement -Wno-pointer-sign -fno-s
   trict-overflow -fno-dwarf2-cfi-asm -fconserve-stack -I/tmp/selfgz2940/NVIDIA
   -Linux-x86_64-256.44/kernel -Wall -MD -Wsign-compare -Wno-cast-qual -Wno-err
   or -D__KERNEL__ -DMODULE -DNVRM -DNV_VERSION_STRING=\"256.44\" -mcmodel=kern
   el -mno-red-zone -UDEBUG -U_DEBUG -DNDEBUG  -DMODULE -D"KBUILD_STR(s)=#s" -D
   "KBUILD_BASENAME=KBUILD_STR(nvacpi)"  -D"KBUILD_MODNAME=KBUILD_STR(nvidia)" 
   -c -o /tmp/selfgz2940/NVIDIA-Linux-x86_64-256.44/kernel/.tmp_nvacpi.o /tmp/s
   elfgz2940/NVIDIA-Linux-x86_64-256.44/kernel/nvacpi.c
     set -e ; perl /usr/src/linux-headers-2.6.32-24-generic/scripts/recordmcoun
   t.pl "x86_64" "64" "objdump" "objcopy" "cc" "ld" "nm" "" "" "1" "/tmp/selfgz
   2940/NVIDIA-Linux-x86_64-256.44/kernel/nvacpi.o";
     ld -m elf_x86_64   -r -o /tmp/selfgz2940/NVIDIA-Linux-x86_64-256.44/kernel
   /nvidia.o /tmp/selfgz2940/NVIDIA-Linux-x86_64-256.44/kernel/nv-kernel.o /tmp
   /selfgz2940/NVIDIA-Linux-x86_64-256.44/kernel/nv.o /tmp/selfgz2940/NVIDIA-Li
   nux-x86_64-256.44/kernel/nv_gvi.o /tmp/selfgz2940/NVIDIA-Linux-x86_64-256.44
   /kernel/nv-vm.o /tmp/selfgz2940/NVIDIA-Linux-x86_64-256.44/kernel/os-agp.o /
   tmp/selfgz2940/NVIDIA-Linux-x86_64-256.44/kernel/os-interface.o /tmp/selfgz2
   940/NVIDIA-Linux-x86_64-256.44/kernel/os-registry.o /tmp/selfgz2940/NVIDIA-L
   inux-x86_64-256.44/kernel/nv-i2c.o /tmp/selfgz2940/NVIDIA-Linux-x86_64-256.4
   4/kernel/nvacpi.o 
   (cat /dev/null;   echo kernel//tmp/selfgz2940/NVIDIA-Linux-x86_64-256.44/ker
   nel/nvidia.ko;) > /tmp/selfgz2940/NVIDIA-Linux-x86_64-256.44/kernel/modules.
   order
   make -f /usr/src/linux-headers-2.6.32-24-generic/scripts/Makefile.modpost
     scripts/mod/modpost -m -a -i /usr/src/linux-headers-2.6.32-24-generic/Modu
   le.symvers -I /tmp/selfgz2940/NVIDIA-Linux-x86_64-256.44/kernel/Module.symve
   rs  -o /tmp/selfgz2940/NVIDIA-Linux-x86_64-256.44/kernel/Module.symvers -S -
   w  -s
   WARNING: could not find /tmp/selfgz2940/NVIDIA-Linux-x86_64-256.44/kernel/.n
   v-kernel.o.cmd for /tmp/selfgz2940/NVIDIA-Linux-x86_64-256.44/kernel/nv-kern
   el.o
     cc -Wp,-MD,/tmp/selfgz2940/NVIDIA-Linux-x86_64-256.44/kernel/.nvidia.mod.o
   .d  -nostdinc -isystem /usr/lib/gcc/x86_64-linux-gnu/4.4.3/include  -Iinclud
   e  -I/usr/src/linux-headers-2.6.32-24-generic/arch/x86/include -include incl
   ude/linux/autoconf.h -Iubuntu/include  -D__KERNEL__ -Wall -Wundef -Wstrict-p
   rototypes -Wno-trigraphs -fno-strict-aliasing -fno-common -Werror-implicit-f
   unction-declaration -Wno-format-security -fno-delete-null-pointer-checks -O2
   -m64 -mtune=generic -mno-red-zone -mcmodel=kernel -funit-at-a-time -maccumul
   ate-outgoing-args -fstack-protector -DCONFIG_AS_CFI=1 -DCONFIG_AS_CFI_SIGNAL
   _FRAME=1 -pipe -Wno-sign-compare -fno-asynchronous-unwind-tables -mno-sse -m
   no-mmx -mno-sse2 -mno-3dnow -Wframe-larger-than=1024 -fno-omit-frame-pointer
   -fno-optimize-sibling-calls -pg -Wdeclaration-after-statement -Wno-pointer-s
   ign -fno-strict-overflow -fno-dwarf2-cfi-asm -fconserve-stack -I/tmp/selfgz2
   940/NVIDIA-Linux-x86_64-256.44/kernel -Wall -MD -Wsign-compare -Wno-cast-qua
   l -Wno-error -D__KERNEL__ -DMODULE -DNVRM -D
   NV_VERSION_STRING=\"256.44\" -mcmodel=kernel -mno-red-zone -UDEBUG -U_DEBUG 
   -DNDEBUG  -D"KBUILD_STR(s)=#s" -D"KBUILD_BASENAME=KBUILD_STR(nvidia.mod)"  -
   D"KBUILD_MODNAME=KBUILD_STR(nvidia)"  -DMODULE -c -o /tmp/selfgz2940/NVIDIA-
   Linux-x86_64-256.44/kernel/nvidia.mod.o /tmp/selfgz2940/NVIDIA-Linux-x86_64-
   256.44/kernel/nvidia.mod.c
     ld -r -m elf_x86_64 -T /usr/src/linux-headers-2.6.32-24-generic/scripts/mo
   dule-common.lds --build-id -o /tmp/selfgz2940/NVIDIA-Linux-x86_64-256.44/ker
   nel/nvidia.ko /tmp/selfgz2940/NVIDIA-Linux-x86_64-256.44/kernel/nvidia.o /tm
   p/selfgz2940/NVIDIA-Linux-x86_64-256.44/kernel/nvidia.mod.o
   NVIDIA: left KBUILD.
-> done.
-> Kernel module compilation complete.
-> Kernel messages:
   [   35.300585] cfg80211: Leaving channel 5520 MHz intact on phy0 - no rule
   found in band on Country IE
   [   35.300587] cfg80211: Leaving channel 5540 MHz intact on phy0 - no rule
   found in band on Country IE
   [   35.300589] cfg80211: Leaving channel 5560 MHz intact on phy0 - no rule
   found in band on Country IE
   [   35.300591] cfg80211: Leaving channel 5580 MHz intact on phy0 - no rule
   found in band on Country IE
   [   35.300593] cfg80211: Leaving channel 5600 MHz intact on phy0 - no rule
   found in band on Country IE
   [   35.300595] cfg80211: Leaving channel 5620 MHz intact on phy0 - no rule
   found in band on Country IE
   [   35.300597] cfg80211: Leaving channel 5640 MHz intact on phy0 - no rule
   found in band on Country IE
   [   35.300599] cfg80211: Leaving channel 5660 MHz intact on phy0 - no rule
   found in band on Country IE
   [   35.300601] cfg80211: Leaving channel 5680 MHz intact on phy0 - no rule
   found in band on Country IE
   [   35.300603] cfg80211: Leaving channel 5700 MHz intact on phy0 - no rule
   found in band on Country IE
   [   35.300605] cfg80211: Leaving channel 5745 MHz intact on phy0 - no rule
   found in band on Country IE
   [   35.300607] cfg80211: Leaving channel 5765 MHz intact on phy0 - no rule
   found in band on Country IE
   [   35.300609] cfg80211: Leaving channel 5785 MHz intact on phy0 - no rule
   found in band on Country IE
   [   35.300611] cfg80211: Leaving channel 5805 MHz intact on phy0 - no rule
   found in band on Country IE
   [   35.300613] cfg80211: Leaving channel 5825 MHz intact on phy0 - no rule
   found in band on Country IE
   [   35.300615] cfg80211: Current regulatory domain updated by AP to: GB
   [   35.300617] 	(start_freq - end_freq @ bandwidth), (max_antenna_gain,
   max_eirp)
   [   35.300619] 	(2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A, 2000 mBm)
   [   35.312459] Intel AES-NI instructions are not detected.
   [   35.332277] padlock: VIA PadLock not detected.
   [   45.850031] wlan0: no IPv6 routers present
   [  582.991361] wlan0: deauthenticating from 00:23:54:dc:78:ce by local
   choice (reason=3)
   [  623.962895] nvidia 0000:01:00.0: setting latency timer to 64
   [  623.962914] vgaarb: device changed decodes:
   PCI:0000:01:00.0,olddecodes=none,decodes=none:owns=io+mem
   [  623.963442] NVRM: loading NVIDIA UNIX x86_64 Kernel Module  256.44  Thu
   Jul 29 01:22:44 PDT 2010
-> Installing both new and classic TLS OpenGL libraries.
-> Installing both new and classic TLS 32bit OpenGL libraries.
-> Install NVIDIA's 32-bit compatibility OpenGL libraries? (Answer: Yes)
-> Parsing log file:
-> done.
-> Validating previous installation:
ERROR: File '/usr/lib/xorg/modules/extensions/libglx.so' is not a symbolic
       link.
-> done.
WARNING: Your driver installation has been altered since it was initially
         installed; this may happen, for example, if you have since installed
         the NVIDIA driver through a mechanism other than nvidia-installer
         (such as your distribution's native package management system). 
         nvidia-installer will attempt to uninstall as best it can.  Please see
         the file '/var/log/nvidia-installer.log' for details.
-> Uninstalling NVIDIA Accelerated Graphics Driver for Linux-x86_64 (1.0-25644
   (256.44)):
-> done.
-> Uninstallation of existing driver: NVIDIA Accelerated Graphics Driver for
   Linux-x86_64 (256.44) is complete.
-> Searching for conflicting X files:
-> done.
-> Searching for conflicting OpenGL files:
-> done.
-> Installing 'NVIDIA Accelerated Graphics Driver for Linux-x86_64' (256.44):
   executing: '/sbin/ldconfig'...
   executing: '/sbin/depmod -aq'...
-> done.
-> Driver file installation is complete.
-> Running post-install sanity check:
-> done.
-> Post-install sanity check passed.
-> Shared memory test passed.
-> Running runtime sanity check:
-> done.
-> Runtime sanity check passed.
-> Would you like to run the nvidia-xconfig utility to automatically update you
   r X configuration file so that the NVIDIA X driver will be used when you res
   tart X?  Any pre-existing X configuration file will be backed up. (Answer: N
   o)
-> Installation of the NVIDIA Accelerated Graphics Driver for Linux-x86_64
   (version: 256.44) is now complete.  Please update your XF86Config or
   xorg.conf file as appropriate; see the file
   /usr/share/doc/NVIDIA_GLX-1.0/README.txt for details.

____________________________________________

/var/log/Xorg.0.log

X.Org X Server 1.7.6
Release Date: 2010-03-17
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-27-server x86_64 Ubuntu
Current Operating System: Linux notebook 2.6.32-24-generic #39-Ubuntu SMP Wed Jul 28 05:14:15 UTC 2010 x86_64
Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.32-24-generic root=UUID=2846023d-9f02-4faa-a800-861f102d748e ro splash quiet splash nomodeset video=uvesafb:mode_option=1280x800-24,mtrr=3,scroll=ywrap
Build Date: 21 July 2010  01:03:39PM
xorg-server 2:1.7.6-2ubuntu7.3 (For technical support please see http://www.ubuntu.com/support) 
Current version of pixman: 0.16.4
	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Thu Aug 19 15:23:18 2010
(==) Using config file: "/etc/X11/xorg.conf"
(==) Using config directory: "/usr/lib/X11/xorg.conf.d"
(==) ServerLayout "Layout0"
(**) |-->Screen "Screen0" (0)
(**) |   |-->Monitor "Monitor0"
(**) |   |-->Device "Device0"
(**) |-->Input Device "Keyboard0"
(**) |-->Input Device "Mouse0"
(**) Option "Xinerama" "0"
(==) Automatically adding devices
(==) Automatically enabling devices
(WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
	Entry deleted from font path.
(==) FontPath set to:
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/100dpi/:unscaled,
	/usr/share/fonts/X11/75dpi/:unscaled,
	/usr/share/fonts/X11/Type1,
	/usr/share/fonts/X11/100dpi,
	/usr/share/fonts/X11/75dpi,
	/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
	built-ins
(==) ModulePath set to "/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
(WW) AllowEmptyInput is on, devices using drivers 'kbd', 'mouse' or 'vmmouse' will be disabled.
(WW) Disabling Keyboard0
(WW) Disabling Mouse0
(II) Loader magic: 0x7ca300
(II) Module ABI versions:
	X.Org ANSI C Emulation: 0.4
	X.Org Video Driver: 6.0
	X.Org XInput driver : 7.0
	X.Org Server Extension : 2.0
(++) using VT number 7

(--) PCI:*(0:1:0:0) 10de:0649:103c:3603 nVidia Corporation G96 [GeForce 9600M GT] rev 161, Mem @ 0xd2000000/16777216, 0xc0000000/268435456, 0xd0000000/33554432, I/O @ 0x00009000/128
(II) Open ACPI successful (/var/run/acpid.socket)
(II) LoadModule: "extmod"
(II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
(II) Module extmod: vendor="X.Org Foundation"
	compiled for 1.7.6, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 2.0
(II) Loading extension MIT-SCREEN-SAVER
(II) Loading extension XFree86-VidModeExtension
(II) Loading extension XFree86-DGA
(II) Loading extension DPMS
(II) Loading extension XVideo
(II) Loading extension XVideo-MotionCompensation
(II) Loading extension X-Resource
(II) LoadModule: "dbe"
(II) Loading /usr/lib/xorg/modules/extensions/libdbe.so
(II) Module dbe: vendor="X.Org Foundation"
	compiled for 1.7.6, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 2.0
(II) Loading extension DOUBLE-BUFFER
(II) LoadModule: "glx"
(II) Loading /usr/lib/xorg/modules/extensions/libglx.so
(II) Module glx: vendor="NVIDIA Corporation"
	compiled for 4.0.2, module version = 1.0.0
	Module class: X.Org Server Extension
(II) NVIDIA GLX Module  256.44  Thu Jul 29 01:47:53 PDT 2010
(II) Loading extension GLX
(II) LoadModule: "record"
(II) Loading /usr/lib/xorg/modules/extensions/librecord.so
(II) Module record: vendor="X.Org Foundation"
	compiled for 1.7.6, module version = 1.13.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 2.0
(II) Loading extension RECORD
(II) LoadModule: "dri"
(II) Loading /usr/lib/xorg/modules/extensions/libdri.so
(II) Module dri: vendor="X.Org Foundation"
	compiled for 1.7.6, module version = 1.0.0
	ABI class: X.Org Server Extension, version 2.0
(II) Loading extension XFree86-DRI
(II) LoadModule: "dri2"
(II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
(II) Module dri2: vendor="X.Org Foundation"
	compiled for 1.7.6, module version = 1.1.0
	ABI class: X.Org Server Extension, version 2.0
(II) Loading extension DRI2
(II) LoadModule: "nvidia"
(II) Loading /usr/lib/xorg/modules/drivers/nvidia_drv.so
(II) Module nvidia: vendor="NVIDIA Corporation"
	compiled for 4.0.2, module version = 1.0.0
	Module class: X.Org Video Driver
(II) NVIDIA dlloader X Driver  256.44  Thu Jul 29 01:24:51 PDT 2010
(II) NVIDIA Unified Driver for all Supported NVIDIA GPUs
(II) Primary Device is: PCI 01@00:00:0
(II) Loading sub module "fb"
(II) LoadModule: "fb"
(II) Loading /usr/lib/xorg/modules/libfb.so
(II) Module fb: vendor="X.Org Foundation"
	compiled for 1.7.6, module version = 1.0.0
	ABI class: X.Org ANSI C Emulation, version 0.4
(II) Loading sub module "wfb"
(II) LoadModule: "wfb"
(II) Loading /usr/lib/xorg/modules/libwfb.so
(II) Module wfb: vendor="X.Org Foundation"
	compiled for 1.7.6, module version = 1.0.0
	ABI class: X.Org ANSI C Emulation, version 0.4
(II) Loading sub module "ramdac"
(II) LoadModule: "ramdac"
(II) Module "ramdac" already built-in
(**) NVIDIA(0): Depth 24, (--) framebuffer bpp 32
(==) NVIDIA(0): RGB weight 888
(==) NVIDIA(0): Default visual is TrueColor
(==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
(**) NVIDIA(0): Option "NoLogo" "1"
(**) NVIDIA(0): Option "TwinView" "1"
(**) NVIDIA(0): Option "MetaModes" "CRT: 1366x768_60 +1280+0, DFP: 1280x800_60 +0+0"
(**) NVIDIA(0): Option "TwinViewXineramaInfoOrder" "DFP-0"
(**) Aug 19 15:23:18 NVIDIA(0): Enabling RENDER acceleration
(II) Aug 19 15:23:18 NVIDIA(0): Support for GLX with the Damage and Composite X extensions is
(II) Aug 19 15:23:18 NVIDIA(0):     enabled.
(II) Aug 19 15:23:21 NVIDIA(0): NVIDIA GPU GeForce 9600M GT (G96) at PCI:1:0:0 (GPU-0)
(--) Aug 19 15:23:21 NVIDIA(0): Memory: 524288 kBytes
(--) Aug 19 15:23:21 NVIDIA(0): VideoBIOS: 62.94.1a.00.19
(II) Aug 19 15:23:21 NVIDIA(0): Detected PCI Express Link width: 16X
(--) Aug 19 15:23:21 NVIDIA(0): Interlaced video modes are supported on this GPU
(--) Aug 19 15:23:21 NVIDIA(0): Connected display device(s) on GeForce 9600M GT at PCI:1:0:0:
(--) Aug 19 15:23:21 NVIDIA(0):     EMA E192HQ (CRT-0)
(--) Aug 19 15:23:21 NVIDIA(0):     LPL (DFP-0)
(--) Aug 19 15:23:21 NVIDIA(0): EMA E192HQ (CRT-0): 400.0 MHz maximum pixel clock
(--) Aug 19 15:23:21 NVIDIA(0): LPL (DFP-0): 330.0 MHz maximum pixel clock
(--) Aug 19 15:23:21 NVIDIA(0): LPL (DFP-0): Internal Dual Link LVDS
(**) Aug 19 15:23:21 NVIDIA(0): TwinView enabled
(II) Aug 19 15:23:21 NVIDIA(0): Display Devices found referenced in MetaMode: CRT-0, DFP-0
(II) Aug 19 15:23:21 NVIDIA(0): Assigned Display Devices: CRT-0, DFP-0
(II) Aug 19 15:23:21 NVIDIA(0): Validated modes:
(II) Aug 19 15:23:21 NVIDIA(0):     "CRT:1366x768_60+1280+0,DFP:1280x800_60+0+0"
(II) Aug 19 15:23:21 NVIDIA(0): Virtual screen size determined to be 2646 x 800
(--) Aug 19 15:23:22 NVIDIA(0): DPI set to (84, 84); computed from "UseEdidDpi" X config
(--) Aug 19 15:23:22 NVIDIA(0):     option
(==) Aug 19 15:23:22 NVIDIA(0): Enabling 32-bit ARGB GLX visuals.
(--) Depth 24 pixmap format is 32 bpp
(II) Aug 19 15:23:22 NVIDIA: Using 768.00 MB of virtual memory for indirect memory access.
(II) Aug 19 15:23:22 NVIDIA(0): Initialized GPU GART.
(II) Aug 19 15:23:22 NVIDIA(0): ACPI display change hotkey events enabled: the X server is new
(II) Aug 19 15:23:22 NVIDIA(0):     enough to receive ACPI hotkey events.
(II) Aug 19 15:23:22 NVIDIA(0): ACPI brightness change hotkey events enabled.
(II) Aug 19 15:23:22 NVIDIA(0): Setting mode "CRT:1366x768_60+1280+0,DFP:1280x800_60+0+0"
(II) Loading extension NV-GLX
(II) Aug 19 15:23:22 NVIDIA(0): Initialized OpenGL Acceleration
(==) NVIDIA(0): Disabling shared memory pixmaps
(II) Aug 19 15:23:22 NVIDIA(0): Initialized X Rendering Acceleration
(==) NVIDIA(0): Backing store disabled
(==) NVIDIA(0): Silken mouse enabled
(**) NVIDIA(0): DPMS enabled
(II) Loading extension NV-CONTROL
(II) Loading extension XINERAMA
(==) RandR enabled
(II) Initializing built-in extension Generic Event Extension
(II) Initializing built-in extension SHAPE
(II) Initializing built-in extension MIT-SHM
(II) Initializing built-in extension XInputExtension
(II) Initializing built-in extension XTEST
(II) Initializing built-in extension BIG-REQUESTS
(II) Initializing built-in extension SYNC
(II) Initializing built-in extension XKEYBOARD
(II) Initializing built-in extension XC-MISC
(II) Initializing built-in extension SECURITY
(II) Initializing built-in extension XINERAMA
(II) Initializing built-in extension XFIXES
(II) Initializing built-in extension RENDER
(II) Initializing built-in extension RANDR
(II) Initializing built-in extension COMPOSITE
(II) Initializing built-in extension DAMAGE
(II) Initializing extension GLX
(II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
(II) config/udev: Adding input device Power Button (/dev/input/event3)
(**) Power Button: Applying InputClass "evdev keyboard catchall"
(II) LoadModule: "evdev"
(II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
(II) Module evdev: vendor="X.Org Foundation"
	compiled for 1.7.6, module version = 2.3.2
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 7.0
(**) Power Button: always reports core events
(**) Power Button: Device: "/dev/input/event3"
(II) Power Button: Found keys
(II) Power Button: Configuring as keyboard
(II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "evdev"
(**) Option "xkb_layout" "us,ru"
(**) Option "xkb_variant" ","
(**) Option "xkb_options" "grp:alt_shift_toggle,grp_led:scroll"
(II) XKB: reuse xkmfile /var/lib/xkb/server-DDD1A189F83D1712CA89CD4B0F2606515EB03703.xkm
(II) config/udev: Adding input device Video Bus (/dev/input/event6)
(**) Video Bus: Applying InputClass "evdev keyboard catchall"
(**) Video Bus: always reports core events
(**) Video Bus: Device: "/dev/input/event6"
(II) Video Bus: Found keys
(II) Video Bus: Configuring as keyboard
(II) XINPUT: Adding extended input device "Video Bus" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "evdev"
(**) Option "xkb_layout" "us,ru"
(**) Option "xkb_variant" ","
(**) Option "xkb_options" "grp:alt_shift_toggle,grp_led:scroll"
(II) config/udev: Adding input device Power Button (/dev/input/event0)
(**) Power Button: Applying InputClass "evdev keyboard catchall"
(**) Power Button: always reports core events
(**) Power Button: Device: "/dev/input/event0"
(II) Power Button: Found keys
(II) Power Button: Configuring as keyboard
(II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "evdev"
(**) Option "xkb_layout" "us,ru"
(**) Option "xkb_variant" ","
(**) Option "xkb_options" "grp:alt_shift_toggle,grp_led:scroll"
(II) config/udev: Adding input device Lid Switch (/dev/input/event1)
(II) No input driver/identifier specified (ignoring)
(II) config/udev: Adding input device Sleep Button (/dev/input/event2)
(**) Sleep Button: Applying InputClass "evdev keyboard catchall"
(**) Sleep Button: always reports core events
(**) Sleep Button: Device: "/dev/input/event2"
(II) Sleep Button: Found keys
(II) Sleep Button: Configuring as keyboard
(II) XINPUT: Adding extended input device "Sleep Button" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "evdev"
(**) Option "xkb_layout" "us,ru"
(**) Option "xkb_variant" ","
(**) Option "xkb_options" "grp:alt_shift_toggle,grp_led:scroll"
(II) config/udev: Adding input device Logitech USB Receiver (/dev/input/event7)
(**) Logitech USB Receiver: Applying InputClass "evdev pointer catchall"
(**) Logitech USB Receiver: always reports core events
(**) Logitech USB Receiver: Device: "/dev/input/event7"
(II) Logitech USB Receiver: Found 20 mouse buttons
(II) Logitech USB Receiver: Found scroll wheel(s)
(II) Logitech USB Receiver: Found relative axes
(II) Logitech USB Receiver: Found x and y relative axes
(II) Logitech USB Receiver: Configuring as mouse
(**) Logitech USB Receiver: YAxisMapping: buttons 4 and 5
(**) Logitech USB Receiver: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) XINPUT: Adding extended input device "Logitech USB Receiver" (type: MOUSE)
(II) Logitech USB Receiver: initialized for relative axes.
(II) config/udev: Adding input device Logitech USB Receiver (/dev/input/mouse1)
(II) No input driver/identifier specified (ignoring)
(II) config/udev: Adding input device Logitech USB Receiver (/dev/input/event8)
(**) Logitech USB Receiver: Applying InputClass "evdev keyboard catchall"
(**) Logitech USB Receiver: always reports core events
(**) Logitech USB Receiver: Device: "/dev/input/event8"
(II) Logitech USB Receiver: Found 1 mouse buttons
(II) Logitech USB Receiver: Found scroll wheel(s)
(II) Logitech USB Receiver: Found relative axes
(II) Logitech USB Receiver: Found absolute axes
(II) Logitech USB Receiver: Found keys
(II) Logitech USB Receiver: Configuring as mouse
(II) Logitech USB Receiver: Configuring as keyboard
(**) Logitech USB Receiver: YAxisMapping: buttons 4 and 5
(**) Logitech USB Receiver: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) XINPUT: Adding extended input device "Logitech USB Receiver" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "evdev"
(**) Option "xkb_layout" "us,ru"
(**) Option "xkb_variant" ","
(**) Option "xkb_options" "grp:alt_shift_toggle,grp_led:scroll"
(EE) Logitech USB Receiver: failed to initialize for relative axes.
(II) Logitech USB Receiver: initialized for absolute axes.
(II) config/udev: Adding input device HDA Digital PCBeep (/dev/input/event11)
(II) No input driver/identifier specified (ignoring)
(II) config/udev: Adding input device HDA Intel Mic at Ext Front Jack (/dev/input/event12)
(II) No input driver/identifier specified (ignoring)
(II) config/udev: Adding input device HDA Intel Mic at Sep UNKNOWN Jack (/dev/input/event13)
(II) No input driver/identifier specified (ignoring)
(II) config/udev: Adding input device HDA Intel HP Out at Ext Front Jack (/dev/input/event14)
(II) No input driver/identifier specified (ignoring)
(II) config/udev: Adding input device HP Webcam (/dev/input/event10)
(**) HP Webcam: Applying InputClass "evdev keyboard catchall"
(**) HP Webcam: always reports core events
(**) HP Webcam: Device: "/dev/input/event10"
(II) HP Webcam: Found keys
(II) HP Webcam: Configuring as keyboard
(II) XINPUT: Adding extended input device "HP Webcam" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "evdev"
(**) Option "xkb_layout" "us,ru"
(**) Option "xkb_variant" ","
(**) Option "xkb_options" "grp:alt_shift_toggle,grp_led:scroll"
(II) config/udev: Adding input device AT Translated Set 2 keyboard (/dev/input/event5)
(**) AT Translated Set 2 keyboard: Applying InputClass "evdev keyboard catchall"
(**) AT Translated Set 2 keyboard: always reports core events
(**) AT Translated Set 2 keyboard: Device: "/dev/input/event5"
(II) AT Translated Set 2 keyboard: Found keys
(II) AT Translated Set 2 keyboard: Configuring as keyboard
(II) XINPUT: Adding extended input device "AT Translated Set 2 keyboard" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "evdev"
(**) Option "xkb_layout" "us,ru"
(**) Option "xkb_variant" ","
(**) Option "xkb_options" "grp:alt_shift_toggle,grp_led:scroll"
(II) config/udev: Adding input device ST LIS3LV02DL Accelerometer (/dev/input/event9)
(II) No input driver/identifier specified (ignoring)
(II) config/udev: Adding input device ST LIS3LV02DL Accelerometer (/dev/input/js0)
(II) No input driver/identifier specified (ignoring)
(II) config/udev: Adding input device Macintosh mouse button emulation (/dev/input/event4)
(**) Macintosh mouse button emulation: Applying InputClass "evdev pointer catchall"
(**) Macintosh mouse button emulation: always reports core events
(**) Macintosh mouse button emulation: Device: "/dev/input/event4"
(II) Macintosh mouse button emulation: Found 3 mouse buttons
(II) Macintosh mouse button emulation: Found relative axes
(II) Macintosh mouse button emulation: Found x and y relative axes
(II) Macintosh mouse button emulation: Configuring as mouse
(**) Macintosh mouse button emulation: YAxisMapping: buttons 4 and 5
(**) Macintosh mouse button emulation: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) XINPUT: Adding extended input device "Macintosh mouse button emulation" (type: MOUSE)
(II) Macintosh mouse button emulation: initialized for relative axes.
(II) config/udev: Adding input device Macintosh mouse button emulation (/dev/input/mouse0)
(II) No input driver/identifier specified (ignoring)

____________________________________________

/etc/X11/xorg.conf
# nvidia-settings: X configuration file generated by nvidia-settings
# nvidia-settings:  version 256.44  (buildmeister@builder103.nvidia.com)  Thu Jul 29 01:52:36 PDT 2010


Section "ServerLayout"
    Identifier     "Layout0"
    Screen      0  "Screen0" 0 0
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
    Option         "Xinerama" "0"
EndSection

Section "Files"
EndSection

Section "InputDevice"

    # generated from default
    Identifier     "Mouse0"
    Driver         "mouse"
    Option         "Protocol" "auto"
    Option         "Device" "/dev/psaux"
    Option         "Emulate3Buttons" "no"
    Option         "ZAxisMapping" "4 5"
EndSection

Section "InputDevice"

    # generated from default
    Identifier     "Keyboard0"
    Driver         "kbd"
EndSection

Section "Monitor"

    # HorizSync source: edid, VertRefresh source: edid
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "EMA E192HQ"
    HorizSync       31.0 - 83.0
    VertRefresh     56.0 - 76.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 9600M GT"
    Option         "NoLogo" "1"
EndSection

Section "Screen"
# Removed Option "metamodes" "DFP: nvidia-auto-select +0+0, CRT: nvidia-auto-select +1280+0"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "TwinView" "1"
    Option         "TwinViewXineramaInfoOrder" "DFP-0"
    Option         "metamodes" "CRT: 1366x768_60 +1280+0, DFP: 1280x800_60 +0+0"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection


____________________________________________

/var/log/Xorg.0.log.old

X.Org X Server 1.7.6
Release Date: 2010-03-17
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-27-server x86_64 Ubuntu
Current Operating System: Linux notebook 2.6.32-24-generic #39-Ubuntu SMP Wed Jul 28 05:14:15 UTC 2010 x86_64
Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.32-24-generic root=UUID=2846023d-9f02-4faa-a800-861f102d748e ro splash quiet splash nomodeset video=uvesafb:mode_option=1280x800-24,mtrr=3,scroll=ywrap
Build Date: 21 July 2010  01:03:39PM
xorg-server 2:1.7.6-2ubuntu7.3 (For technical support please see http://www.ubuntu.com/support) 
Current version of pixman: 0.16.4
	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Wed Aug 18 21:54:38 2010
(==) Using config file: "/etc/X11/xorg.conf"
(==) Using config directory: "/usr/lib/X11/xorg.conf.d"
(==) ServerLayout "Layout0"
(**) |-->Screen "Screen0" (0)
(**) |   |-->Monitor "Monitor0"
(**) |   |-->Device "Device0"
(**) |-->Input Device "Keyboard0"
(**) |-->Input Device "Mouse0"
(**) Option "Xinerama" "0"
(==) Automatically adding devices
(==) Automatically enabling devices
(WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
	Entry deleted from font path.
(==) FontPath set to:
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/100dpi/:unscaled,
	/usr/share/fonts/X11/75dpi/:unscaled,
	/usr/share/fonts/X11/Type1,
	/usr/share/fonts/X11/100dpi,
	/usr/share/fonts/X11/75dpi,
	/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
	built-ins
(==) ModulePath set to "/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
(WW) AllowEmptyInput is on, devices using drivers 'kbd', 'mouse' or 'vmmouse' will be disabled.
(WW) Disabling Keyboard0
(WW) Disabling Mouse0
(II) Loader magic: 0x7ca300
(II) Module ABI versions:
	X.Org ANSI C Emulation: 0.4
	X.Org Video Driver: 6.0
	X.Org XInput driver : 7.0
	X.Org Server Extension : 2.0
(++) using VT number 7

(--) PCI:*(0:1:0:0) 10de:0649:103c:3603 nVidia Corporation G96 [GeForce 9600M GT] rev 161, Mem @ 0xd2000000/16777216, 0xc0000000/268435456, 0xd0000000/33554432, I/O @ 0x00009000/128
(WW) Open ACPI failed (/var/run/acpid.socket) (No such file or directory)
(II) LoadModule: "extmod"
(II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
(II) Module extmod: vendor="X.Org Foundation"
	compiled for 1.7.6, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 2.0
(II) Loading extension MIT-SCREEN-SAVER
(II) Loading extension XFree86-VidModeExtension
(II) Loading extension XFree86-DGA
(II) Loading extension DPMS
(II) Loading extension XVideo
(II) Loading extension XVideo-MotionCompensation
(II) Loading extension X-Resource
(II) LoadModule: "dbe"
(II) Loading /usr/lib/xorg/modules/extensions/libdbe.so
(II) Module dbe: vendor="X.Org Foundation"
	compiled for 1.7.6, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 2.0
(II) Loading extension DOUBLE-BUFFER
(II) LoadModule: "glx"
(II) Loading /usr/lib/xorg/modules/extensions/libglx.so
(II) Module glx: vendor="NVIDIA Corporation"
	compiled for 4.0.2, module version = 1.0.0
	Module class: X.Org Server Extension
(II) NVIDIA GLX Module  256.44  Thu Jul 29 01:47:53 PDT 2010
(II) Loading extension GLX
(II) LoadModule: "record"
(II) Loading /usr/lib/xorg/modules/extensions/librecord.so
(II) Module record: vendor="X.Org Foundation"
	compiled for 1.7.6, module version = 1.13.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 2.0
(II) Loading extension RECORD
(II) LoadModule: "dri"
(II) Loading /usr/lib/xorg/modules/extensions/libdri.so
(II) Module dri: vendor="X.Org Foundation"
	compiled for 1.7.6, module version = 1.0.0
	ABI class: X.Org Server Extension, version 2.0
(II) Loading extension XFree86-DRI
(II) LoadModule: "dri2"
(II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
(II) Module dri2: vendor="X.Org Foundation"
	compiled for 1.7.6, module version = 1.1.0
	ABI class: X.Org Server Extension, version 2.0
(II) Loading extension DRI2
(II) LoadModule: "nvidia"
(II) Loading /usr/lib/xorg/modules/drivers/nvidia_drv.so
(II) Module nvidia: vendor="NVIDIA Corporation"
	compiled for 4.0.2, module version = 1.0.0
	Module class: X.Org Video Driver
(II) NVIDIA dlloader X Driver  256.44  Thu Jul 29 01:24:51 PDT 2010
(II) NVIDIA Unified Driver for all Supported NVIDIA GPUs
(II) Primary Device is: PCI 01@00:00:0
(II) Loading sub module "fb"
(II) LoadModule: "fb"
(II) Loading /usr/lib/xorg/modules/libfb.so
(II) Module fb: vendor="X.Org Foundation"
	compiled for 1.7.6, module version = 1.0.0
	ABI class: X.Org ANSI C Emulation, version 0.4
(II) Loading sub module "wfb"
(II) LoadModule: "wfb"
(II) Loading /usr/lib/xorg/modules/libwfb.so
(II) Module wfb: vendor="X.Org Foundation"
	compiled for 1.7.6, module version = 1.0.0
	ABI class: X.Org ANSI C Emulation, version 0.4
(II) Loading sub module "ramdac"
(II) LoadModule: "ramdac"
(II) Module "ramdac" already built-in
(**) NVIDIA(0): Depth 24, (--) framebuffer bpp 32
(==) NVIDIA(0): RGB weight 888
(==) NVIDIA(0): Default visual is TrueColor
(==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
(**) NVIDIA(0): Option "NoLogo" "1"
(**) NVIDIA(0): Option "TwinView" "1"
(**) NVIDIA(0): Option "MetaModes" "DFP: nvidia-auto-select +0+0, CRT: nvidia-auto-select +1280+0"
(**) NVIDIA(0): Option "TwinViewXineramaInfoOrder" "DFP-0"
(**) Aug 18 21:54:39 NVIDIA(0): Enabling RENDER acceleration
(II) Aug 18 21:54:39 NVIDIA(0): Support for GLX with the Damage and Composite X extensions is
(II) Aug 18 21:54:39 NVIDIA(0):     enabled.
(II) Aug 18 21:54:41 NVIDIA(0): NVIDIA GPU GeForce 9600M GT (G96) at PCI:1:0:0 (GPU-0)
(--) Aug 18 21:54:41 NVIDIA(0): Memory: 524288 kBytes
(--) Aug 18 21:54:41 NVIDIA(0): VideoBIOS: 62.94.1a.00.19
(II) Aug 18 21:54:41 NVIDIA(0): Detected PCI Express Link width: 16X
(--) Aug 18 21:54:41 NVIDIA(0): Interlaced video modes are supported on this GPU
(--) Aug 18 21:54:41 NVIDIA(0): Connected display device(s) on GeForce 9600M GT at PCI:1:0:0:
(--) Aug 18 21:54:41 NVIDIA(0):     EMA E192HQ (CRT-0)
(--) Aug 18 21:54:41 NVIDIA(0):     LPL (DFP-0)
(--) Aug 18 21:54:41 NVIDIA(0): EMA E192HQ (CRT-0): 400.0 MHz maximum pixel clock
(--) Aug 18 21:54:41 NVIDIA(0): LPL (DFP-0): 330.0 MHz maximum pixel clock
(--) Aug 18 21:54:41 NVIDIA(0): LPL (DFP-0): Internal Dual Link LVDS
(**) Aug 18 21:54:41 NVIDIA(0): TwinView enabled
(II) Aug 18 21:54:41 NVIDIA(0): Display Devices found referenced in MetaMode: CRT-0, DFP-0
(II) Aug 18 21:54:42 NVIDIA(0): Assigned Display Devices: CRT-0, DFP-0
(II) Aug 18 21:54:42 NVIDIA(0): Validated modes:
(II) Aug 18 21:54:42 NVIDIA(0):    
(II) Aug 18 21:54:42 NVIDIA(0):     "DFP:nvidia-auto-select+0+0,CRT:nvidia-auto-select+1280+0"
(II) Aug 18 21:54:42 NVIDIA(0): Virtual screen size determined to be 2646 x 800
(--) Aug 18 21:54:43 NVIDIA(0): DPI set to (84, 84); computed from "UseEdidDpi" X config
(--) Aug 18 21:54:43 NVIDIA(0):     option
(==) Aug 18 21:54:43 NVIDIA(0): Enabling 32-bit ARGB GLX visuals.
(--) Depth 24 pixmap format is 32 bpp
(II) Aug 18 21:54:43 NVIDIA: Using 768.00 MB of virtual memory for indirect memory access.
(II) Aug 18 21:54:43 NVIDIA(0): Initialized GPU GART.
(II) Aug 18 21:54:43 NVIDIA(0): ACPI display change hotkey events enabled: the X server is new
(II) Aug 18 21:54:43 NVIDIA(0):     enough to receive ACPI hotkey events.
(II) Aug 18 21:54:43 NVIDIA(0): ACPI brightness change hotkey events enabled.
(II) Aug 18 21:54:43 NVIDIA(0): Setting mode
(II) Aug 18 21:54:43 NVIDIA(0):     "DFP:nvidia-auto-select+0+0,CRT:nvidia-auto-select+1280+0"
(II) Loading extension NV-GLX
(II) Aug 18 21:54:43 NVIDIA(0): Initialized OpenGL Acceleration
(==) NVIDIA(0): Disabling shared memory pixmaps
(II) Aug 18 21:54:43 NVIDIA(0): Initialized X Rendering Acceleration
(==) NVIDIA(0): Backing store disabled
(==) NVIDIA(0): Silken mouse enabled
(**) NVIDIA(0): DPMS enabled
(II) Loading extension NV-CONTROL
(II) Loading extension XINERAMA
(==) RandR enabled
(II) Initializing built-in extension Generic Event Extension
(II) Initializing built-in extension SHAPE
(II) Initializing built-in extension MIT-SHM
(II) Initializing built-in extension XInputExtension
(II) Initializing built-in extension XTEST
(II) Initializing built-in extension BIG-REQUESTS
(II) Initializing built-in extension SYNC
(II) Initializing built-in extension XKEYBOARD
(II) Initializing built-in extension XC-MISC
(II) Initializing built-in extension SECURITY
(II) Initializing built-in extension XINERAMA
(II) Initializing built-in extension XFIXES
(II) Initializing built-in extension RENDER
(II) Initializing built-in extension RANDR
(II) Initializing built-in extension COMPOSITE
(II) Initializing built-in extension DAMAGE
(II) Initializing extension GLX
(II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
(II) config/udev: Adding input device Power Button (/dev/input/event3)
(**) Power Button: Applying InputClass "evdev keyboard catchall"
(II) LoadModule: "evdev"
(II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
(II) Module evdev: vendor="X.Org Foundation"
	compiled for 1.7.6, module version = 2.3.2
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 7.0
(**) Power Button: always reports core events
(**) Power Button: Device: "/dev/input/event3"
(II) Power Button: Found keys
(II) Power Button: Configuring as keyboard
(II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "evdev"
(**) Option "xkb_layout" "us,ru"
(**) Option "xkb_variant" ","
(**) Option "xkb_options" "grp:alt_shift_toggle,grp_led:scroll"
(II) XKB: reuse xkmfile /var/lib/xkb/server-DDD1A189F83D1712CA89CD4B0F2606515EB03703.xkm
(II) config/udev: Adding input device Video Bus (/dev/input/event6)
(**) Video Bus: Applying InputClass "evdev keyboard catchall"
(**) Video Bus: always reports core events
(**) Video Bus: Device: "/dev/input/event6"
(II) Video Bus: Found keys
(II) Video Bus: Configuring as keyboard
(II) XINPUT: Adding extended input device "Video Bus" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "evdev"
(**) Option "xkb_layout" "us,ru"
(**) Option "xkb_variant" ","
(**) Option "xkb_options" "grp:alt_shift_toggle,grp_led:scroll"
(II) config/udev: Adding input device Power Button (/dev/input/event0)
(**) Power Button: Applying InputClass "evdev keyboard catchall"
(**) Power Button: always reports core events
(**) Power Button: Device: "/dev/input/event0"
(II) Power Button: Found keys
(II) Power Button: Configuring as keyboard
(II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "evdev"
(**) Option "xkb_layout" "us,ru"
(**) Option "xkb_variant" ","
(**) Option "xkb_options" "grp:alt_shift_toggle,grp_led:scroll"
(II) config/udev: Adding input device Lid Switch (/dev/input/event1)
(II) No input driver/identifier specified (ignoring)
(II) config/udev: Adding input device Sleep Button (/dev/input/event2)
(**) Sleep Button: Applying InputClass "evdev keyboard catchall"
(**) Sleep Button: always reports core events
(**) Sleep Button: Device: "/dev/input/event2"
(II) Sleep Button: Found keys
(II) Sleep Button: Configuring as keyboard
(II) XINPUT: Adding extended input device "Sleep Button" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "evdev"
(**) Option "xkb_layout" "us,ru"
(**) Option "xkb_variant" ","
(**) Option "xkb_options" "grp:alt_shift_toggle,grp_led:scroll"
(II) config/udev: Adding input device Logitech USB Receiver (/dev/input/event7)
(**) Logitech USB Receiver: Applying InputClass "evdev pointer catchall"
(**) Logitech USB Receiver: always reports core events
(**) Logitech USB Receiver: Device: "/dev/input/event7"
(II) Logitech USB Receiver: Found 20 mouse buttons
(II) Logitech USB Receiver: Found scroll wheel(s)
(II) Logitech USB Receiver: Found relative axes
(II) Logitech USB Receiver: Found x and y relative axes
(II) Logitech USB Receiver: Configuring as mouse
(**) Logitech USB Receiver: YAxisMapping: buttons 4 and 5
(**) Logitech USB Receiver: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) XINPUT: Adding extended input device "Logitech USB Receiver" (type: MOUSE)
(II) Logitech USB Receiver: initialized for relative axes.
(II) config/udev: Adding input device Logitech USB Receiver (/dev/input/mouse1)
(II) No input driver/identifier specified (ignoring)
(II) config/udev: Adding input device Logitech USB Receiver (/dev/input/event8)
(**) Logitech USB Receiver: Applying InputClass "evdev keyboard catchall"
(**) Logitech USB Receiver: always reports core events
(**) Logitech USB Receiver: Device: "/dev/input/event8"
(II) Logitech USB Receiver: Found 1 mouse buttons
(II) Logitech USB Receiver: Found scroll wheel(s)
(II) Logitech USB Receiver: Found relative axes
(II) Logitech USB Receiver: Found absolute axes
(II) Logitech USB Receiver: Found keys
(II) Logitech USB Receiver: Configuring as mouse
(II) Logitech USB Receiver: Configuring as keyboard
(**) Logitech USB Receiver: YAxisMapping: buttons 4 and 5
(**) Logitech USB Receiver: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) XINPUT: Adding extended input device "Logitech USB Receiver" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "evdev"
(**) Option "xkb_layout" "us,ru"
(**) Option "xkb_variant" ","
(**) Option "xkb_options" "grp:alt_shift_toggle,grp_led:scroll"
(EE) Logitech USB Receiver: failed to initialize for relative axes.
(II) Logitech USB Receiver: initialized for absolute axes.
(II) config/udev: Adding input device HDA Digital PCBeep (/dev/input/event11)
(II) No input driver/identifier specified (ignoring)
(II) config/udev: Adding input device HDA Intel Mic at Ext Front Jack (/dev/input/event12)
(II) No input driver/identifier specified (ignoring)
(II) config/udev: Adding input device HDA Intel Mic at Sep UNKNOWN Jack (/dev/input/event13)
(II) No input driver/identifier specified (ignoring)
(II) config/udev: Adding input device HDA Intel HP Out at Ext Front Jack (/dev/input/event14)
(II) No input driver/identifier specified (ignoring)
(II) config/udev: Adding input device HP Webcam (/dev/input/event10)
(**) HP Webcam: Applying InputClass "evdev keyboard catchall"
(**) HP Webcam: always reports core events
(**) HP Webcam: Device: "/dev/input/event10"
(II) HP Webcam: Found keys
(II) HP Webcam: Configuring as keyboard
(II) XINPUT: Adding extended input device "HP Webcam" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "evdev"
(**) Option "xkb_layout" "us,ru"
(**) Option "xkb_variant" ","
(**) Option "xkb_options" "grp:alt_shift_toggle,grp_led:scroll"
(II) config/udev: Adding input device AT Translated Set 2 keyboard (/dev/input/event5)
(**) AT Translated Set 2 keyboard: Applying InputClass "evdev keyboard catchall"
(**) AT Translated Set 2 keyboard: always reports core events
(**) AT Translated Set 2 keyboard: Device: "/dev/input/event5"
(II) AT Translated Set 2 keyboard: Found keys
(II) AT Translated Set 2 keyboard: Configuring as keyboard
(II) XINPUT: Adding extended input device "AT Translated Set 2 keyboard" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "evdev"
(**) Option "xkb_layout" "us,ru"
(**) Option "xkb_variant" ","
(**) Option "xkb_options" "grp:alt_shift_toggle,grp_led:scroll"
(II) config/udev: Adding input device ST LIS3LV02DL Accelerometer (/dev/input/event9)
(II) No input driver/identifier specified (ignoring)
(II) config/udev: Adding input device ST LIS3LV02DL Accelerometer (/dev/input/js0)
(II) No input driver/identifier specified (ignoring)
(II) config/udev: Adding input device Macintosh mouse button emulation (/dev/input/event4)
(**) Macintosh mouse button emulation: Applying InputClass "evdev pointer catchall"
(**) Macintosh mouse button emulation: always reports core events
(**) Macintosh mouse button emulation: Device: "/dev/input/event4"
(II) Macintosh mouse button emulation: Found 3 mouse buttons
(II) Macintosh mouse button emulation: Found relative axes
(II) Macintosh mouse button emulation: Found x and y relative axes
(II) Macintosh mouse button emulation: Configuring as mouse
(**) Macintosh mouse button emulation: YAxisMapping: buttons 4 and 5
(**) Macintosh mouse button emulation: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) XINPUT: Adding extended input device "Macintosh mouse button emulation" (type: MOUSE)
(II) Macintosh mouse button emulation: initialized for relative axes.
(II) config/udev: Adding input device Macintosh mouse button emulation (/dev/input/mouse0)
(II) No input driver/identifier specified (ignoring)
(II) Aug 18 22:10:37 NVIDIA(0): Setting mode
(II) Aug 18 22:10:37 NVIDIA(0):     "CRT-0:1366x768_60@1366x768+1280+0,DFP-0:1280x800_60@1280x800+0+0"
(II) Power Button: Close
(II) UnloadModule: "evdev"
(II) Video Bus: Close
(II) UnloadModule: "evdev"
(II) Power Button: Close
(II) UnloadModule: "evdev"
(II) Sleep Button: Close
(II) UnloadModule: "evdev"
(II) Logitech USB Receiver: Close
(II) UnloadModule: "evdev"
(II) Logitech USB Receiver: Close
(II) UnloadModule: "evdev"
(II) HP Webcam: Close
(II) UnloadModule: "evdev"
(II) AT Translated Set 2 keyboard: Close
(II) UnloadModule: "evdev"
(II) Macintosh mouse button emulation: Close
(II) UnloadModule: "evdev"
 ddxSigGiveUp: Closing log

____________________________________________

/var/log/Xorg.1.log

X.Org X Server 1.7.6
Release Date: 2010-03-17
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-27-server x86_64 Ubuntu
Current Operating System: Linux notebook 2.6.32-24-generic #39-Ubuntu SMP Wed Jul 28 05:14:15 UTC 2010 x86_64
Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.32-24-generic root=UUID=2846023d-9f02-4faa-a800-861f102d748e ro quiet splash
Build Date: 16 June 2010  09:34:29AM
xorg-server 2:1.7.6-2ubuntu7.2 (For technical support please see http://www.ubuntu.com/support) 
Current version of pixman: 0.16.4
	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.1.log", Time: Sun Aug  8 23:45:58 2010
(==) Using config file: "/etc/X11/xorg.conf"
(==) Using config directory: "/usr/lib/X11/xorg.conf.d"
(==) ServerLayout "Layout0"
(**) |-->Screen "Screen0" (0)
(**) |   |-->Monitor "Monitor0"
(**) |   |-->Device "Device0"
(**) |-->Input Device "Keyboard0"
(**) |-->Input Device "Mouse0"
(**) Option "Xinerama" "0"
(==) Automatically adding devices
(==) Automatically enabling devices
(WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
	Entry deleted from font path.
(==) FontPath set to:
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/100dpi/:unscaled,
	/usr/share/fonts/X11/75dpi/:unscaled,
	/usr/share/fonts/X11/Type1,
	/usr/share/fonts/X11/100dpi,
	/usr/share/fonts/X11/75dpi,
	/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
	built-ins
(==) ModulePath set to "/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
(WW) AllowEmptyInput is on, devices using drivers 'kbd', 'mouse' or 'vmmouse' will be disabled.
(WW) Disabling Keyboard0
(WW) Disabling Mouse0
(II) Loader magic: 0x7ca300
(II) Module ABI versions:
	X.Org ANSI C Emulation: 0.4
	X.Org Video Driver: 6.0
	X.Org XInput driver : 7.0
	X.Org Server Extension : 2.0
(--) using VT number 8

(--) PCI:*(0:1:0:0) 10de:0649:103c:3603 nVidia Corporation G96 [GeForce 9600M GT] rev 161, Mem @ 0xd2000000/16777216, 0xc0000000/268435456, 0xd0000000/33554432, I/O @ 0x00009000/128
(II) Open ACPI successful (/var/run/acpid.socket)
(II) "extmod" will be loaded by default.
(II) "dbe" will be loaded by default.
(II) "glx" will be loaded. This was enabled by default and also specified in the config file.
(II) "record" will be loaded by default.
(II) "dri" will be loaded by default.
(II) "dri2" will be loaded by default.
(II) LoadModule: "glx"
(II) Loading /usr/lib/xorg/modules/extensions/libglx.so
(II) Module glx: vendor="X.Org Foundation"
	compiled for 1.7.6, module version = 1.0.0
	ABI class: X.Org Server Extension, version 2.0
(==) AIGLX enabled
(II) Loading extension GLX
(II) LoadModule: "extmod"
(II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
(II) Module extmod: vendor="X.Org Foundation"
	compiled for 1.7.6, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 2.0
(II) Loading extension MIT-SCREEN-SAVER
(II) Loading extension XFree86-VidModeExtension
(II) Loading extension XFree86-DGA
(II) Loading extension DPMS
(II) Loading extension XVideo
(II) Loading extension XVideo-MotionCompensation
(II) Loading extension X-Resource
(II) LoadModule: "dbe"
(II) Loading /usr/lib/xorg/modules/extensions/libdbe.so
(II) Module dbe: vendor="X.Org Foundation"
	compiled for 1.7.6, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 2.0
(II) Loading extension DOUBLE-BUFFER
(II) LoadModule: "record"
(II) Loading /usr/lib/xorg/modules/extensions/librecord.so
(II) Module record: vendor="X.Org Foundation"
	compiled for 1.7.6, module version = 1.13.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 2.0
(II) Loading extension RECORD
(II) LoadModule: "dri"
(II) Loading /usr/lib/xorg/modules/extensions/libdri.so
(II) Module dri: vendor="X.Org Foundation"
	compiled for 1.7.6, module version = 1.0.0
	ABI class: X.Org Server Extension, version 2.0
(II) Loading extension XFree86-DRI
(II) LoadModule: "dri2"
(II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
(II) Module dri2: vendor="X.Org Foundation"
	compiled for 1.7.6, module version = 1.1.0
	ABI class: X.Org Server Extension, version 2.0
(II) Loading extension DRI2
(II) LoadModule: "nvidia"
(WW) Warning, couldn't open module nvidia
(II) UnloadModule: "nvidia"
(EE) Failed to load module "nvidia" (module does not exist, 0)
(EE) No drivers available.

Fatal server error:
no screens found

Please consult the The X.Org Foundation support 
	 at http://wiki.x.org
 for help. 
Please also check the log file at "/var/log/Xorg.1.log" for additional information.

 ddxSigGiveUp: Closing log

____________________________________________

/var/log/Xorg.1.log.old

X.Org X Server 1.7.6
Release Date: 2010-03-17
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-27-server x86_64 Ubuntu
Current Operating System: Linux notebook 2.6.32-24-generic #39-Ubuntu SMP Wed Jul 28 05:14:15 UTC 2010 x86_64
Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.32-24-generic root=UUID=2846023d-9f02-4faa-a800-861f102d748e ro quiet splash
Build Date: 16 June 2010  09:34:29AM
xorg-server 2:1.7.6-2ubuntu7.2 (For technical support please see http://www.ubuntu.com/support) 
Current version of pixman: 0.16.4
	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.1.log", Time: Sun Aug  8 23:43:07 2010
(==) Using config file: "/etc/X11/xorg.conf"
(==) Using config directory: "/usr/lib/X11/xorg.conf.d"
(==) ServerLayout "Layout0"
(**) |-->Screen "Screen0" (0)
(**) |   |-->Monitor "Monitor0"
(**) |   |-->Device "Device0"
(**) |-->Input Device "Keyboard0"
(**) |-->Input Device "Mouse0"
(**) Option "Xinerama" "0"
(==) Automatically adding devices
(==) Automatically enabling devices
(WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
	Entry deleted from font path.
(==) FontPath set to:
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/100dpi/:unscaled,
	/usr/share/fonts/X11/75dpi/:unscaled,
	/usr/share/fonts/X11/Type1,
	/usr/share/fonts/X11/100dpi,
	/usr/share/fonts/X11/75dpi,
	/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
	built-ins
(==) ModulePath set to "/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
(WW) AllowEmptyInput is on, devices using drivers 'kbd', 'mouse' or 'vmmouse' will be disabled.
(WW) Disabling Keyboard0
(WW) Disabling Mouse0
(II) Loader magic: 0x7ca300
(II) Module ABI versions:
	X.Org ANSI C Emulation: 0.4
	X.Org Video Driver: 6.0
	X.Org XInput driver : 7.0
	X.Org Server Extension : 2.0
(--) using VT number 7

(--) PCI:*(0:1:0:0) 10de:0649:103c:3603 nVidia Corporation G96 [GeForce 9600M GT] rev 161, Mem @ 0xd2000000/16777216, 0xc0000000/268435456, 0xd0000000/33554432, I/O @ 0x00009000/128
(II) Open ACPI successful (/var/run/acpid.socket)
(II) "extmod" will be loaded by default.
(II) "dbe" will be loaded by default.
(II) "glx" will be loaded. This was enabled by default and also specified in the config file.
(II) "record" will be loaded by default.
(II) "dri" will be loaded by default.
(II) "dri2" will be loaded by default.
(II) LoadModule: "glx"
(II) Loading /usr/lib/xorg/modules/extensions/libglx.so
(II) Module glx: vendor="X.Org Foundation"
	compiled for 1.7.6, module version = 1.0.0
	ABI class: X.Org Server Extension, version 2.0
(==) AIGLX enabled
(II) Loading extension GLX
(II) LoadModule: "extmod"
(II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
(II) Module extmod: vendor="X.Org Foundation"
	compiled for 1.7.6, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 2.0
(II) Loading extension MIT-SCREEN-SAVER
(II) Loading extension XFree86-VidModeExtension
(II) Loading extension XFree86-DGA
(II) Loading extension DPMS
(II) Loading extension XVideo
(II) Loading extension XVideo-MotionCompensation
(II) Loading extension X-Resource
(II) LoadModule: "dbe"
(II) Loading /usr/lib/xorg/modules/extensions/libdbe.so
(II) Module dbe: vendor="X.Org Foundation"
	compiled for 1.7.6, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 2.0
(II) Loading extension DOUBLE-BUFFER
(II) LoadModule: "record"
(II) Loading /usr/lib/xorg/modules/extensions/librecord.so
(II) Module record: vendor="X.Org Foundation"
	compiled for 1.7.6, module version = 1.13.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 2.0
(II) Loading extension RECORD
(II) LoadModule: "dri"
(II) Loading /usr/lib/xorg/modules/extensions/libdri.so
(II) Module dri: vendor="X.Org Foundation"
	compiled for 1.7.6, module version = 1.0.0
	ABI class: X.Org Server Extension, version 2.0
(II) Loading extension XFree86-DRI
(II) LoadModule: "dri2"
(II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
(II) Module dri2: vendor="X.Org Foundation"
	compiled for 1.7.6, module version = 1.1.0
	ABI class: X.Org Server Extension, version 2.0
(II) Loading extension DRI2
(II) LoadModule: "nvidia"
(WW) Warning, couldn't open module nvidia
(II) UnloadModule: "nvidia"
(EE) Failed to load module "nvidia" (module does not exist, 0)
(EE) No drivers available.

Fatal server error:
no screens found

Please consult the The X.Org Foundation support 
	 at http://wiki.x.org
 for help. 
Please also check the log file at "/var/log/Xorg.1.log" for additional information.

 ddxSigGiveUp: Closing log

____________________________________________

/var/log/Xorg.2.log

X.Org X Server 1.7.6
Release Date: 2010-03-17
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-27-server x86_64 Ubuntu
Current Operating System: Linux notebook 2.6.32-24-generic #39-Ubuntu SMP Wed Jul 28 05:14:15 UTC 2010 x86_64
Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.32-24-generic root=UUID=2846023d-9f02-4faa-a800-861f102d748e ro quiet splash
Build Date: 16 June 2010  09:34:29AM
xorg-server 2:1.7.6-2ubuntu7.2 (For technical support please see http://www.ubuntu.com/support) 
Current version of pixman: 0.16.4
	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.2.log", Time: Sun Aug  8 23:45:58 2010
(==) Using config file: "/etc/X11/xorg.conf"
(==) Using config directory: "/usr/lib/X11/xorg.conf.d"
(==) ServerLayout "Layout0"
(**) |-->Screen "Screen0" (0)
(**) |   |-->Monitor "Monitor0"
(**) |   |-->Device "Device0"
(**) |-->Input Device "Keyboard0"
(**) |-->Input Device "Mouse0"
(**) Option "Xinerama" "0"
(==) Automatically adding devices
(==) Automatically enabling devices
(WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
	Entry deleted from font path.
(==) FontPath set to:
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/100dpi/:unscaled,
	/usr/share/fonts/X11/75dpi/:unscaled,
	/usr/share/fonts/X11/Type1,
	/usr/share/fonts/X11/100dpi,
	/usr/share/fonts/X11/75dpi,
	/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
	built-ins
(==) ModulePath set to "/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
(WW) AllowEmptyInput is on, devices using drivers 'kbd', 'mouse' or 'vmmouse' will be disabled.
(WW) Disabling Keyboard0
(WW) Disabling Mouse0
(II) Loader magic: 0x7ca300
(II) Module ABI versions:
	X.Org ANSI C Emulation: 0.4
	X.Org Video Driver: 6.0
	X.Org XInput driver : 7.0
	X.Org Server Extension : 2.0
(--) using VT number 8

(--) PCI:*(0:1:0:0) 10de:0649:103c:3603 nVidia Corporation G96 [GeForce 9600M GT] rev 161, Mem @ 0xd2000000/16777216, 0xc0000000/268435456, 0xd0000000/33554432, I/O @ 0x00009000/128
(II) Open ACPI successful (/var/run/acpid.socket)
(II) "extmod" will be loaded by default.
(II) "dbe" will be loaded by default.
(II) "glx" will be loaded. This was enabled by default and also specified in the config file.
(II) "record" will be loaded by default.
(II) "dri" will be loaded by default.
(II) "dri2" will be loaded by default.
(II) LoadModule: "glx"
(II) Loading /usr/lib/xorg/modules/extensions/libglx.so
(II) Module glx: vendor="X.Org Foundation"
	compiled for 1.7.6, module version = 1.0.0
	ABI class: X.Org Server Extension, version 2.0
(==) AIGLX enabled
(II) Loading extension GLX
(II) LoadModule: "extmod"
(II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
(II) Module extmod: vendor="X.Org Foundation"
	compiled for 1.7.6, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 2.0
(II) Loading extension MIT-SCREEN-SAVER
(II) Loading extension XFree86-VidModeExtension
(II) Loading extension XFree86-DGA
(II) Loading extension DPMS
(II) Loading extension XVideo
(II) Loading extension XVideo-MotionCompensation
(II) Loading extension X-Resource
(II) LoadModule: "dbe"
(II) Loading /usr/lib/xorg/modules/extensions/libdbe.so
(II) Module dbe: vendor="X.Org Foundation"
	compiled for 1.7.6, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 2.0
(II) Loading extension DOUBLE-BUFFER
(II) LoadModule: "record"
(II) Loading /usr/lib/xorg/modules/extensions/librecord.so
(II) Module record: vendor="X.Org Foundation"
	compiled for 1.7.6, module version = 1.13.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 2.0
(II) Loading extension RECORD
(II) LoadModule: "dri"
(II) Loading /usr/lib/xorg/modules/extensions/libdri.so
(II) Module dri: vendor="X.Org Foundation"
	compiled for 1.7.6, module version = 1.0.0
	ABI class: X.Org Server Extension, version 2.0
(II) Loading extension XFree86-DRI
(II) LoadModule: "dri2"
(II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
(II) Module dri2: vendor="X.Org Foundation"
	compiled for 1.7.6, module version = 1.1.0
	ABI class: X.Org Server Extension, version 2.0
(II) Loading extension DRI2
(II) LoadModule: "nvidia"
(WW) Warning, couldn't open module nvidia
(II) UnloadModule: "nvidia"
(EE) Failed to load module "nvidia" (module does not exist, 0)
(EE) No drivers available.

Fatal server error:
no screens found

Please consult the The X.Org Foundation support 
	 at http://wiki.x.org
 for help. 
Please also check the log file at "/var/log/Xorg.2.log" for additional information.

 ddxSigGiveUp: Closing log

____________________________________________

/var/log/Xorg.2.log.old

X.Org X Server 1.7.6
Release Date: 2010-03-17
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-27-server x86_64 Ubuntu
Current Operating System: Linux notebook 2.6.32-24-generic #39-Ubuntu SMP Wed Jul 28 05:14:15 UTC 2010 x86_64
Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.32-24-generic root=UUID=2846023d-9f02-4faa-a800-861f102d748e ro quiet splash
Build Date: 16 June 2010  09:34:29AM
xorg-server 2:1.7.6-2ubuntu7.2 (For technical support please see http://www.ubuntu.com/support) 
Current version of pixman: 0.16.4
	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.2.log", Time: Sun Aug  8 23:43:08 2010
(==) Using config file: "/etc/X11/xorg.conf"
(==) Using config directory: "/usr/lib/X11/xorg.conf.d"
(==) ServerLayout "Layout0"
(**) |-->Screen "Screen0" (0)
(**) |   |-->Monitor "Monitor0"
(**) |   |-->Device "Device0"
(**) |-->Input Device "Keyboard0"
(**) |-->Input Device "Mouse0"
(**) Option "Xinerama" "0"
(==) Automatically adding devices
(==) Automatically enabling devices
(WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
	Entry deleted from font path.
(==) FontPath set to:
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/100dpi/:unscaled,
	/usr/share/fonts/X11/75dpi/:unscaled,
	/usr/share/fonts/X11/Type1,
	/usr/share/fonts/X11/100dpi,
	/usr/share/fonts/X11/75dpi,
	/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
	built-ins
(==) ModulePath set to "/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
(WW) AllowEmptyInput is on, devices using drivers 'kbd', 'mouse' or 'vmmouse' will be disabled.
(WW) Disabling Keyboard0
(WW) Disabling Mouse0
(II) Loader magic: 0x7ca300
(II) Module ABI versions:
	X.Org ANSI C Emulation: 0.4
	X.Org Video Driver: 6.0
	X.Org XInput driver : 7.0
	X.Org Server Extension : 2.0
(--) using VT number 7

(--) PCI:*(0:1:0:0) 10de:0649:103c:3603 nVidia Corporation G96 [GeForce 9600M GT] rev 161, Mem @ 0xd2000000/16777216, 0xc0000000/268435456, 0xd0000000/33554432, I/O @ 0x00009000/128
(II) Open ACPI successful (/var/run/acpid.socket)
(II) "extmod" will be loaded by default.
(II) "dbe" will be loaded by default.
(II) "glx" will be loaded. This was enabled by default and also specified in the config file.
(II) "record" will be loaded by default.
(II) "dri" will be loaded by default.
(II) "dri2" will be loaded by default.
(II) LoadModule: "glx"
(II) Loading /usr/lib/xorg/modules/extensions/libglx.so
(II) Module glx: vendor="X.Org Foundation"
	compiled for 1.7.6, module version = 1.0.0
	ABI class: X.Org Server Extension, version 2.0
(==) AIGLX enabled
(II) Loading extension GLX
(II) LoadModule: "extmod"
(II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
(II) Module extmod: vendor="X.Org Foundation"
	compiled for 1.7.6, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 2.0
(II) Loading extension MIT-SCREEN-SAVER
(II) Loading extension XFree86-VidModeExtension
(II) Loading extension XFree86-DGA
(II) Loading extension DPMS
(II) Loading extension XVideo
(II) Loading extension XVideo-MotionCompensation
(II) Loading extension X-Resource
(II) LoadModule: "dbe"
(II) Loading /usr/lib/xorg/modules/extensions/libdbe.so
(II) Module dbe: vendor="X.Org Foundation"
	compiled for 1.7.6, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 2.0
(II) Loading extension DOUBLE-BUFFER
(II) LoadModule: "record"
(II) Loading /usr/lib/xorg/modules/extensions/librecord.so
(II) Module record: vendor="X.Org Foundation"
	compiled for 1.7.6, module version = 1.13.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 2.0
(II) Loading extension RECORD
(II) LoadModule: "dri"
(II) Loading /usr/lib/xorg/modules/extensions/libdri.so
(II) Module dri: vendor="X.Org Foundation"
	compiled for 1.7.6, module version = 1.0.0
	ABI class: X.Org Server Extension, version 2.0
(II) Loading extension XFree86-DRI
(II) LoadModule: "dri2"
(II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
(II) Module dri2: vendor="X.Org Foundation"
	compiled for 1.7.6, module version = 1.1.0
	ABI class: X.Org Server Extension, version 2.0
(II) Loading extension DRI2
(II) LoadModule: "nvidia"
(WW) Warning, couldn't open module nvidia
(II) UnloadModule: "nvidia"
(EE) Failed to load module "nvidia" (module does not exist, 0)
(EE) No drivers available.

Fatal server error:
no screens found

Please consult the The X.Org Foundation support 
	 at http://wiki.x.org
 for help. 
Please also check the log file at "/var/log/Xorg.2.log" for additional information.

 ddxSigGiveUp: Closing log

____________________________________________

/var/log/Xorg.3.log

X.Org X Server 1.7.6
Release Date: 2010-03-17
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-27-server x86_64 Ubuntu
Current Operating System: Linux notebook 2.6.32-24-generic #39-Ubuntu SMP Wed Jul 28 05:14:15 UTC 2010 x86_64
Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.32-24-generic root=UUID=2846023d-9f02-4faa-a800-861f102d748e ro quiet splash
Build Date: 16 June 2010  09:34:29AM
xorg-server 2:1.7.6-2ubuntu7.2 (For technical support please see http://www.ubuntu.com/support) 
Current version of pixman: 0.16.4
	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.3.log", Time: Sun Aug  8 23:45:58 2010
(==) Using config file: "/etc/X11/xorg.conf"
(==) Using config directory: "/usr/lib/X11/xorg.conf.d"
(==) ServerLayout "Layout0"
(**) |-->Screen "Screen0" (0)
(**) |   |-->Monitor "Monitor0"
(**) |   |-->Device "Device0"
(**) |-->Input Device "Keyboard0"
(**) |-->Input Device "Mouse0"
(**) Option "Xinerama" "0"
(==) Automatically adding devices
(==) Automatically enabling devices
(WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
	Entry deleted from font path.
(==) FontPath set to:
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/100dpi/:unscaled,
	/usr/share/fonts/X11/75dpi/:unscaled,
	/usr/share/fonts/X11/Type1,
	/usr/share/fonts/X11/100dpi,
	/usr/share/fonts/X11/75dpi,
	/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
	built-ins
(==) ModulePath set to "/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
(WW) AllowEmptyInput is on, devices using drivers 'kbd', 'mouse' or 'vmmouse' will be disabled.
(WW) Disabling Keyboard0
(WW) Disabling Mouse0
(II) Loader magic: 0x7ca300
(II) Module ABI versions:
	X.Org ANSI C Emulation: 0.4
	X.Org Video Driver: 6.0
	X.Org XInput driver : 7.0
	X.Org Server Extension : 2.0
(--) using VT number 8

(--) PCI:*(0:1:0:0) 10de:0649:103c:3603 nVidia Corporation G96 [GeForce 9600M GT] rev 161, Mem @ 0xd2000000/16777216, 0xc0000000/268435456, 0xd0000000/33554432, I/O @ 0x00009000/128
(II) Open ACPI successful (/var/run/acpid.socket)
(II) "extmod" will be loaded by default.
(II) "dbe" will be loaded by default.
(II) "glx" will be loaded. This was enabled by default and also specified in the config file.
(II) "record" will be loaded by default.
(II) "dri" will be loaded by default.
(II) "dri2" will be loaded by default.
(II) LoadModule: "glx"
(II) Loading /usr/lib/xorg/modules/extensions/libglx.so
(II) Module glx: vendor="X.Org Foundation"
	compiled for 1.7.6, module version = 1.0.0
	ABI class: X.Org Server Extension, version 2.0
(==) AIGLX enabled
(II) Loading extension GLX
(II) LoadModule: "extmod"
(II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
(II) Module extmod: vendor="X.Org Foundation"
	compiled for 1.7.6, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 2.0
(II) Loading extension MIT-SCREEN-SAVER
(II) Loading extension XFree86-VidModeExtension
(II) Loading extension XFree86-DGA
(II) Loading extension DPMS
(II) Loading extension XVideo
(II) Loading extension XVideo-MotionCompensation
(II) Loading extension X-Resource
(II) LoadModule: "dbe"
(II) Loading /usr/lib/xorg/modules/extensions/libdbe.so
(II) Module dbe: vendor="X.Org Foundation"
	compiled for 1.7.6, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 2.0
(II) Loading extension DOUBLE-BUFFER
(II) LoadModule: "record"
(II) Loading /usr/lib/xorg/modules/extensions/librecord.so
(II) Module record: vendor="X.Org Foundation"
	compiled for 1.7.6, module version = 1.13.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 2.0
(II) Loading extension RECORD
(II) LoadModule: "dri"
(II) Loading /usr/lib/xorg/modules/extensions/libdri.so
(II) Module dri: vendor="X.Org Foundation"
	compiled for 1.7.6, module version = 1.0.0
	ABI class: X.Org Server Extension, version 2.0
(II) Loading extension XFree86-DRI
(II) LoadModule: "dri2"
(II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
(II) Module dri2: vendor="X.Org Foundation"
	compiled for 1.7.6, module version = 1.1.0
	ABI class: X.Org Server Extension, version 2.0
(II) Loading extension DRI2
(II) LoadModule: "nvidia"
(WW) Warning, couldn't open module nvidia
(II) UnloadModule: "nvidia"
(EE) Failed to load module "nvidia" (module does not exist, 0)
(EE) No drivers available.

Fatal server error:
no screens found

Please consult the The X.Org Foundation support 
	 at http://wiki.x.org
 for help. 
Please also check the log file at "/var/log/Xorg.3.log" for additional information.

 ddxSigGiveUp: Closing log

____________________________________________

/var/log/Xorg.3.log.old

X.Org X Server 1.7.6
Release Date: 2010-03-17
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-27-server x86_64 Ubuntu
Current Operating System: Linux notebook 2.6.32-24-generic #39-Ubuntu SMP Wed Jul 28 05:14:15 UTC 2010 x86_64
Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.32-24-generic root=UUID=2846023d-9f02-4faa-a800-861f102d748e ro quiet splash
Build Date: 16 June 2010  09:34:29AM
xorg-server 2:1.7.6-2ubuntu7.2 (For technical support please see http://www.ubuntu.com/support) 
Current version of pixman: 0.16.4
	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.3.log", Time: Sun Aug  8 23:43:08 2010
(==) Using config file: "/etc/X11/xorg.conf"
(==) Using config directory: "/usr/lib/X11/xorg.conf.d"
(==) ServerLayout "Layout0"
(**) |-->Screen "Screen0" (0)
(**) |   |-->Monitor "Monitor0"
(**) |   |-->Device "Device0"
(**) |-->Input Device "Keyboard0"
(**) |-->Input Device "Mouse0"
(**) Option "Xinerama" "0"
(==) Automatically adding devices
(==) Automatically enabling devices
(WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
	Entry deleted from font path.
(==) FontPath set to:
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/100dpi/:unscaled,
	/usr/share/fonts/X11/75dpi/:unscaled,
	/usr/share/fonts/X11/Type1,
	/usr/share/fonts/X11/100dpi,
	/usr/share/fonts/X11/75dpi,
	/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
	built-ins
(==) ModulePath set to "/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
(WW) AllowEmptyInput is on, devices using drivers 'kbd', 'mouse' or 'vmmouse' will be disabled.
(WW) Disabling Keyboard0
(WW) Disabling Mouse0
(II) Loader magic: 0x7ca300
(II) Module ABI versions:
	X.Org ANSI C Emulation: 0.4
	X.Org Video Driver: 6.0
	X.Org XInput driver : 7.0
	X.Org Server Extension : 2.0
(--) using VT number 7

(--) PCI:*(0:1:0:0) 10de:0649:103c:3603 nVidia Corporation G96 [GeForce 9600M GT] rev 161, Mem @ 0xd2000000/16777216, 0xc0000000/268435456, 0xd0000000/33554432, I/O @ 0x00009000/128
(II) Open ACPI successful (/var/run/acpid.socket)
(II) "extmod" will be loaded by default.
(II) "dbe" will be loaded by default.
(II) "glx" will be loaded. This was enabled by default and also specified in the config file.
(II) "record" will be loaded by default.
(II) "dri" will be loaded by default.
(II) "dri2" will be loaded by default.
(II) LoadModule: "glx"
(II) Loading /usr/lib/xorg/modules/extensions/libglx.so
(II) Module glx: vendor="X.Org Foundation"
	compiled for 1.7.6, module version = 1.0.0
	ABI class: X.Org Server Extension, version 2.0
(==) AIGLX enabled
(II) Loading extension GLX
(II) LoadModule: "extmod"
(II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
(II) Module extmod: vendor="X.Org Foundation"
	compiled for 1.7.6, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 2.0
(II) Loading extension MIT-SCREEN-SAVER
(II) Loading extension XFree86-VidModeExtension
(II) Loading extension XFree86-DGA
(II) Loading extension DPMS
(II) Loading extension XVideo
(II) Loading extension XVideo-MotionCompensation
(II) Loading extension X-Resource
(II) LoadModule: "dbe"
(II) Loading /usr/lib/xorg/modules/extensions/libdbe.so
(II) Module dbe: vendor="X.Org Foundation"
	compiled for 1.7.6, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 2.0
(II) Loading extension DOUBLE-BUFFER
(II) LoadModule: "record"
(II) Loading /usr/lib/xorg/modules/extensions/librecord.so
(II) Module record: vendor="X.Org Foundation"
	compiled for 1.7.6, module version = 1.13.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 2.0
(II) Loading extension RECORD
(II) LoadModule: "dri"
(II) Loading /usr/lib/xorg/modules/extensions/libdri.so
(II) Module dri: vendor="X.Org Foundation"
	compiled for 1.7.6, module version = 1.0.0
	ABI class: X.Org Server Extension, version 2.0
(II) Loading extension XFree86-DRI
(II) LoadModule: "dri2"
(II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
(II) Module dri2: vendor="X.Org Foundation"
	compiled for 1.7.6, module version = 1.1.0
	ABI class: X.Org Server Extension, version 2.0
(II) Loading extension DRI2
(II) LoadModule: "nvidia"
(WW) Warning, couldn't open module nvidia
(II) UnloadModule: "nvidia"
(EE) Failed to load module "nvidia" (module does not exist, 0)
(EE) No drivers available.

Fatal server error:
no screens found

Please consult the The X.Org Foundation support 
	 at http://wiki.x.org
 for help. 
Please also check the log file at "/var/log/Xorg.3.log" for additional information.

 ddxSigGiveUp: Closing log

____________________________________________

/var/log/Xorg.4.log

X.Org X Server 1.7.6
Release Date: 2010-03-17
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-27-server x86_64 Ubuntu
Current Operating System: Linux notebook 2.6.32-24-generic #39-Ubuntu SMP Wed Jul 28 05:14:15 UTC 2010 x86_64
Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.32-24-generic root=UUID=2846023d-9f02-4faa-a800-861f102d748e ro quiet splash
Build Date: 16 June 2010  09:34:29AM
xorg-server 2:1.7.6-2ubuntu7.2 (For technical support please see http://www.ubuntu.com/support) 
Current version of pixman: 0.16.4
	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.4.log", Time: Sun Aug  8 23:45:58 2010
(==) Using config file: "/etc/X11/xorg.conf"
(==) Using config directory: "/usr/lib/X11/xorg.conf.d"
(==) ServerLayout "Layout0"
(**) |-->Screen "Screen0" (0)
(**) |   |-->Monitor "Monitor0"
(**) |   |-->Device "Device0"
(**) |-->Input Device "Keyboard0"
(**) |-->Input Device "Mouse0"
(**) Option "Xinerama" "0"
(==) Automatically adding devices
(==) Automatically enabling devices
(WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
	Entry deleted from font path.
(==) FontPath set to:
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/100dpi/:unscaled,
	/usr/share/fonts/X11/75dpi/:unscaled,
	/usr/share/fonts/X11/Type1,
	/usr/share/fonts/X11/100dpi,
	/usr/share/fonts/X11/75dpi,
	/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
	built-ins
(==) ModulePath set to "/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
(WW) AllowEmptyInput is on, devices using drivers 'kbd', 'mouse' or 'vmmouse' will be disabled.
(WW) Disabling Keyboard0
(WW) Disabling Mouse0
(II) Loader magic: 0x7ca300
(II) Module ABI versions:
	X.Org ANSI C Emulation: 0.4
	X.Org Video Driver: 6.0
	X.Org XInput driver : 7.0
	X.Org Server Extension : 2.0
(--) using VT number 8

(--) PCI:*(0:1:0:0) 10de:0649:103c:3603 nVidia Corporation G96 [GeForce 9600M GT] rev 161, Mem @ 0xd2000000/16777216, 0xc0000000/268435456, 0xd0000000/33554432, I/O @ 0x00009000/128
(II) Open ACPI successful (/var/run/acpid.socket)
(II) "extmod" will be loaded by default.
(II) "dbe" will be loaded by default.
(II) "glx" will be loaded. This was enabled by default and also specified in the config file.
(II) "record" will be loaded by default.
(II) "dri" will be loaded by default.
(II) "dri2" will be loaded by default.
(II) LoadModule: "glx"
(II) Loading /usr/lib/xorg/modules/extensions/libglx.so
(II) Module glx: vendor="X.Org Foundation"
	compiled for 1.7.6, module version = 1.0.0
	ABI class: X.Org Server Extension, version 2.0
(==) AIGLX enabled
(II) Loading extension GLX
(II) LoadModule: "extmod"
(II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
(II) Module extmod: vendor="X.Org Foundation"
	compiled for 1.7.6, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 2.0
(II) Loading extension MIT-SCREEN-SAVER
(II) Loading extension XFree86-VidModeExtension
(II) Loading extension XFree86-DGA
(II) Loading extension DPMS
(II) Loading extension XVideo
(II) Loading extension XVideo-MotionCompensation
(II) Loading extension X-Resource
(II) LoadModule: "dbe"
(II) Loading /usr/lib/xorg/modules/extensions/libdbe.so
(II) Module dbe: vendor="X.Org Foundation"
	compiled for 1.7.6, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 2.0
(II) Loading extension DOUBLE-BUFFER
(II) LoadModule: "record"
(II) Loading /usr/lib/xorg/modules/extensions/librecord.so
(II) Module record: vendor="X.Org Foundation"
	compiled for 1.7.6, module version = 1.13.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 2.0
(II) Loading extension RECORD
(II) LoadModule: "dri"
(II) Loading /usr/lib/xorg/modules/extensions/libdri.so
(II) Module dri: vendor="X.Org Foundation"
	compiled for 1.7.6, module version = 1.0.0
	ABI class: X.Org Server Extension, version 2.0
(II) Loading extension XFree86-DRI
(II) LoadModule: "dri2"
(II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
(II) Module dri2: vendor="X.Org Foundation"
	compiled for 1.7.6, module version = 1.1.0
	ABI class: X.Org Server Extension, version 2.0
(II) Loading extension DRI2
(II) LoadModule: "nvidia"
(WW) Warning, couldn't open module nvidia
(II) UnloadModule: "nvidia"
(EE) Failed to load module "nvidia" (module does not exist, 0)
(EE) No drivers available.

Fatal server error:
no screens found

Please consult the The X.Org Foundation support 
	 at http://wiki.x.org
 for help. 
Please also check the log file at "/var/log/Xorg.4.log" for additional information.

 ddxSigGiveUp: Closing log

____________________________________________

/var/log/Xorg.4.log.old

X.Org X Server 1.7.6
Release Date: 2010-03-17
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-27-server x86_64 Ubuntu
Current Operating System: Linux notebook 2.6.32-24-generic #39-Ubuntu SMP Wed Jul 28 05:14:15 UTC 2010 x86_64
Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.32-24-generic root=UUID=2846023d-9f02-4faa-a800-861f102d748e ro quiet splash
Build Date: 16 June 2010  09:34:29AM
xorg-server 2:1.7.6-2ubuntu7.2 (For technical support please see http://www.ubuntu.com/support) 
Current version of pixman: 0.16.4
	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.4.log", Time: Sun Aug  8 23:43:08 2010
(==) Using config file: "/etc/X11/xorg.conf"
(==) Using config directory: "/usr/lib/X11/xorg.conf.d"
(==) ServerLayout "Layout0"
(**) |-->Screen "Screen0" (0)
(**) |   |-->Monitor "Monitor0"
(**) |   |-->Device "Device0"
(**) |-->Input Device "Keyboard0"
(**) |-->Input Device "Mouse0"
(**) Option "Xinerama" "0"
(==) Automatically adding devices
(==) Automatically enabling devices
(WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
	Entry deleted from font path.
(==) FontPath set to:
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/100dpi/:unscaled,
	/usr/share/fonts/X11/75dpi/:unscaled,
	/usr/share/fonts/X11/Type1,
	/usr/share/fonts/X11/100dpi,
	/usr/share/fonts/X11/75dpi,
	/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
	built-ins
(==) ModulePath set to "/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
(WW) AllowEmptyInput is on, devices using drivers 'kbd', 'mouse' or 'vmmouse' will be disabled.
(WW) Disabling Keyboard0
(WW) Disabling Mouse0
(II) Loader magic: 0x7ca300
(II) Module ABI versions:
	X.Org ANSI C Emulation: 0.4
	X.Org Video Driver: 6.0
	X.Org XInput driver : 7.0
	X.Org Server Extension : 2.0
(--) using VT number 7

(--) PCI:*(0:1:0:0) 10de:0649:103c:3603 nVidia Corporation G96 [GeForce 9600M GT] rev 161, Mem @ 0xd2000000/16777216, 0xc0000000/268435456, 0xd0000000/33554432, I/O @ 0x00009000/128
(II) Open ACPI successful (/var/run/acpid.socket)
(II) "extmod" will be loaded by default.
(II) "dbe" will be loaded by default.
(II) "glx" will be loaded. This was enabled by default and also specified in the config file.
(II) "record" will be loaded by default.
(II) "dri" will be loaded by default.
(II) "dri2" will be loaded by default.
(II) LoadModule: "glx"
(II) Loading /usr/lib/xorg/modules/extensions/libglx.so
(II) Module glx: vendor="X.Org Foundation"
	compiled for 1.7.6, module version = 1.0.0
	ABI class: X.Org Server Extension, version 2.0
(==) AIGLX enabled
(II) Loading extension GLX
(II) LoadModule: "extmod"
(II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
(II) Module extmod: vendor="X.Org Foundation"
	compiled for 1.7.6, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 2.0
(II) Loading extension MIT-SCREEN-SAVER
(II) Loading extension XFree86-VidModeExtension
(II) Loading extension XFree86-DGA
(II) Loading extension DPMS
(II) Loading extension XVideo
(II) Loading extension XVideo-MotionCompensation
(II) Loading extension X-Resource
(II) LoadModule: "dbe"
(II) Loading /usr/lib/xorg/modules/extensions/libdbe.so
(II) Module dbe: vendor="X.Org Foundation"
	compiled for 1.7.6, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 2.0
(II) Loading extension DOUBLE-BUFFER
(II) LoadModule: "record"
(II) Loading /usr/lib/xorg/modules/extensions/librecord.so
(II) Module record: vendor="X.Org Foundation"
	compiled for 1.7.6, module version = 1.13.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 2.0
(II) Loading extension RECORD
(II) LoadModule: "dri"
(II) Loading /usr/lib/xorg/modules/extensions/libdri.so
(II) Module dri: vendor="X.Org Foundation"
	compiled for 1.7.6, module version = 1.0.0
	ABI class: X.Org Server Extension, version 2.0
(II) Loading extension XFree86-DRI
(II) LoadModule: "dri2"
(II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
(II) Module dri2: vendor="X.Org Foundation"
	compiled for 1.7.6, module version = 1.1.0
	ABI class: X.Org Server Extension, version 2.0
(II) Loading extension DRI2
(II) LoadModule: "nvidia"
(WW) Warning, couldn't open module nvidia
(II) UnloadModule: "nvidia"
(EE) Failed to load module "nvidia" (module does not exist, 0)
(EE) No drivers available.

Fatal server error:
no screens found

Please consult the The X.Org Foundation support 
	 at http://wiki.x.org
 for help. 
Please also check the log file at "/var/log/Xorg.4.log" for additional information.

 ddxSigGiveUp: Closing log

____________________________________________

/var/log/Xorg.5.log

X.Org X Server 1.7.6
Release Date: 2010-03-17
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-27-server x86_64 Ubuntu
Current Operating System: Linux notebook 2.6.32-24-generic #39-Ubuntu SMP Wed Jul 28 05:14:15 UTC 2010 x86_64
Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.32-24-generic root=UUID=2846023d-9f02-4faa-a800-861f102d748e ro quiet splash
Build Date: 16 June 2010  09:34:29AM
xorg-server 2:1.7.6-2ubuntu7.2 (For technical support please see http://www.ubuntu.com/support) 
Current version of pixman: 0.16.4
	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.5.log", Time: Sun Aug  8 23:45:58 2010
(==) Using config file: "/etc/X11/xorg.conf"
(==) Using config directory: "/usr/lib/X11/xorg.conf.d"
(==) ServerLayout "Layout0"
(**) |-->Screen "Screen0" (0)
(**) |   |-->Monitor "Monitor0"
(**) |   |-->Device "Device0"
(**) |-->Input Device "Keyboard0"
(**) |-->Input Device "Mouse0"
(**) Option "Xinerama" "0"
(==) Automatically adding devices
(==) Automatically enabling devices
(WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
	Entry deleted from font path.
(==) FontPath set to:
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/100dpi/:unscaled,
	/usr/share/fonts/X11/75dpi/:unscaled,
	/usr/share/fonts/X11/Type1,
	/usr/share/fonts/X11/100dpi,
	/usr/share/fonts/X11/75dpi,
	/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
	built-ins
(==) ModulePath set to "/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
(WW) AllowEmptyInput is on, devices using drivers 'kbd', 'mouse' or 'vmmouse' will be disabled.
(WW) Disabling Keyboard0
(WW) Disabling Mouse0
(II) Loader magic: 0x7ca300
(II) Module ABI versions:
	X.Org ANSI C Emulation: 0.4
	X.Org Video Driver: 6.0
	X.Org XInput driver : 7.0
	X.Org Server Extension : 2.0
(--) using VT number 8

(--) PCI:*(0:1:0:0) 10de:0649:103c:3603 nVidia Corporation G96 [GeForce 9600M GT] rev 161, Mem @ 0xd2000000/16777216, 0xc0000000/268435456, 0xd0000000/33554432, I/O @ 0x00009000/128
(II) Open ACPI successful (/var/run/acpid.socket)
(II) "extmod" will be loaded by default.
(II) "dbe" will be loaded by default.
(II) "glx" will be loaded. This was enabled by default and also specified in the config file.
(II) "record" will be loaded by default.
(II) "dri" will be loaded by default.
(II) "dri2" will be loaded by default.
(II) LoadModule: "glx"
(II) Loading /usr/lib/xorg/modules/extensions/libglx.so
(II) Module glx: vendor="X.Org Foundation"
	compiled for 1.7.6, module version = 1.0.0
	ABI class: X.Org Server Extension, version 2.0
(==) AIGLX enabled
(II) Loading extension GLX
(II) LoadModule: "extmod"
(II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
(II) Module extmod: vendor="X.Org Foundation"
	compiled for 1.7.6, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 2.0
(II) Loading extension MIT-SCREEN-SAVER
(II) Loading extension XFree86-VidModeExtension
(II) Loading extension XFree86-DGA
(II) Loading extension DPMS
(II) Loading extension XVideo
(II) Loading extension XVideo-MotionCompensation
(II) Loading extension X-Resource
(II) LoadModule: "dbe"
(II) Loading /usr/lib/xorg/modules/extensions/libdbe.so
(II) Module dbe: vendor="X.Org Foundation"
	compiled for 1.7.6, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 2.0
(II) Loading extension DOUBLE-BUFFER
(II) LoadModule: "record"
(II) Loading /usr/lib/xorg/modules/extensions/librecord.so
(II) Module record: vendor="X.Org Foundation"
	compiled for 1.7.6, module version = 1.13.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 2.0
(II) Loading extension RECORD
(II) LoadModule: "dri"
(II) Loading /usr/lib/xorg/modules/extensions/libdri.so
(II) Module dri: vendor="X.Org Foundation"
	compiled for 1.7.6, module version = 1.0.0
	ABI class: X.Org Server Extension, version 2.0
(II) Loading extension XFree86-DRI
(II) LoadModule: "dri2"
(II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
(II) Module dri2: vendor="X.Org Foundation"
	compiled for 1.7.6, module version = 1.1.0
	ABI class: X.Org Server Extension, version 2.0
(II) Loading extension DRI2
(II) LoadModule: "nvidia"
(WW) Warning, couldn't open module nvidia
(II) UnloadModule: "nvidia"
(EE) Failed to load module "nvidia" (module does not exist, 0)
(EE) No drivers available.

Fatal server error:
no screens found

Please consult the The X.Org Foundation support 
	 at http://wiki.x.org
 for help. 
Please also check the log file at "/var/log/Xorg.5.log" for additional information.

 ddxSigGiveUp: Closing log

____________________________________________

/var/log/Xorg.5.log.old

X.Org X Server 1.7.6
Release Date: 2010-03-17
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-27-server x86_64 Ubuntu
Current Operating System: Linux notebook 2.6.32-24-generic #39-Ubuntu SMP Wed Jul 28 05:14:15 UTC 2010 x86_64
Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.32-24-generic root=UUID=2846023d-9f02-4faa-a800-861f102d748e ro quiet splash
Build Date: 16 June 2010  09:34:29AM
xorg-server 2:1.7.6-2ubuntu7.2 (For technical support please see http://www.ubuntu.com/support) 
Current version of pixman: 0.16.4
	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.5.log", Time: Sun Aug  8 23:43:08 2010
(==) Using config file: "/etc/X11/xorg.conf"
(==) Using config directory: "/usr/lib/X11/xorg.conf.d"
(==) ServerLayout "Layout0"
(**) |-->Screen "Screen0" (0)
(**) |   |-->Monitor "Monitor0"
(**) |   |-->Device "Device0"
(**) |-->Input Device "Keyboard0"
(**) |-->Input Device "Mouse0"
(**) Option "Xinerama" "0"
(==) Automatically adding devices
(==) Automatically enabling devices
(WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
	Entry deleted from font path.
(==) FontPath set to:
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/100dpi/:unscaled,
	/usr/share/fonts/X11/75dpi/:unscaled,
	/usr/share/fonts/X11/Type1,
	/usr/share/fonts/X11/100dpi,
	/usr/share/fonts/X11/75dpi,
	/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
	built-ins
(==) ModulePath set to "/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
(WW) AllowEmptyInput is on, devices using drivers 'kbd', 'mouse' or 'vmmouse' will be disabled.
(WW) Disabling Keyboard0
(WW) Disabling Mouse0
(II) Loader magic: 0x7ca300
(II) Module ABI versions:
	X.Org ANSI C Emulation: 0.4
	X.Org Video Driver: 6.0
	X.Org XInput driver : 7.0
	X.Org Server Extension : 2.0
(--) using VT number 7

(--) PCI:*(0:1:0:0) 10de:0649:103c:3603 nVidia Corporation G96 [GeForce 9600M GT] rev 161, Mem @ 0xd2000000/16777216, 0xc0000000/268435456, 0xd0000000/33554432, I/O @ 0x00009000/128
(II) Open ACPI successful (/var/run/acpid.socket)
(II) "extmod" will be loaded by default.
(II) "dbe" will be loaded by default.
(II) "glx" will be loaded. This was enabled by default and also specified in the config file.
(II) "record" will be loaded by default.
(II) "dri" will be loaded by default.
(II) "dri2" will be loaded by default.
(II) LoadModule: "glx"
(II) Loading /usr/lib/xorg/modules/extensions/libglx.so
(II) Module glx: vendor="X.Org Foundation"
	compiled for 1.7.6, module version = 1.0.0
	ABI class: X.Org Server Extension, version 2.0
(==) AIGLX enabled
(II) Loading extension GLX
(II) LoadModule: "extmod"
(II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
(II) Module extmod: vendor="X.Org Foundation"
	compiled for 1.7.6, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 2.0
(II) Loading extension MIT-SCREEN-SAVER
(II) Loading extension XFree86-VidModeExtension
(II) Loading extension XFree86-DGA
(II) Loading extension DPMS
(II) Loading extension XVideo
(II) Loading extension XVideo-MotionCompensation
(II) Loading extension X-Resource
(II) LoadModule: "dbe"
(II) Loading /usr/lib/xorg/modules/extensions/libdbe.so
(II) Module dbe: vendor="X.Org Foundation"
	compiled for 1.7.6, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 2.0
(II) Loading extension DOUBLE-BUFFER
(II) LoadModule: "record"
(II) Loading /usr/lib/xorg/modules/extensions/librecord.so
(II) Module record: vendor="X.Org Foundation"
	compiled for 1.7.6, module version = 1.13.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 2.0
(II) Loading extension RECORD
(II) LoadModule: "dri"
(II) Loading /usr/lib/xorg/modules/extensions/libdri.so
(II) Module dri: vendor="X.Org Foundation"
	compiled for 1.7.6, module version = 1.0.0
	ABI class: X.Org Server Extension, version 2.0
(II) Loading extension XFree86-DRI
(II) LoadModule: "dri2"
(II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
(II) Module dri2: vendor="X.Org Foundation"
	compiled for 1.7.6, module version = 1.1.0
	ABI class: X.Org Server Extension, version 2.0
(II) Loading extension DRI2
(II) LoadModule: "nvidia"
(WW) Warning, couldn't open module nvidia
(II) UnloadModule: "nvidia"
(EE) Failed to load module "nvidia" (module does not exist, 0)
(EE) No drivers available.

Fatal server error:
no screens found

Please consult the The X.Org Foundation support 
	 at http://wiki.x.org
 for help. 
Please also check the log file at "/var/log/Xorg.5.log" for additional information.

 ddxSigGiveUp: Closing log

____________________________________________

ldd /usr/bin/glxinfo

	linux-vdso.so.1 =>  (0x00007fffd9fff000)
	libGL.so.1 => /usr/lib/libGL.so.1 (0x00007f9e2b152000)
	libm.so.6 => /lib/libm.so.6 (0x00007f9e2aecf000)
	libX11.so.6 => /usr/lib/libX11.so.6 (0x00007f9e2ab98000)
	libpthread.so.0 => /lib/libpthread.so.0 (0x00007f9e2a97b000)
	libc.so.6 => /lib/libc.so.6 (0x00007f9e2a5f8000)
	libnvidia-tls.so.256.44 => /usr/lib/tls/libnvidia-tls.so.256.44 (0x00007f9e2a3f5000)
	libnvidia-glcore.so.256.44 => /usr/lib/libnvidia-glcore.so.256.44 (0x00007f9e28a08000)
	libXext.so.6 => /usr/lib/libXext.so.6 (0x00007f9e287f6000)
	libdl.so.2 => /lib/libdl.so.2 (0x00007f9e285f1000)
	libxcb.so.1 => /usr/lib/libxcb.so.1 (0x00007f9e283d5000)
	/lib64/ld-linux-x86-64.so.2 (0x00007f9e2b478000)
	libXau.so.6 => /usr/lib/libXau.so.6 (0x00007f9e281d0000)
	libXdmcp.so.6 => /usr/lib/libXdmcp.so.6 (0x00007f9e27fca000)

____________________________________________

/usr/bin/lspci -d "10de:*" -v -xxx

01:00.0 VGA compatible controller: nVidia Corporation G96 [GeForce 9600M GT] (rev a1)
	Subsystem: Hewlett-Packard Company Device 3603
	Flags: bus master, fast devsel, latency 0, IRQ 16
	Memory at d2000000 (32-bit, non-prefetchable) [size=16M]
	Memory at c0000000 (64-bit, prefetchable) [size=256M]
	Memory at d0000000 (64-bit, non-prefetchable) [size=32M]
	I/O ports at 9000 [size=128]
	Capabilities: [60] Power Management version 3
	Capabilities: [68] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable-
	Capabilities: [78] Express Endpoint, MSI 00
	Capabilities: [b4] Vendor Specific Information <?>
	Capabilities: [100] Virtual Channel <?>
	Capabilities: [128] Power Budgeting <?>
	Capabilities: [600] Vendor Specific Information <?>
	Kernel driver in use: nvidia
	Kernel modules: nvidia, nvidiafb, nouveau
00: de 10 49 06 07 00 10 00 a1 00 00 03 00 00 00 00
10: 00 00 00 d2 0c 00 00 c0 00 00 00 00 04 00 00 d0
20: 00 00 00 00 01 90 00 00 00 00 00 00 3c 10 03 36
30: 00 00 00 00 60 00 00 00 00 00 00 00 0b 01 00 00
40: 3c 10 03 36 00 00 00 00 00 00 00 00 00 00 00 00
50: 01 00 00 00 01 00 00 00 ce d6 23 00 00 00 00 00
60: 01 68 03 00 08 00 00 00 05 78 80 00 00 00 00 00
70: 00 00 00 00 00 00 00 00 10 b4 02 00 a0 84 2c 01
80: 10 29 00 00 02 2d 00 00 4b 00 01 11 00 00 00 00
90: 00 00 00 00 00 00 00 00 00 00 00 00 10 00 00 00
a0: 00 00 00 00 00 00 00 00 02 00 00 00 00 00 00 00
b0: 00 00 00 00 09 00 14 01 00 00 00 00 00 00 00 00
c0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
d0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
e0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
f0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00


____________________________________________

/usr/bin/lspci -t

-[0000:00]-+-00.0
           +-01.0-[0000:01]----00.0
           +-1a.0
           +-1a.1
           +-1a.7
           +-1b.0
           +-1c.0-[0000:02]----00.0
           +-1c.1-[0000:03]----00.0
           +-1c.2-[0000:04]--
           +-1c.3-[0000:05]--
           +-1c.4-[0000:06]--+-00.0
           |                 +-00.1
           |                 +-00.2
           |                 +-00.3
           |                 \-00.4
           +-1c.5-[0000:07-09]--
           +-1d.0
           +-1d.1
           +-1d.2
           +-1d.3
           +-1d.7
           +-1e.0-[0000:0a]--
           +-1f.0
           +-1f.2
           +-1f.3
           \-1f.6

____________________________________________

/usr/sbin/lsusb

Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 002: ID 03f0:171d Hewlett-Packard Wireless (Bluetooth + WLAN) Interface [Integrated Module]
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 5986:0137 Acer, Inc 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 006: ID 046d:c525 Logitech, Inc. 
Bus 001 Device 004: ID 1a40:0101 TERMINUS TECHNOLOGY INC. 
Bus 001 Device 003: ID 13fe:1a23 Kingston Technology Company Inc. 512MB Flash Drive
Bus 001 Device 002: ID 1a40:0101 TERMINUS TECHNOLOGY INC. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

____________________________________________

/usr/sbin/dmidecode

# dmidecode 2.9
SMBIOS 2.4 present.
26 structures occupying 1116 bytes.
Table at 0x000E5360.

Handle 0x0000, DMI type 0, 24 bytes
BIOS Information
	Vendor: Hewlett-Packard
	Version: F.21
	Release Date: 08/20/2009
	ROM Size: 1024 kB
	Characteristics:
		PCI is supported
		BIOS is upgradeable
		BIOS shadowing is allowed
		Boot from CD is supported
		Selectable boot is supported
		BIOS ROM is socketed
		EDD is supported
		Japanese floppy for NEC 9800 1.2 MB is supported (int 13h)
		Japanese floppy for Toshiba 1.2 MB is supported (int 13h)
		5.25"/360 KB floppy services are supported (int 13h)
		5.25"/1.2 MB floppy services are supported (int 13h)
		3.5"/720 KB floppy services are supported (int 13h)
		3.5"/2.88 MB floppy services are supported (int 13h)
		8042 keyboard services are supported (int 9h)
		CGA/mono video services are supported (int 10h)
		ACPI is supported
		USB legacy is supported
		Targeted content distribution is supported
	BIOS Revision: 15.33
	Firmware Revision: 2.38

Handle 0x0001, DMI type 1, 27 bytes
System Information
	Manufacturer: Hewlett-Packard
	Product Name: HP Pavilion dv5 Notebook PC
	Version: Rev 1
	Serial Number: CNF829298D
	UUID: 434E4638-3239-3239-3844-001E68B07A57
	Wake-up Type: Power Switch
	SKU Number: FM535EA#ACB
	Family: 103C_5335KV

Handle 0x0002, DMI type 2, 16 bytes
Base Board Information
	Manufacturer: Quanta
	Product Name: 3603
	Version: 02.26
	Serial Number: CNF829298D
	Asset Tag: Base Board Asset Tag
	Features:
		Board is a hosting board
		Board is replaceable
	Location In Chassis: Base Board Chassis Location
	Chassis Handle: 0x0003
	Type: Motherboard
	Contained Object Handles: 0

Handle 0x0003, DMI type 3, 22 bytes
Chassis Information
	Manufacturer: Quanta
	Type: Notebook
	Lock: Not Present
	Version: N/A
	Serial Number: None
	Asset Tag: Not Specified
	Boot-up State: Safe
	Power Supply State: Safe
	Thermal State: Safe
	Security Status: None
	OEM Information: 0x0000010C
	Height: Unspecified
	Number Of Power Cords: 1
	Contained Elements: 0

Handle 0x0004, DMI type 9, 13 bytes
System Slot Information
	Designation: PCI Express Graphic X16
	Type: x16 PCI Express
	Current Usage: Available
	Length: Other
	ID: 0
	Characteristics:
		PME signal is supported
		Hot-plug devices are supported

Handle 0x0005, DMI type 9, 13 bytes
System Slot Information
	Designation: PCI Express-0
	Type: x1 PCI Express
	Current Usage: Available
	Length: Other
	ID: 0
	Characteristics:
		PME signal is supported
		Hot-plug devices are supported

Handle 0x0006, DMI type 9, 13 bytes
System Slot Information
	Designation: PCI Express-1
	Type: x1 PCI Express
	Current Usage: Available
	Length: Other
	ID: 1
	Characteristics:
		PME signal is supported
		Hot-plug devices are supported

Handle 0x0007, DMI type 9, 13 bytes
System Slot Information
	Designation: PCI Express-2
	Type: x1 PCI Express
	Current Usage: Available
	Length: Other
	ID: 2
	Characteristics:
		PME signal is supported
		Hot-plug devices are supported

Handle 0x0008, DMI type 9, 13 bytes
System Slot Information
	Designation: PCI Express-3
	Type: x1 PCI Express
	Current Usage: Available
	Length: Other
	ID: 3
	Characteristics:
		PME signal is supported
		Hot-plug devices are supported

Handle 0x0009, DMI type 9, 13 bytes
System Slot Information
	Designation: PCI Express-4
	Type: x1 PCI Express
	Current Usage: Available
	Length: Other
	ID: 4
	Characteristics:
		PME signal is supported
		Hot-plug devices are supported

Handle 0x000A, DMI type 10, 6 bytes
On Board Device Information
	Type: Video
	Status: Enabled
	Description:    

Handle 0x000B, DMI type 11, 5 bytes
OEM Strings
	String 1: $HP$
	String 2: LOC#ACB
	String 3: ABS 70/71 79 7A 7B 7C
	String 4: CNB1 01100000130C10000

Handle 0x000C, DMI type 15, 29 bytes
System Event Log
	Area Length: 32672 bytes
	Header Start Offset: 0x0000
	Data Start Offset: 0x0000
	Access Method: General-purpose non-volatile data functions
	Access Address: 0x0000
	Status: Valid, Not Full
	Change Token: 0x12345678
	Header Format: OEM-specific
	Supported Log Type Descriptors: 3
	Descriptor 1: POST memory resize
	Data Format 1: None
	Descriptor 2: POST error
	Data Format 2: POST results bitmap
	Descriptor 3: Log area reset/cleared
	Data Format 3: None

Handle 0x000D, DMI type 32, 20 bytes
System Boot Information
	Status: No errors detected

Handle 0x000E, DMI type 136, 6 bytes
OEM-specific Type
	Header and Data:
		88 06 0E 00 5A 5A

Handle 0x000F, DMI type 4, 35 bytes
Processor Information
	Socket Designation: CPU
	Type: Central Processor
	Family: Pentium M
	Manufacturer: Intel(R) Corporation
	ID: 76 06 01 00 FF FB EB BF
	Signature: Type 0, Family 6, Model 23, Stepping 6
	Flags:
		FPU (Floating-point unit on-chip)
		VME (Virtual mode extension)
		DE (Debugging extension)
		PSE (Page size extension)
		TSC (Time stamp counter)
		MSR (Model specific registers)
		PAE (Physical address extension)
		MCE (Machine check exception)
		CX8 (CMPXCHG8 instruction supported)
		APIC (On-chip APIC hardware supported)
		SEP (Fast system call)
		MTRR (Memory type range registers)
		PGE (Page global enable)
		MCA (Machine check architecture)
		CMOV (Conditional move instruction supported)
		PAT (Page attribute table)
		PSE-36 (36-bit page size extension)
		CLFSH (CLFLUSH instruction supported)
		DS (Debug store)
		ACPI (ACPI supported)
		MMX (MMX technology supported)
		FXSR (Fast floating-point save and restore)
		SSE (Streaming SIMD extensions)
		SSE2 (Streaming SIMD extensions 2)
		SS (Self-snoop)
		HTT (Hyper-threading technology)
		TM (Thermal monitor supported)
		PBE (Pending break enabled)
	Version: Intel(R) Core(TM)2 Duo CPU     P8600  @ 2.40GHz
	Voltage: 1.6 V
	External Clock: 1066 MHz
	Max Speed: 2400 MHz
	Current Speed: 2400 MHz
	Status: Populated, Enabled
	Upgrade: <OUT OF SPEC>
	L1 Cache Handle: 0x0012
	L2 Cache Handle: 0x0010
	L3 Cache Handle: Not Provided
	Serial Number: Not Specified
	Asset Tag: FFFF
	Part Number: Not Specified

Handle 0x0010, DMI type 7, 19 bytes
Cache Information
	Socket Designation: L2 Cache
	Configuration: Enabled, Not Socketed, Level 2
	Operational Mode: Write Back
	Location: Internal
	Installed Size: 3072 KB
	Maximum Size: 3072 KB
	Supported SRAM Types:
		Synchronous
	Installed SRAM Type: Synchronous
	Speed: Unknown
	Error Correction Type: Single-bit ECC
	System Type: Unified
	Associativity: <OUT OF SPEC>

Handle 0x0011, DMI type 7, 19 bytes
Cache Information
	Socket Designation: L1 Cache
	Configuration: Enabled, Not Socketed, Level 1
	Operational Mode: Write Back
	Location: Internal
	Installed Size: 32 KB
	Maximum Size: 32 KB
	Supported SRAM Types:
		Synchronous
	Installed SRAM Type: Synchronous
	Speed: Unknown
	Error Correction Type: Single-bit ECC
	System Type: Instruction
	Associativity: 8-way Set-associative

Handle 0x0012, DMI type 7, 19 bytes
Cache Information
	Socket Designation: L1 Cache
	Configuration: Enabled, Not Socketed, Level 1
	Operational Mode: Write Back
	Location: Internal
	Installed Size: 32 KB
	Maximum Size: 32 KB
	Supported SRAM Types:
		Synchronous
	Installed SRAM Type: Synchronous
	Speed: Unknown
	Error Correction Type: Single-bit ECC
	System Type: Data
	Associativity: 8-way Set-associative

Handle 0x0013, DMI type 16, 15 bytes
Physical Memory Array
	Location: System Board Or Motherboard
	Use: System Memory
	Error Correction Type: None
	Maximum Capacity: 8 GB
	Error Information Handle: Not Provided
	Number Of Devices: 2

Handle 0x0014, DMI type 17, 27 bytes
Memory Device
	Array Handle: 0x0013
	Error Information Handle: Not Provided
	Total Width: 64 bits
	Data Width: 64 bits
	Size: 2048 MB
	Form Factor: SODIMM
	Set: None
	Locator: DIMM0
	Bank Locator: BANK 0
	Type: DDR2
	Type Detail: Synchronous
	Speed: 800 MHz (1.2 ns)
	Manufacturer: AD00000000000000
	Serial Number: 00004028
	Asset Tag: Unknown
	Part Number: 282828282828282828282828282828282828

Handle 0x0015, DMI type 20, 19 bytes
Memory Device Mapped Address
	Starting Address: 0x00000000000
	Ending Address: 0x0007FFFFFFF
	Range Size: 2 GB
	Physical Device Handle: 0x0014
	Memory Array Mapped Address Handle: 0x0018
	Partition Row Position: 2
	Interleave Position: 1
	Interleaved Data Depth: 1

Handle 0x0016, DMI type 17, 27 bytes
Memory Device
	Array Handle: 0x0013
	Error Information Handle: Not Provided
	Total Width: 64 bits
	Data Width: 64 bits
	Size: 2048 MB
	Form Factor: SODIMM
	Set: None
	Locator: DIMM2
	Bank Locator: BANK 2
	Type: DDR2
	Type Detail: Synchronous
	Speed: 800 MHz (1.2 ns)
	Manufacturer: Samsung
	Serial Number: 64EA9F2E
	Asset Tag: Unknown
	Part Number: 2E2E2E2E2E2E2E2E2E2E2E2E2E2E2E2E2E2E

Handle 0x0017, DMI type 20, 19 bytes
Memory Device Mapped Address
	Starting Address: 0x00000000000
	Ending Address: 0x0007FFFFFFF
	Range Size: 2 GB
	Physical Device Handle: 0x0016
	Memory Array Mapped Address Handle: 0x0018
	Partition Row Position: 2
	Interleave Position: 2
	Interleaved Data Depth: 1

Handle 0x0018, DMI type 19, 15 bytes
Memory Array Mapped Address
	Starting Address: 0x00000000000
	Ending Address: 0x000FFFFFFFF
	Range Size: 4 GB
	Physical Array Handle: 0x0013
	Partition Width: 0

Handle 0x0019, DMI type 127, 4 bytes
End Of Table


____________________________________________

/sbin/modinfo nvidia | grep vermagic

vermagic:       2.6.32-24-generic SMP mod_unload modversions 

____________________________________________

Scanning kernel log files for NVRM messages:

  /var/log/messages:
Aug 15 16:22:00 notebook kernel: [   19.225678] NVRM: loading NVIDIA UNIX x86_64 Kernel Module  256.44  Thu Jul 29 01:22:44 PDT 2010
Aug 15 23:00:54 notebook kernel: [   18.906950] NVRM: loading NVIDIA UNIX x86_64 Kernel Module  256.44  Thu Jul 29 01:22:44 PDT 2010
Aug 16 17:16:36 notebook kernel: [   19.250088] NVRM: loading NVIDIA UNIX x86_64 Kernel Module  256.44  Thu Jul 29 01:22:44 PDT 2010
Aug 17 15:41:44 notebook kernel: [   12.334784] NVRM: loading NVIDIA UNIX x86_64 Kernel Module  256.44  Thu Jul 29 01:22:44 PDT 2010
Aug 17 23:07:07 notebook kernel: [   18.580173] NVRM: loading NVIDIA UNIX x86_64 Kernel Module  256.44  Thu Jul 29 01:22:44 PDT 2010
Aug 18 00:48:27 notebook kernel: [   23.360954] NVRM: loading NVIDIA UNIX x86_64 Kernel Module  256.44  Thu Jul 29 01:22:44 PDT 2010
Aug 18 01:20:13 notebook kernel: [   18.291616] NVRM: loading NVIDIA UNIX x86_64 Kernel Module  256.44  Thu Jul 29 01:22:44 PDT 2010
Aug 18 12:35:28 notebook kernel: [   18.578578] NVRM: loading NVIDIA UNIX x86_64 Kernel Module  256.44  Thu Jul 29 01:22:44 PDT 2010
Aug 18 21:42:05 notebook kernel: [   18.363376] NVRM: loading NVIDIA UNIX x86_64 Kernel Module  256.44  Thu Jul 29 01:22:44 PDT 2010
Aug 18 21:52:10 notebook kernel: [  623.963442] NVRM: loading NVIDIA UNIX x86_64 Kernel Module  256.44  Thu Jul 29 01:22:44 PDT 2010
Aug 18 21:54:38 notebook kernel: [   18.301058] NVRM: loading NVIDIA UNIX x86_64 Kernel Module  256.44  Thu Jul 29 01:22:44 PDT 2010
Aug 19 15:23:17 notebook kernel: [   18.525877] NVRM: loading NVIDIA UNIX x86_64 Kernel Module  256.44  Thu Jul 29 01:22:44 PDT 2010
/var/log/kernel.log is not readable

____________________________________________

dmesg:

[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.32-24-generic (buildd@yellow) (gcc version 4.4.3 (Ubuntu 4.4.3-4ubuntu5) ) #39-Ubuntu SMP Wed Jul 28 05:14:15 UTC 2010 (Ubuntu 2.6.32-24.39-generic 2.6.32.15+drm33.5)
[    0.000000] Command line: BOOT_IMAGE=/boot/vmlinuz-2.6.32-24-generic root=UUID=2846023d-9f02-4faa-a800-861f102d748e ro splash quiet splash nomodeset video=uvesafb:mode_option=1280x800-24,mtrr=3,scroll=ywrap
[    0.000000] KERNEL supported cpus:
[    0.000000]   Intel GenuineIntel
[    0.000000]   AMD AuthenticAMD
[    0.000000]   Centaur CentaurHauls
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009e000 (usable)
[    0.000000]  BIOS-e820: 000000000009e000 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000e0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 00000000bca99000 (usable)
[    0.000000]  BIOS-e820: 00000000bca99000 - 00000000bca9c000 (ACPI NVS)
[    0.000000]  BIOS-e820: 00000000bca9c000 - 00000000bdea8000 (usable)
[    0.000000]  BIOS-e820: 00000000bdea8000 - 00000000bdebf000 (reserved)
[    0.000000]  BIOS-e820: 00000000bdebf000 - 00000000bdf86000 (usable)
[    0.000000]  BIOS-e820: 00000000bdf86000 - 00000000bdfbf000 (ACPI NVS)
[    0.000000]  BIOS-e820: 00000000bdfbf000 - 00000000bdfe0000 (usable)
[    0.000000]  BIOS-e820: 00000000bdfe0000 - 00000000bdff6000 (ACPI data)
[    0.000000]  BIOS-e820: 00000000bdff6000 - 00000000be000000 (usable)
[    0.000000]  BIOS-e820: 00000000be000000 - 00000000c0000000 (reserved)
[    0.000000]  BIOS-e820: 00000000f8000000 - 00000000fc000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec01000 (reserved)
[    0.000000]  BIOS-e820: 00000000fed10000 - 00000000fed14000 (reserved)
[    0.000000]  BIOS-e820: 00000000fed18000 - 00000000fed1a000 (reserved)
[    0.000000]  BIOS-e820: 00000000fed1c000 - 00000000fed20000 (reserved)
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  BIOS-e820: 00000000fff00000 - 0000000100000000 (reserved)
[    0.000000]  BIOS-e820: 0000000100000000 - 0000000140000000 (usable)
[    0.000000] DMI 2.4 present.
[    0.000000] last_pfn = 0x140000 max_arch_pfn = 0x400000000
[    0.000000] MTRR default type: uncachable
[    0.000000] MTRR fixed ranges enabled:
[    0.000000]   00000-9FFFF write-back
[    0.000000]   A0000-BFFFF uncachable
[    0.000000]   C0000-FFFFF write-protect
[    0.000000] MTRR variable ranges enabled:
[    0.000000]   0 base 000000000 mask F80000000 write-back
[    0.000000]   1 base 0FFFE0000 mask FFFFE0000 write-protect
[    0.000000]   2 base 0FFFD8000 mask FFFFF8000 write-protect
[    0.000000]   3 base 080000000 mask FC0000000 write-back
[    0.000000]   4 base 0BE000000 mask FFE000000 uncachable
[    0.000000]   5 base 100000000 mask FC0000000 write-back
[    0.000000]   6 disabled
[    0.000000]   7 disabled
[    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
[    0.000000] last_pfn = 0xbe000 max_arch_pfn = 0x400000000
[    0.000000] e820 update range: 0000000000001000 - 0000000000006000 (usable) ==> (reserved)
[    0.000000] Scanning 1 areas for low memory corruption
[    0.000000] modified physical RAM map:
[    0.000000]  modified: 0000000000000000 - 0000000000001000 (usable)
[    0.000000]  modified: 0000000000001000 - 0000000000006000 (reserved)
[    0.000000]  modified: 0000000000006000 - 000000000009e000 (usable)
[    0.000000]  modified: 000000000009e000 - 00000000000a0000 (reserved)
[    0.000000]  modified: 00000000000e0000 - 0000000000100000 (reserved)
[    0.000000]  modified: 0000000000100000 - 00000000bca99000 (usable)
[    0.000000]  modified: 00000000bca99000 - 00000000bca9c000 (ACPI NVS)
[    0.000000]  modified: 00000000bca9c000 - 00000000bdea8000 (usable)
[    0.000000]  modified: 00000000bdea8000 - 00000000bdebf000 (reserved)
[    0.000000]  modified: 00000000bdebf000 - 00000000bdf86000 (usable)
[    0.000000]  modified: 00000000bdf86000 - 00000000bdfbf000 (ACPI NVS)
[    0.000000]  modified: 00000000bdfbf000 - 00000000bdfe0000 (usable)
[    0.000000]  modified: 00000000bdfe0000 - 00000000bdff6000 (ACPI data)
[    0.000000]  modified: 00000000bdff6000 - 00000000be000000 (usable)
[    0.000000]  modified: 00000000be000000 - 00000000c0000000 (reserved)
[    0.000000]  modified: 00000000f8000000 - 00000000fc000000 (reserved)
[    0.000000]  modified: 00000000fec00000 - 00000000fec01000 (reserved)
[    0.000000]  modified: 00000000fed10000 - 00000000fed14000 (reserved)
[    0.000000]  modified: 00000000fed18000 - 00000000fed1a000 (reserved)
[    0.000000]  modified: 00000000fed1c000 - 00000000fed20000 (reserved)
[    0.000000]  modified: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  modified: 00000000fff00000 - 0000000100000000 (reserved)
[    0.000000]  modified: 0000000100000000 - 0000000140000000 (usable)
[    0.000000] initial memory mapped : 0 - 20000000
[    0.000000] init_memory_mapping: 0000000000000000-00000000be000000
[    0.000000] NX (Execute Disable) protection: active
[    0.000000]  0000000000 - 00be000000 page 2M
[    0.000000] kernel direct mapping tables up to be000000 @ 8000-c000
[    0.000000] init_memory_mapping: 0000000100000000-0000000140000000
[    0.000000] NX (Execute Disable) protection: active
[    0.000000]  0100000000 - 0140000000 page 2M
[    0.000000] kernel direct mapping tables up to 140000000 @ a000-10000
[    0.000000] RAMDISK: 37135000 - 37fef674
[    0.000000] ACPI: RSDP 00000000000fe020 00024 (v02 HPQOEM)
[    0.000000] ACPI: XSDT 00000000bdff5120 0006C (v01 HPQOEM SLIC-MPC 00000001      01000013)
[    0.000000] ACPI: FACP 00000000bdff3000 000F4 (v04 HPQOEM SLIC-MPC 00000001 MSFT 01000013)
[    0.000000] ACPI: DSDT 00000000bdfe3000 0BBE9 (v01 HPQOEM SLIC-MPC 00000001 MSFT 01000013)
[    0.000000] ACPI: FACS 00000000bdf92000 00040
[    0.000000] ACPI: DMAR 00000000bdff4000 000B0 (v01               ? 00000001      00000000)
[    0.000000] ACPI: HPET 00000000bdff2000 00038 (v01 HPQOEM SLIC-MPC 00000001 MSFT 01000013)
[    0.000000] ACPI: APIC 00000000bdff1000 0006C (v02 HPQOEM SLIC-MPC 00000001 MSFT 01000013)
[    0.000000] ACPI: MCFG 00000000bdff0000 0003C (v01 HPQOEM SLIC-MPC 00000001 MSFT 01000013)
[    0.000000] ACPI: ASF! 00000000bdfef000 000A5 (v32 HPQOEM SLIC-MPC 00000001 MSFT 01000013)
[    0.000000] ACPI: SLIC 00000000bdfe2000 00176 (v01 HPQOEM SLIC-MPC 06040000  LTP 00000001)
[    0.000000] ACPI: BOOT 00000000bdfe1000 00028 (v01 HPQOEM SLIC-MPC 00000001 MSFT 01000013)
[    0.000000] ACPI: SSDT 00000000bdfe0000 00655 (v01  PmRef    CpuPm 00003000 INTL 20051117)
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] No NUMA configuration found
[    0.000000] Faking a node at 0000000000000000-0000000140000000
[    0.000000] Bootmem setup node 0 0000000000000000-0000000140000000
[    0.000000]   NODE_DATA [000000000000b000 - 000000000000ffff]
[    0.000000]   bootmap [0000000000010000 -  0000000000037fff] pages 28
[    0.000000] (8 early reservations) ==> bootmem [0000000000 - 0140000000]
[    0.000000]   #0 [0000000000 - 0000001000]   BIOS data page ==> [0000000000 - 0000001000]
[    0.000000]   #1 [0000006000 - 0000008000]       TRAMPOLINE ==> [0000006000 - 0000008000]
[    0.000000]   #2 [0001000000 - 0001a2fe64]    TEXT DATA BSS ==> [0001000000 - 0001a2fe64]
[    0.000000]   #3 [0037135000 - 0037fef674]          RAMDISK ==> [0037135000 - 0037fef674]
[    0.000000]   #4 [000009e000 - 0000100000]    BIOS reserved ==> [000009e000 - 0000100000]
[    0.000000]   #5 [0001a30000 - 0001a301f0]              BRK ==> [0001a30000 - 0001a301f0]
[    0.000000]   #6 [0000008000 - 000000a000]          PGTABLE ==> [0000008000 - 000000a000]
[    0.000000]   #7 [000000a000 - 000000b000]          PGTABLE ==> [000000a000 - 000000b000]
[    0.000000]  [ffffea0000000000-ffffea00045fffff] PMD -> [ffff880028600000-ffff88002bdfffff] on node 0
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000000 -> 0x00001000
[    0.000000]   DMA32    0x00001000 -> 0x00100000
[    0.000000]   Normal   0x00100000 -> 0x00140000
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[8] active PFN ranges
[    0.000000]     0: 0x00000000 -> 0x00000001
[    0.000000]     0: 0x00000006 -> 0x0000009e
[    0.000000]     0: 0x00000100 -> 0x000bca99
[    0.000000]     0: 0x000bca9c -> 0x000bdea8
[    0.000000]     0: 0x000bdebf -> 0x000bdf86
[    0.000000]     0: 0x000bdfbf -> 0x000bdfe0
[    0.000000]     0: 0x000bdff6 -> 0x000be000
[    0.000000]     0: 0x00100000 -> 0x00140000
[    0.000000] On node 0 totalpages: 1040176
[    0.000000]   DMA zone: 56 pages used for memmap
[    0.000000]   DMA zone: 104 pages reserved
[    0.000000]   DMA zone: 3833 pages, LIFO batch:0
[    0.000000]   DMA32 zone: 14280 pages used for memmap
[    0.000000]   DMA32 zone: 759759 pages, LIFO batch:31
[    0.000000]   Normal zone: 3584 pages used for memmap
[    0.000000]   Normal zone: 258560 pages, LIFO batch:31
[    0.000000] ACPI: PM-Timer IO Port: 0x408
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x01] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x00] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x04] lapic_id[0x00] disabled)
[    0.000000] ACPI: IOAPIC (id[0x04] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 4, version 32, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] ACPI: HPET id: 0x8086a201 base: 0xfed00000
[    0.000000] SMP: Allowing 4 CPUs, 2 hotplug CPUs
[    0.000000] nr_irqs_gsi: 24
[    0.000000] PM: Registered nosave memory: 0000000000001000 - 0000000000006000
[    0.000000] PM: Registered nosave memory: 000000000009e000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e0000
[    0.000000] PM: Registered nosave memory: 00000000000e0000 - 0000000000100000
[    0.000000] PM: Registered nosave memory: 00000000bca99000 - 00000000bca9c000
[    0.000000] PM: Registered nosave memory: 00000000bdea8000 - 00000000bdebf000
[    0.000000] PM: Registered nosave memory: 00000000bdf86000 - 00000000bdfbf000
[    0.000000] PM: Registered nosave memory: 00000000bdfe0000 - 00000000bdff6000
[    0.000000] PM: Registered nosave memory: 00000000be000000 - 00000000c0000000
[    0.000000] PM: Registered nosave memory: 00000000c0000000 - 00000000f8000000
[    0.000000] PM: Registered nosave memory: 00000000f8000000 - 00000000fc000000
[    0.000000] PM: Registered nosave memory: 00000000fc000000 - 00000000fec00000
[    0.000000] PM: Registered nosave memory: 00000000fec00000 - 00000000fec01000
[    0.000000] PM: Registered nosave memory: 00000000fec01000 - 00000000fed10000
[    0.000000] PM: Registered nosave memory: 00000000fed10000 - 00000000fed14000
[    0.000000] PM: Registered nosave memory: 00000000fed14000 - 00000000fed18000
[    0.000000] PM: Registered nosave memory: 00000000fed18000 - 00000000fed1a000
[    0.000000] PM: Registered nosave memory: 00000000fed1a000 - 00000000fed1c000
[    0.000000] PM: Registered nosave memory: 00000000fed1c000 - 00000000fed20000
[    0.000000] PM: Registered nosave memory: 00000000fed20000 - 00000000fee00000
[    0.000000] PM: Registered nosave memory: 00000000fee00000 - 00000000fee01000
[    0.000000] PM: Registered nosave memory: 00000000fee01000 - 00000000fff00000
[    0.000000] PM: Registered nosave memory: 00000000fff00000 - 0000000100000000
[    0.000000] Allocating PCI resources starting at c0000000 (gap: c0000000:38000000)
[    0.000000] Booting paravirtualized kernel on bare hardware
[    0.000000] NR_CPUS:64 nr_cpumask_bits:64 nr_cpu_ids:4 nr_node_ids:1
[    0.000000] PERCPU: Embedded 30 pages/cpu @ffff880028200000 s91544 r8192 d23144 u524288
[    0.000000] pcpu-alloc: s91544 r8192 d23144 u524288 alloc=1*2097152
[    0.000000] pcpu-alloc: [0] 0 1 2 3 
[    0.000000] Built 1 zonelists in Node order, mobility grouping on.  Total pages: 1022152
[    0.000000] Policy zone: Normal
[    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.32-24-generic root=UUID=2846023d-9f02-4faa-a800-861f102d748e ro splash quiet splash nomodeset video=uvesafb:mode_option=1280x800-24,mtrr=3,scroll=ywrap
[    0.000000] PID hash table entries: 4096 (order: 3, 32768 bytes)
[    0.000000] Initializing CPU#0
[    0.000000] Checking aperture...
[    0.000000] No AGP bridge found
[    0.000000] Calgary: detecting Calgary via BIOS EBDA area
[    0.000000] Calgary: Unable to locate Rio Grande table in EBDA - bailing!
[    0.000000] PCI-DMA: Using software bounce buffering for IO (SWIOTLB)
[    0.000000] Placing 64MB software IO TLB between ffff880020000000 - ffff880024000000
[    0.000000] software IO TLB at phys 0x20000000 - 0x24000000
[    0.000000] Memory: 4011152k/5242880k available (5422k kernel code, 1082176k absent, 149552k reserved, 2979k data, 880k init)
[    0.000000] SLUB: Genslabs=14, HWalign=64, Order=0-3, MinObjects=0, CPUs=4, Nodes=1
[    0.000000] Hierarchical RCU implementation.
[    0.000000] NR_IRQS:4352 nr_irqs:440
[    0.000000] Console: colour dummy device 80x25
[    0.000000] console [tty0] enabled
[    0.000000] allocated 41943040 bytes of page_cgroup
[    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
[    0.000000] hpet clockevent registered
[    0.000000] HPET: 4 timers in total, 0 timers will be used for per-cpu timer
[    0.000000] Fast TSC calibration using PIT
[    0.000000] Detected 2394.465 MHz processor.
[    0.010007] Calibrating delay loop (skipped), value calculated using timer frequency.. 4788.93 BogoMIPS (lpj=23944650)
[    0.010033] Security Framework initialized
[    0.010052] AppArmor: AppArmor initialized
[    0.010381] Dentry cache hash table entries: 524288 (order: 10, 4194304 bytes)
[    0.012354] Inode-cache hash table entries: 262144 (order: 9, 2097152 bytes)
[    0.013299] Mount-cache hash table entries: 256
[    0.013444] Initializing cgroup subsys ns
[    0.013450] Initializing cgroup subsys cpuacct
[    0.013453] Initializing cgroup subsys memory
[    0.013460] Initializing cgroup subsys devices
[    0.013462] Initializing cgroup subsys freezer
[    0.013464] Initializing cgroup subsys net_cls
[    0.013484] CPU: L1 I cache: 32K, L1 D cache: 32K
[    0.013486] CPU: L2 cache: 3072K
[    0.013489] CPU 0/0x0 -> Node 0
[    0.013491] CPU: Physical Processor ID: 0
[    0.013492] CPU: Processor Core ID: 0
[    0.013495] mce: CPU supports 6 MCE banks
[    0.013503] CPU0: Thermal monitoring enabled (TM1)
[    0.013508] using mwait in idle threads.
[    0.013509] Performance Events: Core2 events, Intel PMU driver.
[    0.013515] ... version:                2
[    0.013516] ... bit width:              40
[    0.013517] ... generic registers:      2
[    0.013519] ... value mask:             000000ffffffffff
[    0.013520] ... max period:             000000007fffffff
[    0.013522] ... fixed-purpose events:   3
[    0.013523] ... event mask:             0000000700000003
[    0.015943] ACPI: Core revision 20090903
[    0.040010] ftrace: converting mcount calls to 0f 1f 44 00 00
[    0.040015] ftrace: allocating 22527 entries in 89 pages
[    0.050051] Setting APIC routing to flat
[    0.050362] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.156767] CPU0: Intel(R) Core(TM)2 Duo CPU     P8600  @ 2.40GHz stepping 06
[    0.160000] Booting processor 1 APIC 0x1 ip 0x6000
[    0.020000] Initializing CPU#1
[    0.020000] CPU: L1 I cache: 32K, L1 D cache: 32K
[    0.020000] CPU: L2 cache: 3072K
[    0.020000] CPU 1/0x1 -> Node 0
[    0.020000] CPU: Physical Processor ID: 0
[    0.020000] CPU: Processor Core ID: 1
[    0.020000] CPU1: Thermal monitoring enabled (TM1)
[    0.310065] CPU1: Intel(R) Core(TM)2 Duo CPU     P8600  @ 2.40GHz stepping 06
[    0.310071] checking TSC synchronization [CPU#0 -> CPU#1]: passed.
[    0.320016] Brought up 2 CPUs
[    0.320018] Total of 2 processors activated (9577.45 BogoMIPS).
[    0.320571] CPU0 attaching sched-domain:
[    0.320574]  domain 0: span 0-1 level MC
[    0.320576]   groups: 0 1
[    0.320581] CPU1 attaching sched-domain:
[    0.320583]  domain 0: span 0-1 level MC
[    0.320585]   groups: 1 0
[    0.320670] devtmpfs: initialized
[    0.320670] regulator: core version 0.5
[    0.320670] Time: 15:22:58  Date: 08/19/10
[    0.320670] NET: Registered protocol family 16
[    0.320670] Trying to unpack rootfs image as initramfs...
[    0.320670] ACPI: bus type pci registered
[    0.320670] PCI: MCFG configuration 0: base f8000000 segment 0 buses 0 - 63
[    0.320670] PCI: MCFG area at f8000000 reserved in E820
[    0.322659] PCI: Using MMCONFIG at f8000000 - fbffffff
[    0.322661] PCI: Using configuration type 1 for base access
[    0.323371] bio: create slab <bio-0> at 0
[    0.324534] ACPI: EC: Look up EC in DSDT
[    0.326617] ACPI: Executed 1 blocks of module-level executable AML code
[    0.328050] ACPI: BIOS _OSI(Linux) query ignored
[    0.431727] ACPI: Interpreter enabled
[    0.431727] ACPI: (supports S0 S3 S4 S5)
[    0.431727] ACPI: Using IOAPIC for interrupt routing
[    0.442037] ACPI: EC: GPE = 0x17, I/O: command/status = 0x66, data = 0x62
[    0.442385] ACPI: No dock devices found.
[    0.442983] ACPI: PCI Root Bridge [PCI0] (0000:00)
[    0.443088] pci 0000:00:01.0: PME# supported from D0 D3hot D3cold
[    0.443091] pci 0000:00:01.0: PME# disabled
[    0.443175] pci 0000:00:1a.0: reg 20 io port: [0xa0e0-0xa0ff]
[    0.443257] pci 0000:00:1a.1: reg 20 io port: [0xa0c0-0xa0df]
[    0.443345] pci 0000:00:1a.7: reg 10 32bit mmio: [0xdf305c00-0xdf305fff]
[    0.443409] pci 0000:00:1a.7: PME# supported from D0 D3hot D3cold
[    0.443413] pci 0000:00:1a.7: PME# disabled
[    0.443462] pci 0000:00:1b.0: reg 10 64bit mmio: [0xdf300000-0xdf303fff]
[    0.443511] pci 0000:00:1b.0: PME# supported from D0 D3hot D3cold
[    0.443515] pci 0000:00:1b.0: PME# disabled
[    0.443590] pci 0000:00:1c.0: PME# supported from D0 D3hot D3cold
[    0.443594] pci 0000:00:1c.0: PME# disabled
[    0.443674] pci 0000:00:1c.1: PME# supported from D0 D3hot D3cold
[    0.443678] pci 0000:00:1c.1: PME# disabled
[    0.443755] pci 0000:00:1c.2: PME# supported from D0 D3hot D3cold
[    0.443759] pci 0000:00:1c.2: PME# disabled
[    0.443835] pci 0000:00:1c.3: PME# supported from D0 D3hot D3cold
[    0.443839] pci 0000:00:1c.3: PME# disabled
[    0.443917] pci 0000:00:1c.4: PME# supported from D0 D3hot D3cold
[    0.443921] pci 0000:00:1c.4: PME# disabled
[    0.443997] pci 0000:00:1c.5: PME# supported from D0 D3hot D3cold
[    0.444001] pci 0000:00:1c.5: PME# disabled
[    0.444066] pci 0000:00:1d.0: reg 20 io port: [0xa0a0-0xa0bf]
[    0.444149] pci 0000:00:1d.1: reg 20 io port: [0xa080-0xa09f]
[    0.444230] pci 0000:00:1d.2: reg 20 io port: [0xa060-0xa07f]
[    0.444314] pci 0000:00:1d.3: reg 20 io port: [0xa040-0xa05f]
[    0.444398] pci 0000:00:1d.7: reg 10 32bit mmio: [0xdf305800-0xdf305bff]
[    0.444463] pci 0000:00:1d.7: PME# supported from D0 D3hot D3cold
[    0.444467] pci 0000:00:1d.7: PME# disabled
[    0.444680] pci 0000:00:1f.2: reg 10 io port: [0xa108-0xa10f]
[    0.444687] pci 0000:00:1f.2: reg 14 io port: [0xa114-0xa117]
[    0.444693] pci 0000:00:1f.2: reg 18 io port: [0xa100-0xa107]
[    0.444700] pci 0000:00:1f.2: reg 1c io port: [0xa110-0xa113]
[    0.444706] pci 0000:00:1f.2: reg 20 io port: [0xa020-0xa03f]
[    0.444713] pci 0000:00:1f.2: reg 24 32bit mmio: [0xdf305000-0xdf3057ff]
[    0.444751] pci 0000:00:1f.2: PME# supported from D3hot
[    0.444755] pci 0000:00:1f.2: PME# disabled
[    0.444789] pci 0000:00:1f.3: reg 10 64bit mmio: [0xdf306000-0xdf3060ff]
[    0.444804] pci 0000:00:1f.3: reg 20 io port: [0xa000-0xa01f]
[    0.444864] pci 0000:00:1f.6: reg 10 64bit mmio: [0xdf304000-0xdf304fff]
[    0.445001] pci 0000:01:00.0: reg 10 32bit mmio: [0xd2000000-0xd2ffffff]
[    0.445021] pci 0000:01:00.0: reg 14 64bit mmio pref: [0xc0000000-0xcfffffff]
[    0.445041] pci 0000:01:00.0: reg 1c 64bit mmio: [0xd0000000-0xd1ffffff]
[    0.445055] pci 0000:01:00.0: reg 24 io port: [0x9000-0x907f]
[    0.445069] pci 0000:01:00.0: reg 30 32bit mmio pref: [0xfff80000-0xffffffff]
[    0.445206] pci 0000:00:01.0: bridge io port: [0x9000-0x9fff]
[    0.445208] pci 0000:00:01.0: bridge 32bit mmio: [0xd0000000-0xd2ffffff]
[    0.445212] pci 0000:00:01.0: bridge 64bit mmio pref: [0xc0000000-0xcfffffff]
[    0.445293] pci 0000:02:00.0: reg 10 64bit mmio: [0xde200000-0xde201fff]
[    0.445395] pci 0000:02:00.0: PME# supported from D0 D3hot D3cold
[    0.445401] pci 0000:02:00.0: PME# disabled
[    0.445469] pci 0000:00:1c.0: bridge io port: [0x8000-0x8fff]
[    0.445473] pci 0000:00:1c.0: bridge 32bit mmio: [0xde200000-0xdf2fffff]
[    0.445479] pci 0000:00:1c.0: bridge 64bit mmio pref: [0xd3000000-0xd3ffffff]
[    0.445531] pci 0000:03:00.0: reg 10 io port: [0x6000-0x60ff]
[    0.445553] pci 0000:03:00.0: reg 18 64bit mmio pref: [0xd4010000-0xd4010fff]
[    0.445569] pci 0000:03:00.0: reg 20 64bit mmio pref: [0xd4000000-0xd400ffff]
[    0.445578] pci 0000:03:00.0: reg 30 32bit mmio pref: [0xffff0000-0xffffffff]
[    0.445622] pci 0000:03:00.0: supports D1 D2
[    0.445624] pci 0000:03:00.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.445629] pci 0000:03:00.0: PME# disabled
[    0.445696] pci 0000:00:1c.1: bridge io port: [0x6000-0x7fff]
[    0.445700] pci 0000:00:1c.1: bridge 32bit mmio: [0xdd200000-0xde1fffff]
[    0.445707] pci 0000:00:1c.1: bridge 64bit mmio pref: [0xd4000000-0xd50fffff]
[    0.445754] pci 0000:00:1c.2: bridge io port: [0x5000-0x5fff]
[    0.445758] pci 0000:00:1c.2: bridge 32bit mmio: [0xdc200000-0xdd1fffff]
[    0.445764] pci 0000:00:1c.2: bridge 64bit mmio pref: [0xd5100000-0xd60fffff]
[    0.445811] pci 0000:00:1c.3: bridge io port: [0x4000-0x4fff]
[    0.445815] pci 0000:00:1c.3: bridge 32bit mmio: [0xdb200000-0xdc1fffff]
[    0.445821] pci 0000:00:1c.3: bridge 64bit mmio pref: [0xd6100000-0xd70fffff]
[    0.445877] pci 0000:06:00.0: reg 10 32bit mmio: [0xda100000-0xda1007ff]
[    0.445889] pci 0000:06:00.0: reg 14 32bit mmio: [0xda100d00-0xda100d7f]
[    0.445919] pci 0000:06:00.0: reg 20 32bit mmio: [0xda100c80-0xda100cff]
[    0.445931] pci 0000:06:00.0: reg 24 32bit mmio: [0xda100c00-0xda100c7f]
[    0.446047] pci 0000:06:00.1: reg 10 32bit mmio: [0xda100b00-0xda100bff]
[    0.446194] pci 0000:06:00.2: reg 10 32bit mmio: [0xda100a00-0xda100aff]
[    0.446340] pci 0000:06:00.3: reg 10 32bit mmio: [0xda100900-0xda1009ff]
[    0.446486] pci 0000:06:00.4: reg 10 32bit mmio: [0xda100800-0xda1008ff]
[    0.446634] pci 0000:00:1c.4: bridge io port: [0x3000-0x3fff]
[    0.446638] pci 0000:00:1c.4: bridge 32bit mmio: [0xda100000-0xdb1fffff]
[    0.446645] pci 0000:00:1c.4: bridge 64bit mmio pref: [0xd7100000-0xd80fffff]
[    0.446691] pci 0000:00:1c.5: bridge io port: [0x2000-0x2fff]
[    0.446695] pci 0000:00:1c.5: bridge 32bit mmio: [0xd9100000-0xda0fffff]
[    0.446702] pci 0000:00:1c.5: bridge 64bit mmio pref: [0xd8100000-0xd90fffff]
[    0.446756] pci 0000:00:1e.0: transparent bridge
[    0.446811] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.447055] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PEGP._PRT]
[    0.447142] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P32_._PRT]
[    0.447286] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.EXP1._PRT]
[    0.447372] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.EXP2._PRT]
[    0.447467] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.EXP3._PRT]
[    0.447557] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.EXP4._PRT]
[    0.447642] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.EXP5._PRT]
[    0.447777] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.EXP6._PRT]
[    0.454329] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 7 9 10 *11 12)
[    0.454463] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 7 9 10 *11 12)
[    0.454595] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 7 9 10 *11 12)
[    0.454724] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 7 9 10 *11 12)
[    0.454853] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 7 9 10 *11 12)
[    0.454984] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 7 9 *10 11 12)
[    0.455114] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 7 9 10 *11 12)
[    0.455243] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 7 9 10 11 12) *0, disabled.
[    0.455386] vgaarb: device added: PCI:0000:01:00.0,decodes=io+mem,owns=io+mem,locks=none
[    0.455391] vgaarb: loaded
[    0.455502] SCSI subsystem initialized
[    0.455594] libata version 3.00 loaded.
[    0.455653] usbcore: registered new interface driver usbfs
[    0.455663] usbcore: registered new interface driver hub
[    0.455692] usbcore: registered new device driver usb
[    0.455841] ACPI: WMI: Mapper loaded
[    0.455843] PCI: Using ACPI for IRQ routing
[    0.456070] NetLabel: Initializing
[    0.456072] NetLabel:  domain hash size = 128
[    0.456073] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.456086] NetLabel:  unlabeled traffic allowed by default
[    0.456117] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0, 0
[    0.456122] hpet0: 4 comparators, 64-bit 14.318180 MHz counter
[    0.460030] Switching to clocksource tsc
[    0.461602] AppArmor: AppArmor Filesystem Enabled
[    0.461616] pnp: PnP ACPI init
[    0.461630] ACPI: bus type pnp registered
[    0.464085]   alloc irq_desc for 23 on node 0
[    0.464087]   alloc kstat_irqs on node 0
[    0.464423] pnp: PnP ACPI: found 12 devices
[    0.464425] ACPI: ACPI bus type pnp unregistered
[    0.464436] system 00:00: iomem range 0xf8000000-0xfbffffff has been reserved
[    0.464442] system 00:02: ioport range 0x164e-0x164f has been reserved
[    0.464445] system 00:02: ioport range 0x600-0x60f has been reserved
[    0.464447] system 00:02: ioport range 0x610-0x610 has been reserved
[    0.464449] system 00:02: ioport range 0x800-0x80f has been reserved
[    0.464451] system 00:02: ioport range 0x810-0x817 has been reserved
[    0.464454] system 00:02: ioport range 0x820-0x823 has been reserved
[    0.464456] system 00:02: ioport range 0x400-0x47f has been reserved
[    0.464458] system 00:02: ioport range 0x500-0x53f has been reserved
[    0.464460] system 00:02: ioport range 0x380-0x387 has been reserved
[    0.464463] system 00:02: iomem range 0xf8000000-0xfbffffff has been reserved
[    0.464466] system 00:02: iomem range 0xfed1c000-0xfed1ffff has been reserved
[    0.464468] system 00:02: iomem range 0xfed10000-0xfed13fff has been reserved
[    0.464471] system 00:02: iomem range 0xfed18000-0xfed18fff has been reserved
[    0.464477] system 00:02: iomem range 0xfed19000-0xfed19fff has been reserved
[    0.464479] system 00:02: iomem range 0xfec00000-0xfec00fff could not be reserved
[    0.464482] system 00:02: iomem range 0xfed20000-0xfed3ffff has been reserved
[    0.464485] system 00:02: iomem range 0xfed40000-0xfed44fff has been reserved
[    0.464487] system 00:02: iomem range 0xfed45000-0xfed8ffff has been reserved
[    0.464490] system 00:02: iomem range 0xfee00000-0xfee00fff has been reserved
[    0.469177] pci 0000:01:00.0: BAR 6: no parent found for of device [0xfff80000-0xffffffff]
[    0.469182] pci 0000:03:00.0: BAR 6: no parent found for of device [0xffff0000-0xffffffff]
[    0.469251] pci 0000:01:00.0: BAR 6: can't allocate mem resource [0xd0000000-0xcfffffff]
[    0.469253] pci 0000:00:01.0: PCI bridge, secondary bus 0000:01
[    0.469256] pci 0000:00:01.0:   IO window: 0x9000-0x9fff
[    0.469259] pci 0000:00:01.0:   MEM window: 0xd0000000-0xd2ffffff
[    0.469262] pci 0000:00:01.0:   PREFETCH window: 0x000000c0000000-0x000000cfffffff
[    0.469267] pci 0000:00:1c.0: PCI bridge, secondary bus 0000:02
[    0.469270] pci 0000:00:1c.0:   IO window: 0x8000-0x8fff
[    0.469275] pci 0000:00:1c.0:   MEM window: 0xde200000-0xdf2fffff
[    0.469279] pci 0000:00:1c.0:   PREFETCH window: 0x000000d3000000-0x000000d3ffffff
[    0.469287] pci 0000:00:1c.1: PCI bridge, secondary bus 0000:03
[    0.469290] pci 0000:00:1c.1:   IO window: 0x6000-0x7fff
[    0.469295] pci 0000:00:1c.1:   MEM window: 0xdd200000-0xde1fffff
[    0.469299] pci 0000:00:1c.1:   PREFETCH window: 0x000000d4000000-0x000000d50fffff
[    0.469305] pci 0000:00:1c.2: PCI bridge, secondary bus 0000:04
[    0.469308] pci 0000:00:1c.2:   IO window: 0x5000-0x5fff
[    0.469313] pci 0000:00:1c.2:   MEM window: 0xdc200000-0xdd1fffff
[    0.469317] pci 0000:00:1c.2:   PREFETCH window: 0x000000d5100000-0x000000d60fffff
[    0.469323] pci 0000:00:1c.3: PCI bridge, secondary bus 0000:05
[    0.469326] pci 0000:00:1c.3:   IO window: 0x4000-0x4fff
[    0.469331] pci 0000:00:1c.3:   MEM window: 0xdb200000-0xdc1fffff
[    0.469335] pci 0000:00:1c.3:   PREFETCH window: 0x000000d6100000-0x000000d70fffff
[    0.469343] pci 0000:00:1c.4: PCI bridge, secondary bus 0000:06
[    0.469346] pci 0000:00:1c.4:   IO window: 0x3000-0x3fff
[    0.469351] pci 0000:00:1c.4:   MEM window: 0xda100000-0xdb1fffff
[    0.469355] pci 0000:00:1c.4:   PREFETCH window: 0x000000d7100000-0x000000d80fffff
[    0.469361] pci 0000:00:1c.5: PCI bridge, secondary bus 0000:07
[    0.469364] pci 0000:00:1c.5:   IO window: 0x2000-0x2fff
[    0.469368] pci 0000:00:1c.5:   MEM window: 0xd9100000-0xda0fffff
[    0.469372] pci 0000:00:1c.5:   PREFETCH window: 0x000000d8100000-0x000000d90fffff
[    0.469379] pci 0000:00:1e.0: PCI bridge, secondary bus 0000:0a
[    0.469380] pci 0000:00:1e.0:   IO window: disabled
[    0.469385] pci 0000:00:1e.0:   MEM window: disabled
[    0.469388] pci 0000:00:1e.0:   PREFETCH window: disabled
[    0.469401]   alloc irq_desc for 16 on node -1
[    0.469402]   alloc kstat_irqs on node -1
[    0.469407] pci 0000:00:01.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.469411] pci 0000:00:01.0: setting latency timer to 64
[    0.469419]   alloc irq_desc for 17 on node -1
[    0.469420]   alloc kstat_irqs on node -1
[    0.469423] pci 0000:00:1c.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    0.469427] pci 0000:00:1c.0: setting latency timer to 64
[    0.469435] pci 0000:00:1c.1: PCI INT B -> GSI 16 (level, low) -> IRQ 16
[    0.469439] pci 0000:00:1c.1: setting latency timer to 64
[    0.469448] pci 0000:00:1c.2: enabling device (0000 -> 0003)
[    0.469450]   alloc irq_desc for 18 on node -1
[    0.469452]   alloc kstat_irqs on node -1
[    0.469454] pci 0000:00:1c.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    0.469460] pci 0000:00:1c.2: setting latency timer to 64
[    0.469467] pci 0000:00:1c.3: enabling device (0000 -> 0003)
[    0.469470]   alloc irq_desc for 19 on node -1
[    0.469472]   alloc kstat_irqs on node -1
[    0.469474] pci 0000:00:1c.3: PCI INT D -> GSI 19 (level, low) -> IRQ 19
[    0.469480] pci 0000:00:1c.3: setting latency timer to 64
[    0.469489] pci 0000:00:1c.4: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    0.469493] pci 0000:00:1c.4: setting latency timer to 64
[    0.469501] pci 0000:00:1c.5: PCI INT B -> GSI 16 (level, low) -> IRQ 16
[    0.469506] pci 0000:00:1c.5: setting latency timer to 64
[    0.469512] pci 0000:00:1e.0: setting latency timer to 64
[    0.469516] pci_bus 0000:00: resource 0 io:  [0x00-0xffff]
[    0.469518] pci_bus 0000:00: resource 1 mem: [0x000000-0xffffffffffffffff]
[    0.469520] pci_bus 0000:01: resource 0 io:  [0x9000-0x9fff]
[    0.469522] pci_bus 0000:01: resource 1 mem: [0xd0000000-0xd2ffffff]
[    0.469524] pci_bus 0000:01: resource 2 pref mem [0xc0000000-0xcfffffff]
[    0.469527] pci_bus 0000:02: resource 0 io:  [0x8000-0x8fff]
[    0.469528] pci_bus 0000:02: resource 1 mem: [0xde200000-0xdf2fffff]
[    0.469530] pci_bus 0000:02: resource 2 pref mem [0xd3000000-0xd3ffffff]
[    0.469533] pci_bus 0000:03: resource 0 io:  [0x6000-0x7fff]
[    0.469534] pci_bus 0000:03: resource 1 mem: [0xdd200000-0xde1fffff]
[    0.469536] pci_bus 0000:03: resource 2 pref mem [0xd4000000-0xd50fffff]
[    0.469538] pci_bus 0000:04: resource 0 io:  [0x5000-0x5fff]
[    0.469540] pci_bus 0000:04: resource 1 mem: [0xdc200000-0xdd1fffff]
[    0.469542] pci_bus 0000:04: resource 2 pref mem [0xd5100000-0xd60fffff]
[    0.469544] pci_bus 0000:05: resource 0 io:  [0x4000-0x4fff]
[    0.469546] pci_bus 0000:05: resource 1 mem: [0xdb200000-0xdc1fffff]
[    0.469548] pci_bus 0000:05: resource 2 pref mem [0xd6100000-0xd70fffff]
[    0.469550] pci_bus 0000:06: resource 0 io:  [0x3000-0x3fff]
[    0.469552] pci_bus 0000:06: resource 1 mem: [0xda100000-0xdb1fffff]
[    0.469554] pci_bus 0000:06: resource 2 pref mem [0xd7100000-0xd80fffff]
[    0.469556] pci_bus 0000:07: resource 0 io:  [0x2000-0x2fff]
[    0.469558] pci_bus 0000:07: resource 1 mem: [0xd9100000-0xda0fffff]
[    0.469560] pci_bus 0000:07: resource 2 pref mem [0xd8100000-0xd90fffff]
[    0.469562] pci_bus 0000:0a: resource 3 io:  [0x00-0xffff]
[    0.469564] pci_bus 0000:0a: resource 4 mem: [0x000000-0xffffffffffffffff]
[    0.469596] NET: Registered protocol family 2
[    0.469777] IP route cache hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.470939] TCP established hash table entries: 524288 (order: 11, 8388608 bytes)
[    0.474957] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
[    0.475482] TCP: Hash tables configured (established 524288 bind 65536)
[    0.475484] TCP reno registered
[    0.475614] NET: Registered protocol family 1
[    0.476025] pci 0000:01:00.0: Boot video device
[    0.476074] Simple Boot Flag value 0x5 read from CMOS RAM was invalid
[    0.476075] Simple Boot Flag at 0x44 set to 0x1
[    0.476252] Scanning for low memory corruption every 60 seconds
[    0.476400] audit: initializing netlink socket (disabled)
[    0.476413] type=2000 audit(1282231378.469:1): initialized
[    0.484862] HugeTLB registered 2 MB page size, pre-allocated 0 pages
[    0.486037] VFS: Disk quotas dquot_6.5.2
[    0.486084] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
[    0.486614] fuse init (API version 7.13)
[    0.486688] msgmni has been set to 7834
[    0.486862] alg: No test for stdrng (krng)
[    0.486909] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
[    0.486912] io scheduler noop registered
[    0.486914] io scheduler anticipatory registered
[    0.486915] io scheduler deadline registered
[    0.486943] io scheduler cfq registered (default)
[    0.487083]   alloc irq_desc for 24 on node -1
[    0.487085]   alloc kstat_irqs on node -1
[    0.487092] pcieport 0000:00:01.0: irq 24 for MSI/MSI-X
[    0.487098] pcieport 0000:00:01.0: setting latency timer to 64
[    0.487203]   alloc irq_desc for 25 on node -1
[    0.487205]   alloc kstat_irqs on node -1
[    0.487212] pcieport 0000:00:1c.0: irq 25 for MSI/MSI-X
[    0.487220] pcieport 0000:00:1c.0: setting latency timer to 64
[    0.487344]   alloc irq_desc for 26 on node -1
[    0.487345]   alloc kstat_irqs on node -1
[    0.487352] pcieport 0000:00:1c.1: irq 26 for MSI/MSI-X
[    0.487361] pcieport 0000:00:1c.1: setting latency timer to 64
[    0.487481]   alloc irq_desc for 27 on node -1
[    0.487483]   alloc kstat_irqs on node -1
[    0.487490] pcieport 0000:00:1c.2: irq 27 for MSI/MSI-X
[    0.487498] pcieport 0000:00:1c.2: setting latency timer to 64
[    0.487621]   alloc irq_desc for 28 on node -1
[    0.487623]   alloc kstat_irqs on node -1
[    0.487630] pcieport 0000:00:1c.3: irq 28 for MSI/MSI-X
[    0.487638] pcieport 0000:00:1c.3: setting latency timer to 64
[    0.487763]   alloc irq_desc for 29 on node -1
[    0.487764]   alloc kstat_irqs on node -1
[    0.487771] pcieport 0000:00:1c.4: irq 29 for MSI/MSI-X
[    0.487780] pcieport 0000:00:1c.4: setting latency timer to 64
[    0.487902]   alloc irq_desc for 30 on node -1
[    0.487904]   alloc kstat_irqs on node -1
[    0.487911] pcieport 0000:00:1c.5: irq 30 for MSI/MSI-X
[    0.487920] pcieport 0000:00:1c.5: setting latency timer to 64
[    0.488004] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.488026] Firmware did not grant requested _OSC control
[    0.488053] Firmware did not grant requested _OSC control
[    0.488075] Firmware did not grant requested _OSC control
[    0.488097] Firmware did not grant requested _OSC control
[    0.488118] Firmware did not grant requested _OSC control
[    0.488138] Firmware did not grant requested _OSC control
[    0.488159] Firmware did not grant requested _OSC control
[    0.488192] Firmware did not grant requested _OSC control
[    0.488214] Firmware did not grant requested _OSC control
[    0.488235] Firmware did not grant requested _OSC control
[    0.488256] Firmware did not grant requested _OSC control
[    0.488277] Firmware did not grant requested _OSC control
[    0.488297] Firmware did not grant requested _OSC control
[    0.488318] Firmware did not grant requested _OSC control
[    0.488338] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.489405] ACPI: AC Adapter [ACAD] (on-line)
[    0.489506] input: Power Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input0
[    0.489509] ACPI: Power Button [PWRB]
[    0.489544] input: Lid Switch as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0D:00/input/input1
[    0.489839] ACPI: Lid Switch [LID0]
[    0.489878] input: Sleep Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0E:00/input/input2
[    0.489881] ACPI: Sleep Button [SLPB]
[    0.489931] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input3
[    0.489933] ACPI: Power Button [PWRF]
[    0.490872] ACPI: SSDT 00000000bdeb4c18 00265 (v01  PmRef  Cpu0Ist 00003000 INTL 20051117)
[    0.491398] ACPI: SSDT 00000000bdeb2598 00537 (v01  PmRef  Cpu0Cst 00003001 INTL 20051117)
[    0.491840] Monitor-Mwait will be used to enter C-1 state
[    0.491862] Monitor-Mwait will be used to enter C-2 state
[    0.491867] Marking TSC unstable due to TSC halts in idle
[    0.491915] processor LNXCPU:00: registered as cooling_device0
[    0.492377] ACPI: SSDT 00000000bdeb3e18 001CF (v01  PmRef    ApIst 00003000 INTL 20051117)
[    0.492808] ACPI: SSDT 00000000bdeb4f18 0008D (v01  PmRef    ApCst 00003000 INTL 20051117)
[    0.493174] Switching to clocksource hpet
[    0.493567] processor LNXCPU:01: registered as cooling_device1
[    0.499253] ACPI Exception: AE_OK, No or invalid critical threshold (20090903/thermal-386)
[    0.500595] Linux agpgart interface v0.103
[    0.500646] efifb: probing for efifb
[    0.500795] efifb: framebuffer at 0xd1000000, mapped to 0xffffc90005100000, using 4032k, total 4032k
[    0.500798] efifb: mode is 1280x800x32, linelength=5120, pages=1
[    0.500799] efifb: scrolling: redraw
[    0.500802] efifb: Truecolor: size=8:8:8:8, shift=24:16:8:0
[    0.500832] fb0: EFI VGA frame buffer device
[    0.500837] Serial: 8250/16550 driver, 4 ports, IRQ sharing enabled
[    0.501971] brd: module loaded
[    0.502374] loop: module loaded
[    0.502448] input: Macintosh mouse button emulation as /devices/virtual/input/input4
[    0.502792] Fixed MDIO Bus: probed
[    0.502818] PPP generic driver version 2.4.2
[    0.502854] tun: Universal TUN/TAP device driver, 1.6
[    0.502856] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    0.502926] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    0.502948] ehci_hcd 0000:00:1a.7: PCI INT D -> GSI 19 (level, low) -> IRQ 19
[    0.502962] ehci_hcd 0000:00:1a.7: setting latency timer to 64
[    0.502965] ehci_hcd 0000:00:1a.7: EHCI Host Controller
[    0.502992] ehci_hcd 0000:00:1a.7: new USB bus registered, assigned bus number 1
[    0.503025] ehci_hcd 0000:00:1a.7: debug port 1
[    0.506891] ehci_hcd 0000:00:1a.7: cache line size of 32 is not supported
[    0.506906] ehci_hcd 0000:00:1a.7: irq 19, io mem 0xdf305c00
[    0.540024] ehci_hcd 0000:00:1a.7: USB 2.0 started, EHCI 1.00
[    0.540148] usb usb1: configuration #1 chosen from 1 choice
[    0.540173] hub 1-0:1.0: USB hub found
[    0.540182] hub 1-0:1.0: 4 ports detected
[    0.540246]   alloc irq_desc for 20 on node -1
[    0.540248]   alloc kstat_irqs on node -1
[    0.540254] ehci_hcd 0000:00:1d.7: PCI INT A -> GSI 20 (level, low) -> IRQ 20
[    0.540283] ehci_hcd 0000:00:1d.7: setting latency timer to 64
[    0.540287] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[    0.540320] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 2
[    0.540347] ehci_hcd 0000:00:1d.7: debug port 1
[    0.544215] ehci_hcd 0000:00:1d.7: cache line size of 32 is not supported
[    0.544232] ehci_hcd 0000:00:1d.7: irq 20, io mem 0xdf305800
[    0.570023] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00
[    0.570138] usb usb2: configuration #1 chosen from 1 choice
[    0.570163] hub 2-0:1.0: USB hub found
[    0.570171] hub 2-0:1.0: 8 ports detected
[    0.570240] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    0.570258] uhci_hcd: USB Universal Host Controller Interface driver
[    0.570299] uhci_hcd 0000:00:1a.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.570308] uhci_hcd 0000:00:1a.0: setting latency timer to 64
[    0.570311] uhci_hcd 0000:00:1a.0: UHCI Host Controller
[    0.570343] uhci_hcd 0000:00:1a.0: new USB bus registered, assigned bus number 3
[    0.570379] uhci_hcd 0000:00:1a.0: irq 16, io base 0x0000a0e0
[    0.570453] usb usb3: configuration #1 chosen from 1 choice
[    0.570474] hub 3-0:1.0: USB hub found
[    0.570480] hub 3-0:1.0: 2 ports detected
[    0.570523]   alloc irq_desc for 21 on node -1
[    0.570525]   alloc kstat_irqs on node -1
[    0.570530] uhci_hcd 0000:00:1a.1: PCI INT B -> GSI 21 (level, low) -> IRQ 21
[    0.570536] uhci_hcd 0000:00:1a.1: setting latency timer to 64
[    0.570539] uhci_hcd 0000:00:1a.1: UHCI Host Controller
[    0.570564] uhci_hcd 0000:00:1a.1: new USB bus registered, assigned bus number 4
[    0.570593] uhci_hcd 0000:00:1a.1: irq 21, io base 0x0000a0c0
[    0.570669] usb usb4: configuration #1 chosen from 1 choice
[    0.570689] hub 4-0:1.0: USB hub found
[    0.570694] hub 4-0:1.0: 2 ports detected
[    0.570737] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 20 (level, low) -> IRQ 20
[    0.570743] uhci_hcd 0000:00:1d.0: setting latency timer to 64
[    0.570746] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[    0.570784] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 5
[    0.570807] uhci_hcd 0000:00:1d.0: irq 20, io base 0x0000a0a0
[    0.570887] usb usb5: configuration #1 chosen from 1 choice
[    0.570907] hub 5-0:1.0: USB hub found
[    0.570913] hub 5-0:1.0: 2 ports detected
[    0.570951] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    0.570956] uhci_hcd 0000:00:1d.1: setting latency timer to 64
[    0.570959] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[    0.570988] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 6
[    0.571012] uhci_hcd 0000:00:1d.1: irq 19, io base 0x0000a080
[    0.571081] usb usb6: configuration #1 chosen from 1 choice
[    0.571105] hub 6-0:1.0: USB hub found
[    0.571110] hub 6-0:1.0: 2 ports detected
[    0.571147] uhci_hcd 0000:00:1d.2: PCI INT D -> GSI 16 (level, low) -> IRQ 16
[    0.571152] uhci_hcd 0000:00:1d.2: setting latency timer to 64
[    0.571155] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[    0.571179] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 7
[    0.571202] uhci_hcd 0000:00:1d.2: irq 16, io base 0x0000a060
[    0.571277] usb usb7: configuration #1 chosen from 1 choice
[    0.571297] hub 7-0:1.0: USB hub found
[    0.571302] hub 7-0:1.0: 2 ports detected
[    0.571340] uhci_hcd 0000:00:1d.3: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    0.571346] uhci_hcd 0000:00:1d.3: setting latency timer to 64
[    0.571349] uhci_hcd 0000:00:1d.3: UHCI Host Controller
[    0.571374] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 8
[    0.571402] uhci_hcd 0000:00:1d.3: irq 18, io base 0x0000a040
[    0.571475] usb usb8: configuration #1 chosen from 1 choice
[    0.571495] hub 8-0:1.0: USB hub found
[    0.571503] hub 8-0:1.0: 2 ports detected
[    0.571587] PNP: PS/2 Controller [PNP0303:KBC,PNP0f13:MOUE] at 0x60,0x64 irq 1,12
[    0.587421] Freeing initrd memory: 15081k freed
[    0.593094] serio: i8042 KBD port at 0x60,0x64 irq 1
[    0.593127] serio: i8042 AUX port at 0x60,0x64 irq 12
[    0.593367] mice: PS/2 mouse device common for all mice
[    0.596104] rtc_cmos 00:04: RTC can wake from S4
[    0.596192] rtc_cmos 00:04: rtc core: registered rtc_cmos as rtc0
[    0.596220] rtc0: alarms up to one month, 242 bytes nvram, hpet irqs
[    0.596353] device-mapper: uevent: version 1.0.3
[    0.596459] device-mapper: ioctl: 4.15.0-ioctl (2009-04-01) initialised: dm-devel@redhat.com
[    0.596556] device-mapper: multipath: version 1.1.0 loaded
[    0.596559] device-mapper: multipath round-robin: version 1.0.0 loaded
[    0.596812] cpuidle: using governor ladder
[    0.596902] cpuidle: using governor menu
[    0.597254] TCP cubic registered
[    0.597348] NET: Registered protocol family 10
[    0.597723] lo: Disabled Privacy Extensions
[    0.597950] NET: Registered protocol family 17
[    0.598596] PM: Resume from disk failed.
[    0.598610] registered taskstats version 1
[    0.598681] ACPI: Battery Slot [BAT0] (battery present)
[    0.599484]   Magic number: 6:852:386
[    0.599492] usb usb4: hash matches
[    0.599518] thermal cooling_device1: hash matches
[    0.599522] pci_express 0000:00:1c.4:pcie01: hash matches
[    0.599627] rtc_cmos 00:04: setting system clock to 2010-08-19 15:22:59 UTC (1282231379)
[    0.599629] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    0.599631] EDD information not available.
[    0.603999] Freeing unused kernel memory: 880k freed
[    0.604300] Write protecting the kernel read-only data: 7696k
[    0.617876] udev: starting version 151
[    0.620937] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input5
[    0.700922] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
[    0.700946] r8169 0000:03:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    0.701004] r8169 0000:03:00.0: setting latency timer to 64
[    0.701049]   alloc irq_desc for 31 on node -1
[    0.701051]   alloc kstat_irqs on node -1
[    0.701065] r8169 0000:03:00.0: irq 31 for MSI/MSI-X
[    0.704140] Console: switching to colour frame buffer device 160x50
[    0.728758] ahci 0000:00:1f.2: version 3.0
[    0.728773] ahci 0000:00:1f.2: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    0.728840]   alloc irq_desc for 32 on node -1
[    0.728842]   alloc kstat_irqs on node -1
[    0.728851] ahci 0000:00:1f.2: irq 32 for MSI/MSI-X
[    0.728896] ahci: SSS flag set, parallel bus scan disabled
[    0.728955] ahci 0000:00:1f.2: AHCI 0001.0200 32 slots 4 ports 3 Gbps 0x33 impl SATA mode
[    0.728958] ahci 0000:00:1f.2: flags: 64bit ncq sntf stag pm led clo pmp pio slum part ccc ems sxs 
[    0.728962] ahci 0000:00:1f.2: setting latency timer to 64
[    0.733038] acpi device:07: registered as cooling_device2
[    0.733249] input: Video Bus as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/device:05/LNXVIDEO:01/input/input6
[    0.733321] ACPI: Video Device [VGA] (multi-head: yes  rom: no  post: no)
[    0.753662] eth0: RTL8168c/8111c at 0xffffc90000676000, 00:1e:68:b0:7a:57, XID 1c4000c0 IRQ 31
[    0.763617] ohci1394 0000:06:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.763625] ohci1394 0000:06:00.0: setting latency timer to 64
[    0.790498] scsi0 : ahci
[    0.790612] scsi1 : ahci
[    0.790663] scsi2 : ahci
[    0.790712] scsi3 : ahci
[    0.790759] scsi4 : ahci
[    0.790821] scsi5 : ahci
[    0.790992] ata1: SATA max UDMA/133 abar m2048@0xdf305000 port 0xdf305100 irq 32
[    0.790996] ata2: SATA max UDMA/133 abar m2048@0xdf305000 port 0xdf305180 irq 32
[    0.790997] ata3: DUMMY
[    0.790998] ata4: DUMMY
[    0.791001] ata5: SATA max UDMA/133 abar m2048@0xdf305000 port 0xdf305300 irq 32
[    0.791003] ata6: SATA max UDMA/133 abar m2048@0xdf305000 port 0xdf305380 irq 32
[    0.831081] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[16]  MMIO=[da100000-da1007ff]  Max Packet=[2048]  IR/IT contexts=[4/4]
[    0.860058] usb 1-4: new high speed USB device using ehci_hcd and address 2
[    1.000707] usb 1-4: configuration #1 chosen from 1 choice
[    1.000950] hub 1-4:1.0: USB hub found
[    1.001098] hub 1-4:1.0: 4 ports detected
[    1.120035] usb 2-4: new high speed USB device using ehci_hcd and address 2
[    1.310035] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    1.328220] usb 2-4: configuration #1 chosen from 1 choice
[    1.348138] ata1.00: ATA-8: WDC WD5000BEVT-00A0RT0, 01.01A01, max UDMA/133
[    1.348141] ata1.00: 976773168 sectors, multi 0: LBA48 NCQ (depth 31/32), AA
[    1.350632] ata1.00: configured for UDMA/133
[    1.370161] scsi 0:0:0:0: Direct-Access     ATA      WDC WD5000BEVT-0 01.0 PQ: 0 ANSI: 5
[    1.370299] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    1.370368] sd 0:0:0:0: [sda] 976773168 512-byte logical blocks: (500 GB/465 GiB)
[    1.370408] sd 0:0:0:0: [sda] Write Protect is off
[    1.370410] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    1.370430] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.370544]  sda: sda1 sda2 sda3 < sda5 sda6 >
[    1.418751] sd 0:0:0:0: [sda] Attached SCSI disk
[    1.530110] usb 1-4.1: new high speed USB device using ehci_hcd and address 3
[    1.644305] usb 1-4.1: configuration #1 chosen from 1 choice
[    1.649650] Initializing USB Mass Storage driver...
[    1.649762] scsi6 : SCSI emulation for USB Mass Storage devices
[    1.649842] usbcore: registered new interface driver usb-storage
[    1.649844] USB Mass Storage support registered.
[    1.649848] usb-storage: device found at 3
[    1.649849] usb-storage: waiting for device to settle before scanning
[    1.720219] usb 1-4.4: new high speed USB device using ehci_hcd and address 4
[    1.832809] usb 1-4.4: configuration #1 chosen from 1 choice
[    1.833016] hub 1-4.4:1.0: USB hub found
[    1.833092] hub 1-4.4:1.0: 4 ports detected
[    2.110012] usb 7-2: new full speed USB device using uhci_hcd and address 2
[    2.150296] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[00241b00a2c52001]
[    2.291336] usb 7-2: configuration #1 chosen from 1 choice
[    2.300030] ata2: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    2.314218] ata2.00: ATAPI: TSSTcorp CDDVDW TS-L633L, 0400, max UDMA/100
[    2.327612] ata2.00: configured for UDMA/100
[    2.342325] scsi 1:0:0:0: CD-ROM            TSSTcorp CDDVDW TS-L633L  0400 PQ: 0 ANSI: 5
[    2.350028] sr0: scsi3-mmc drive: 24x/24x writer dvd-ram cd/rw xa/form2 cdda tray
[    2.350031] Uniform CD-ROM driver Revision: 3.20
[    2.350156] sr 1:0:0:0: Attached scsi CD-ROM sr0
[    2.350206] sr 1:0:0:0: Attached scsi generic sg1 type 5
[    2.370101] usb 1-4.4.3: new high speed USB device using ehci_hcd and address 5
[    2.493182] usb 1-4.4.3: configuration #1 chosen from 1 choice
[    2.495802] scsi7 : SCSI emulation for USB Mass Storage devices
[    2.495926] usb-storage: device found at 5
[    2.495928] usb-storage: waiting for device to settle before scanning
[    2.570104] usb 1-4.4.4: new full speed USB device using ehci_hcd and address 6
[    2.683554] usb 1-4.4.4: configuration #1 chosen from 1 choice
[    2.692584] usbcore: registered new interface driver hiddev
[    2.694192] input: Logitech USB Receiver as /devices/pci0000:00/0000:00:1a.7/usb1/1-4/1-4.4/1-4.4.4/1-4.4.4:1.0/input/input7
[    2.694280] generic-usb 0003:046D:C525.0001: input,hidraw0: USB HID v1.11 Mouse [Logitech USB Receiver] on usb-0000:00:1a.7-4.4.4/input0
[    2.696550] input: Logitech USB Receiver as /devices/pci0000:00/0000:00:1a.7/usb1/1-4/1-4.4/1-4.4.4/1-4.4.4:1.1/input/input8
[    2.696723] generic-usb 0003:046D:C525.0002: input,hiddev96,hidraw1: USB HID v1.11 Device [Logitech USB Receiver] on usb-0000:00:1a.7-4.4.4/input1
[    2.696739] usbcore: registered new interface driver usbhid
[    2.696741] usbhid: v2.6:USB HID core driver
[    2.700029] ata5: SATA link down (SStatus 0 SControl 300)
[    3.070035] ata6: SATA link down (SStatus 0 SControl 300)
[    3.710384] uvesafb: NVIDIA Corporation, G96 Board - 05666490, Chip Rev   , OEM: NVIDIA, VBE v3.0
[    3.855769] uvesafb: VBIOS/hardware supports DDC2 transfers
[    4.084896] uvesafb: monitor limits: vf = 76 Hz, hf = 83 kHz, clk = 180 MHz
[    4.085231] uvesafb: scrolling: redraw
[    4.085234] uvesafb: cannot reserve video memory at 0xd1000000
[    4.085244] uvesafb: probe of uvesafb.0 failed with error -5
[    4.738996] EXT4-fs (sda5): mounted filesystem with ordered data mode
[    6.640270] usb-storage: device scan complete
[    6.640858] scsi 6:0:0:0: Direct-Access              Silicon-Power    PMAP PQ: 0 ANSI: 0 CCS
[    6.641225] sd 6:0:0:0: Attached scsi generic sg2 type 0
[    6.641844] sd 6:0:0:0: [sdb] 2014208 512-byte logical blocks: (1.03 GB/983 MiB)
[    6.642342] sd 6:0:0:0: [sdb] Write Protect is off
[    6.642344] sd 6:0:0:0: [sdb] Mode Sense: 23 00 00 00
[    6.642346] sd 6:0:0:0: [sdb] Assuming drive cache: write through
[    6.644470] sd 6:0:0:0: [sdb] Assuming drive cache: write through
[    6.644473]  sdb: sdb1
[    6.646971] sd 6:0:0:0: [sdb] Assuming drive cache: write through
[    6.646973] sd 6:0:0:0: [sdb] Attached SCSI removable disk
[    7.491391] usb-storage: device scan complete
[   17.618363] udev: starting version 151
[   17.702906] Adding 3668984k swap on /dev/sda6.  Priority:-1 extents:1 across:3668984k 
[   17.708542] lis3lv02d: hardware type HPDV5_I found.
[   17.736456] lis3lv02d: 1-byte sensor found
[   17.770202] lp: driver loaded but no devices found
[   17.880269] input: ST LIS3LV02DL Accelerometer as /devices/platform/lis3lv02d/input/input9
[   17.880357] Registered led device: hp::hddprotect
[   17.880375] lis3lv02d driver loaded.
[   17.907301] nvidia: module license 'NVIDIA' taints kernel.
[   17.907304] Disabling lock debugging due to kernel taint
[   17.934658] type=1505 audit(1282209796.831:2):  operation="profile_load" pid=822 name="/sbin/dhclient3"
[   17.935213] type=1505 audit(1282209796.831:3):  operation="profile_load" pid=822 name="/usr/lib/NetworkManager/nm-dhcp-client.action"
[   17.935511] type=1505 audit(1282209796.831:4):  operation="profile_load" pid=822 name="/usr/lib/connman/scripts/dhclient-script"
[   18.279854] lirc_dev: IR Remote Control driver registered, major 61 
[   18.280374] lirc_dev: lirc_register_driver: sample_rate: 0
[   18.280472] enecir: KB3926C detected, driver support is not complete!
[   18.280474] enecir: chip is 0x3926 - 0x00, 0xc0
[   18.280480] enecir: hardware features:
[   18.280482] enecir: learning and tx off, gpio40_learn off, fan_in off
[   18.280483] enecir: driver has been succesfully loaded
[   18.284217] sdhci: Secure Digital Host Controller Interface driver
[   18.284220] sdhci: Copyright(c) Pierre Ossman
[   18.285249] sdhci-pci 0000:06:00.1: SDHCI controller found [197b:2382] (rev 0)
[   18.285271] sdhci-pci 0000:06:00.1: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   18.285393] sdhci-pci 0000:06:00.1: setting latency timer to 64
[   18.285426] Registered led device: mmc0::
[   18.285458] mmc0: SDHCI controller on PCI [0000:06:00.1] using DMA
[   18.285469] sdhci-pci 0000:06:00.2: SDHCI controller found [197b:2381] (rev 0)
[   18.285485] sdhci-pci 0000:06:00.2: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   18.285491] sdhci-pci 0000:06:00.2: Refusing to bind to secondary interface.
[   18.285497] sdhci-pci 0000:06:00.2: PCI INT A disabled
[   18.299947] Bluetooth: Core ver 2.15
[   18.300234] cfg80211: Calling CRDA to update world regulatory domain
[   18.300849] NET: Registered protocol family 31
[   18.300851] Bluetooth: HCI device and connection manager initialized
[   18.300853] Bluetooth: HCI socket layer initialized
[   18.302109] Bluetooth: Generic Bluetooth USB driver ver 0.6
[   18.302201] usbcore: registered new interface driver btusb
[   18.305319] Linux video capture interface: v2.00
[   18.307653] uvcvideo: Found UVC 1.00 device HP Webcam (5986:0137)
[   18.311872] jmb38x_ms 0000:06:00.3: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   18.311879] jmb38x_ms 0000:06:00.3: setting latency timer to 64
[   18.322891] input: HP Webcam as /devices/pci0000:00/0000:00:1d.7/usb2/2-4/2-4:1.0/input/input10
[   18.322949] usbcore: registered new interface driver uvcvideo
[   18.322952] USB Video Class driver (v0.1.0)
[   18.377018] iwlagn: Intel(R) Wireless WiFi Link AGN driver for Linux, 1.3.27k
[   18.377021] iwlagn: Copyright(c) 2003-2009 Intel Corporation
[   18.377085] iwlagn 0000:02:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   18.377092] iwlagn 0000:02:00.0: setting latency timer to 64
[   18.377137] iwlagn 0000:02:00.0: Detected Intel Wireless WiFi Link 5100ABG REV=0x54
[   18.443420] iwlagn 0000:02:00.0: Tunable channels: 13 802.11bg, 24 802.11a channels
[   18.443476]   alloc irq_desc for 33 on node -1
[   18.443478]   alloc kstat_irqs on node -1
[   18.443495] iwlagn 0000:02:00.0: irq 33 for MSI/MSI-X
[   18.480442]   alloc irq_desc for 22 on node -1
[   18.480445]   alloc kstat_irqs on node -1
[   18.480451] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[   18.480498] HDA Intel 0000:00:1b.0: setting latency timer to 64
[   18.485462] phy0: Selected rate control algorithm 'iwl-agn-rs'
[   18.524771] nvidia 0000:01:00.0: power state changed by ACPI to D0
[   18.524790] nvidia 0000:01:00.0: power state changed by ACPI to D0
[   18.524813] nvidia 0000:01:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   18.524834] nvidia 0000:01:00.0: setting latency timer to 64
[   18.524845] vgaarb: device changed decodes: PCI:0000:01:00.0,olddecodes=io+mem,decodes=none:owns=io+mem
[   18.525877] NVRM: loading NVIDIA UNIX x86_64 Kernel Module  256.44  Thu Jul 29 01:22:44 PDT 2010
[   18.580216] cfg80211: World regulatory domain updated:
[   18.580219] 	(start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   18.580221] 	(2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   18.580224] 	(2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   18.580226] 	(2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   18.580228] 	(5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   18.580230] 	(5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   18.694779] input: HDA Digital PCBeep as /devices/pci0000:00/0000:00:1b.0/input/input11
[   18.725847] type=1505 audit(1282209797.621:5):  operation="profile_load" pid=1022 name="/usr/share/gdm/guest-session/Xsession"
[   18.727131] type=1505 audit(1282209797.621:6):  operation="profile_replace" pid=1023 name="/sbin/dhclient3"
[   18.727703] type=1505 audit(1282209797.621:7):  operation="profile_replace" pid=1023 name="/usr/lib/NetworkManager/nm-dhcp-client.action"
[   18.728005] type=1505 audit(1282209797.621:8):  operation="profile_replace" pid=1023 name="/usr/lib/connman/scripts/dhclient-script"
[   18.731590] type=1505 audit(1282209797.631:9):  operation="profile_load" pid=1024 name="/usr/bin/evince"
[   18.731840] input: HDA Intel Mic at Ext Front Jack as /devices/pci0000:00/0000:00:1b.0/sound/card0/input12
[   18.732007] input: HDA Intel Mic at Sep UNKNOWN Jack as /devices/pci0000:00/0000:00:1b.0/sound/card0/input13
[   18.732143] input: HDA Intel HP Out at Ext Front Jack as /devices/pci0000:00/0000:00:1b.0/sound/card0/input14
[   18.745084] type=1505 audit(1282209797.641:10):  operation="profile_load" pid=1024 name="/usr/bin/evince-previewer"
[   18.749539] type=1505 audit(1282209797.641:11):  operation="profile_load" pid=1024 name="/usr/bin/evince-thumbnailer"
[   19.210361] iwlagn 0000:02:00.0: firmware: requesting iwlwifi-5000-2.ucode
[   19.292328] iwlagn 0000:02:00.0: loaded firmware version 8.24.2.12
[   19.369252] vboxdrv: Trying to deactivate the NMI watchdog permanently...
[   19.369255] vboxdrv: Warning: 2.6.31+ kernel detected. Most likely the hardware performance
[   19.369256] vboxdrv: counter framework which can generate NMIs is active. You have to prevent
[   19.369257] vboxdrv: the usage of hardware performance counters by
[   19.369258] vboxdrv:   echo 2 > /proc/sys/kernel/perf_counter_paranoid
[   19.369261] vboxdrv: Found 2 processor cores.
[   19.369589] VBoxDrv: dbg - g_abExecMemory=ffffffffa0e79ca0
[   19.369604] vboxdrv: fAsync=0 offMin=0x1b0 offMax=0x65d
[   19.369942] vboxdrv: TSC mode is 'synchronous', kernel timer mode is 'normal'.
[   19.369944] vboxdrv: Successfully loaded version 3.2.8 (interface 0x00140001).
[   19.424719] Registered led device: iwl-phy0::radio
[   19.424735] Registered led device: iwl-phy0::assoc
[   19.424748] Registered led device: iwl-phy0::RX
[   19.424763] Registered led device: iwl-phy0::TX
[   19.461884] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   19.491229] r8169: eth0: link down
[   19.491751] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   19.615498] Bluetooth: L2CAP ver 2.14
[   19.615501] Bluetooth: L2CAP socket layer initialized
[   19.619870] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   19.619873] Bluetooth: BNEP filters: protocol multicast
[   19.626162] Bridge firewalling registered
[   19.634907] Bluetooth: SCO (Voice Link) ver 0.6
[   19.634910] Bluetooth: SCO socket layer initialized
[   19.665999] ppdev: user-space parallel port driver
[   19.750576] Bluetooth: RFCOMM TTY layer initialized
[   19.750579] Bluetooth: RFCOMM socket layer initialized
[   19.750581] Bluetooth: RFCOMM ver 1.11
[   21.656681] CPU0 attaching NULL sched-domain.
[   21.656686] CPU1 attaching NULL sched-domain.
[   22.301420] CPU0 attaching sched-domain:
[   22.301423]  domain 0: span 0-1 level MC
[   22.301425]   groups: 0 1
[   22.301430] CPU1 attaching sched-domain:
[   22.301432]  domain 0: span 0-1 level MC
[   22.301434]   groups: 1 0
[   25.089685] CPU0 attaching NULL sched-domain.
[   25.089690] CPU1 attaching NULL sched-domain.
[   25.161376] CPU0 attaching sched-domain:
[   25.161379]  domain 0: span 0-1 level MC
[   25.161381]   groups: 0 1
[   25.161386] CPU1 attaching sched-domain:
[   25.161388]  domain 0: span 0-1 level MC
[   25.161390]   groups: 1 0
[   28.130108] usb 1-4.4.3: reset high speed USB device using ehci_hcd and address 5
[   28.273899] scsi 7:0:0:0: Direct-Access     HTC      Desire           0100 PQ: 0 ANSI: 2
[   28.274301] sd 7:0:0:0: Attached scsi generic sg3 type 0
[   28.279875] sd 7:0:0:0: [sdc] Attached SCSI removable disk
[   39.681471] usb 1-4.4.3: USB disconnect, address 5
[   40.227148] wlan0: deauthenticating from 00:23:54:dc:78:ce by local choice (reason=3)
[   40.227238] wlan0: direct probe to AP 00:23:54:dc:78:ce (try 1)
[   40.230323] wlan0: direct probe responded
[   40.230326] wlan0: authenticate with AP 00:23:54:dc:78:ce (try 1)
[   40.232037] wlan0: authenticated
[   40.232051] wlan0: associate with AP 00:23:54:dc:78:ce (try 1)
[   40.234874] wlan0: RX AssocResp from 00:23:54:dc:78:ce (capab=0x431 status=0 aid=1)
[   40.234876] wlan0: associated
[   40.236371] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   40.236432] cfg80211: Calling CRDA for country: GB
[   40.238205] cfg80211: Received country IE:
[   40.238208] cfg80211: Regulatory domain: GB
[   40.238210] 	(start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   40.238212] 	(2402000 KHz - 2494000 KHz @ 40000 KHz), (10000 mBi, 10000 mBm)
[   40.238214] cfg80211: CRDA thinks this should applied:
[   40.238215] cfg80211: Regulatory domain: GB
[   40.238216] 	(start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   40.238218] 	(2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A, 2000 mBm)
[   40.238220] 	(5170000 KHz - 5250000 KHz @ 40000 KHz), (N/A, 2000 mBm)
[   40.238222] 	(5250000 KHz - 5330000 KHz @ 40000 KHz), (N/A, 2000 mBm)
[   40.238224] 	(5490000 KHz - 5710000 KHz @ 40000 KHz), (N/A, 2700 mBm)
[   40.238226] cfg80211: We intersect both of these and get:
[   40.238227] cfg80211: Regulatory domain: 98
[   40.238228] 	(start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   40.238230] 	(2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A, 2000 mBm)
[   40.238234] cfg80211: Leaving channel 5180 MHz intact on phy0 - no rule found in band on Country IE
[   40.238237] cfg80211: Leaving channel 5200 MHz intact on phy0 - no rule found in band on Country IE
[   40.238239] cfg80211: Leaving channel 5220 MHz intact on phy0 - no rule found in band on Country IE
[   40.238241] cfg80211: Leaving channel 5240 MHz intact on phy0 - no rule found in band on Country IE
[   40.238243] cfg80211: Leaving channel 5260 MHz intact on phy0 - no rule found in band on Country IE
[   40.238245] cfg80211: Leaving channel 5280 MHz intact on phy0 - no rule found in band on Country IE
[   40.238247] cfg80211: Leaving channel 5300 MHz intact on phy0 - no rule found in band on Country IE
[   40.238249] cfg80211: Leaving channel 5320 MHz intact on phy0 - no rule found in band on Country IE
[   40.238251] cfg80211: Leaving channel 5500 MHz intact on phy0 - no rule found in band on Country IE
[   40.238253] cfg80211: Leaving channel 5520 MHz intact on phy0 - no rule found in band on Country IE
[   40.238255] cfg80211: Leaving channel 5540 MHz intact on phy0 - no rule found in band on Country IE
[   40.238257] cfg80211: Leaving channel 5560 MHz intact on phy0 - no rule found in band on Country IE
[   40.238259] cfg80211: Leaving channel 5580 MHz intact on phy0 - no rule found in band on Country IE
[   40.238261] cfg80211: Leaving channel 5600 MHz intact on phy0 - no rule found in band on Country IE
[   40.238263] cfg80211: Leaving channel 5620 MHz intact on phy0 - no rule found in band on Country IE
[   40.238265] cfg80211: Leaving channel 5640 MHz intact on phy0 - no rule found in band on Country IE
[   40.238267] cfg80211: Leaving channel 5660 MHz intact on phy0 - no rule found in band on Country IE
[   40.238269] cfg80211: Leaving channel 5680 MHz intact on phy0 - no rule found in band on Country IE
[   40.238271] cfg80211: Leaving channel 5700 MHz intact on phy0 - no rule found in band on Country IE
[   40.238273] cfg80211: Leaving channel 5745 MHz intact on phy0 - no rule found in band on Country IE
[   40.238275] cfg80211: Leaving channel 5765 MHz intact on phy0 - no rule found in band on Country IE
[   40.238278] cfg80211: Leaving channel 5785 MHz intact on phy0 - no rule found in band on Country IE
[   40.238280] cfg80211: Leaving channel 5805 MHz intact on phy0 - no rule found in band on Country IE
[   40.238282] cfg80211: Leaving channel 5825 MHz intact on phy0 - no rule found in band on Country IE
[   40.238284] cfg80211: Current regulatory domain updated by AP to: GB
[   40.238285] 	(start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   40.238287] 	(2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A, 2000 mBm)
[   40.249220] Intel AES-NI instructions are not detected.
[   40.262286] padlock: VIA PadLock not detected.
[   50.600023] wlan0: no IPv6 routers present
[ 7537.342673] __ratelimit: 9 callbacks suppressed
[ 7537.342677] operapluginwrap[4097]: segfault at 0 ip (null) sp 00007fffb091ef58 error 14 in operapluginwrapper-native[400000+31000]
[ 7537.358511] operapluginwrap[4113]: segfault at 0 ip (null) sp 00007fff02134078 error 14 in operapluginwrapper-native[400000+31000]
[ 7537.373244] operapluginwrap[4129]: segfault at 0 ip (null) sp 00007fff13cc0638 error 14 in operapluginwrapper-native[400000+31000]
[ 7537.402493] operapluginwrap[4161]: segfault at 0 ip (null) sp 00007fffa7515048 error 14 in operapluginwrapper-native[400000+31000]
[ 7537.418596] operapluginwrap[4177]: segfault at 0 ip (null) sp 00007ffffe6acb88 error 14 in operapluginwrapper-native[400000+31000]
[ 7537.435151] operapluginwrap[4193]: segfault at 0 ip (null) sp 00007fff275d3d48 error 14 in operapluginwrapper-native[400000+31000]
[ 7537.450425] operapluginwrap[4209]: segfault at 0 ip (null) sp 00007fff33213aa8 error 14 in operapluginwrapper-native[400000+31000]
[ 7537.467184] operapluginwrap[4226]: segfault at 0 ip (null) sp 00007fffabf7ce88 error 14 in operapluginwrapper-native[400000+31000]
[22633.460303] usb 1-4.4.3: new high speed USB device using ehci_hcd and address 7
[22633.583477] usb 1-4.4.3: configuration #1 chosen from 1 choice
[22633.585386] scsi8 : SCSI emulation for USB Mass Storage devices
[22633.585598] usb-storage: device found at 7
[22633.585604] usb-storage: waiting for device to settle before scanning
[22638.582858] usb-storage: device scan complete
[22638.584305] scsi 8:0:0:0: Direct-Access     HTC      Desire           0100 PQ: 0 ANSI: 2
[22638.585330] sd 8:0:0:0: Attached scsi generic sg3 type 0
[22638.601612] sd 8:0:0:0: [sdc] Attached SCSI removable disk
[26813.184992] wlan0: disassociated from 00:23:54:dc:78:ce (Reason: 8)
[26813.230338] wlan0: deauthenticating from 00:23:54:dc:78:ce by local choice (reason=3)
[26873.471137] wlan0: direct probe to AP 00:23:54:dc:78:ce (try 1)
[26873.473635] wlan0: direct probe responded
[26873.473639] wlan0: authenticate with AP 00:23:54:dc:78:ce (try 1)
[26873.475303] wlan0: authenticated
[26873.475321] wlan0: associate with AP 00:23:54:dc:78:ce (try 1)
[26873.478121] wlan0: RX AssocResp from 00:23:54:dc:78:ce (capab=0x431 status=0 aid=1)
[26873.478124] wlan0: associated
[28310.855949] process `skype' is using obsolete setsockopt SO_BSDCOMPAT
[33908.874119] wlan0: disassociated from 00:23:54:dc:78:ce (Reason: 8)
[33908.921354] wlan0: deauthenticating from 00:23:54:dc:78:ce by local choice (reason=3)
[33955.398879] CE: hpet increasing min_delta_ns to 15000 nsec
[33969.151190] wlan0: direct probe to AP 00:23:54:dc:78:ce (try 1)
[33969.153700] wlan0: direct probe responded
[33969.153710] wlan0: authenticate with AP 00:23:54:dc:78:ce (try 1)
[33969.155482] wlan0: authenticated
[33969.155526] wlan0: associate with AP 00:23:54:dc:78:ce (try 1)
[33969.158615] wlan0: RX AssocResp from 00:23:54:dc:78:ce (capab=0x431 status=0 aid=1)
[33969.158623] wlan0: associated
[39897.754437] usb 1-4.4.3: USB disconnect, address 7
[41117.081560] usb 1-4.4.3: new high speed USB device using ehci_hcd and address 8
[41117.210220] usb 1-4.4.3: configuration #1 chosen from 1 choice
[41117.227515] scsi9 : SCSI emulation for USB Mass Storage devices
[41117.227722] usb-storage: device found at 8
[41117.227724] usb-storage: waiting for device to settle before scanning
[41122.224609] usb-storage: device scan complete
[41122.226364] scsi 9:0:0:0: Direct-Access     HTC      Desire           0100 PQ: 0 ANSI: 2
[41122.228244] sd 9:0:0:0: Attached scsi generic sg3 type 0
[41122.239362] sd 9:0:0:0: [sdc] Attached SCSI removable disk
[49195.076806] npviewer.bin[2637]: segfault at 418 ip 00000000f601ddd6 sp 00000000ff9e9dc8 error 6 in libflashplayer.so[f5dcf000+b2c000]
[49373.083902] usb 1-4.4.3: USB disconnect, address 8
____________________________________________

Using built-in specs.
Target: x86_64-linux-gnu
Configured with: ../src/configure -v --with-pkgversion='Ubuntu 4.4.3-4ubuntu5' --with-bugurl=file:///usr/share/doc/gcc-4.4/README.Bugs --enable-languages=c,c++,fortran,objc,obj-c++ --prefix=/usr --enable-shared --enable-multiarch --enable-linker-build-id --with-system-zlib --libexecdir=/usr/lib --without-included-gettext --enable-threads=posix --with-gxx-include-dir=/usr/include/c++/4.4 --program-suffix=-4.4 --enable-nls --enable-clocale=gnu --enable-libstdcxx-debug --enable-plugin --enable-objc-gc --disable-werror --with-arch-32=i486 --with-tune=generic --enable-checking=release --build=x86_64-linux-gnu --host=x86_64-linux-gnu --target=x86_64-linux-gnu
Thread model: posix
gcc version 4.4.3 (Ubuntu 4.4.3-4ubuntu5) 
____________________________________________

Using built-in specs.
Target: x86_64-linux-gnu
Configured with: ../src/configure -v --with-pkgversion='Ubuntu 4.4.3-4ubuntu5' --with-bugurl=file:///usr/share/doc/gcc-4.4/README.Bugs --enable-languages=c,c++,fortran,objc,obj-c++ --prefix=/usr --enable-shared --enable-multiarch --enable-linker-build-id --with-system-zlib --libexecdir=/usr/lib --without-included-gettext --enable-threads=posix --with-gxx-include-dir=/usr/include/c++/4.4 --program-suffix=-4.4 --enable-nls --enable-clocale=gnu --enable-libstdcxx-debug --enable-plugin --enable-objc-gc --disable-werror --with-arch-32=i486 --with-tune=generic --enable-checking=release --build=x86_64-linux-gnu --host=x86_64-linux-gnu --target=x86_64-linux-gnu
Thread model: posix
gcc version 4.4.3 (Ubuntu 4.4.3-4ubuntu5) 
____________________________________________

xset -q:

Keyboard Control:
  auto repeat:  on    key click percent:  0    LED mask:  00000000
  XKB indicators:
    00: Caps Lock:   off    01: Num Lock:    off    02: Scroll Lock: off
    03: Compose:     off    04: Kana:        off    05: Sleep:       off
    06: Suspend:     off    07: Mute:        off    08: Misc:        off
    09: Mail:        off    10: Charging:    off    11: Shift Lock:  off
    12: Group 2:     off    13: Mouse Keys:  off
  auto repeat delay:  500    repeat rate:  30
  auto repeating keys:  00ffffffdffffbbf
                        fadfffefffedffff
                        9fffffffffffffff
                        fff7ffffffffffff
  bell percent:  50    bell pitch:  400    bell duration:  100
Pointer Control:
  acceleration:  2/1    threshold:  4
Screen Saver:
  prefer blanking:  yes    allow exposures:  yes
  timeout:  0    cycle:  0
Colors:
  default colormap:  0x20    BlackPixel:  0    WhitePixel:  16777215
Font Path:
  /usr/share/fonts/X11/misc,/usr/share/fonts/X11/100dpi/:unscaled,/usr/share/fonts/X11/75dpi/:unscaled,/usr/share/fonts/X11/Type1,/usr/share/fonts/X11/100dpi,/usr/share/fonts/X11/75dpi,/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,built-ins
DPMS (Energy Star):
  Standby: 0    Suspend: 0    Off: 0
  DPMS is Enabled
  Monitor is On
____________________________________________

nvidia-settings -q all:


Attributes queryable via notebook:0.0:

  Attribute 'OperatingSystem' (notebook:0.0): 0.
    The valid values for 'OperatingSystem' are in the range 0 - 2
    (inclusive).
    'OperatingSystem' is a read-only attribute.
    'OperatingSystem' can use the following target types: X Screen, GPU.

  Attribute 'NvidiaDriverVersion' (notebook:0.0): 256.44 
    'NvidiaDriverVersion' is a string attribute.
    'NvidiaDriverVersion' is a read-only attribute.
    'NvidiaDriverVersion' can use the following target types: X Screen,
    GPU.

  Attribute 'NvControlVersion' (notebook:0.0): 1.23 
    'NvControlVersion' is a string attribute.
    'NvControlVersion' is a read-only attribute.
    'NvControlVersion' can use the following target types: X Screen.

  Attribute 'GLXServerVersion' (notebook:0.0): 1.4 
    'GLXServerVersion' is a string attribute.
    'GLXServerVersion' is a read-only attribute.
    'GLXServerVersion' can use the following target types: X Screen.

  Attribute 'GLXClientVersion' (notebook:0.0): 1.4 
    'GLXClientVersion' is a string attribute.
    'GLXClientVersion' is a read-only attribute.
    'GLXClientVersion' can use the following target types: X Screen.

  Attribute 'OpenGLVersion' (notebook:0.0): 3.3.0 NVIDIA 256.44 
    'OpenGLVersion' is a string attribute.
    'OpenGLVersion' is a read-only attribute.
    'OpenGLVersion' can use the following target types: X Screen.

  Attribute 'XRandRVersion' (notebook:0.0): 1.3 
    'XRandRVersion' is a string attribute.
    'XRandRVersion' is a read-only attribute.
    'XRandRVersion' can use the following target types: X Screen.

  Attribute 'XF86VidModeVersion' (notebook:0.0): 2.2 
    'XF86VidModeVersion' is a string attribute.
    'XF86VidModeVersion' is a read-only attribute.
    'XF86VidModeVersion' can use the following target types: X Screen.

  Attribute 'XvVersion' (notebook:0.0): 2.2 
    'XvVersion' is a string attribute.
    'XvVersion' is a read-only attribute.
    'XvVersion' can use the following target types: X Screen.

  Attribute 'TwinView' (notebook:0.0): 1.
    'TwinView' is a boolean attribute; valid values are: 1 (on/true) and 0
    (off/false).
    'TwinView' is a read-only attribute.
    'TwinView' can use the following target types: X Screen.

  Attribute 'ConnectedDisplays' (notebook:0.0): 0x00010001.
    'ConnectedDisplays' is a bitmask attribute.
    'ConnectedDisplays' is a read-only attribute.
    'ConnectedDisplays' can use the following target types: X Screen, GPU.

  Attribute 'EnabledDisplays' (notebook:0.0): 0x00010001.
    'EnabledDisplays' is a bitmask attribute.
    'EnabledDisplays' is a read-only attribute.
    'EnabledDisplays' can use the following target types: X Screen, GPU.

  Attribute 'CursorShadow' (notebook:0.0): 0.
    'CursorShadow' is a boolean attribute; valid values are: 1 (on/true)
    and 0 (off/false).
    'CursorShadow' can use the following target types: X Screen.

  Attribute 'CursorShadowAlpha' (notebook:0.0): 64.
    The valid values for 'CursorShadowAlpha' are in the range 0 - 254
    (inclusive).
    'CursorShadowAlpha' can use the following target types: X Screen.

  Attribute 'CursorShadowRed' (notebook:0.0): 0.
    The valid values for 'CursorShadowRed' are in the range 0 - 255
    (inclusive).
    'CursorShadowRed' can use the following target types: X Screen.

  Attribute 'CursorShadowGreen' (notebook:0.0): 0.
    The valid values for 'CursorShadowGreen' are in the range 0 - 255
    (inclusive).
    'CursorShadowGreen' can use the following target types: X Screen.

  Attribute 'CursorShadowBlue' (notebook:0.0): 0.
    The valid values for 'CursorShadowBlue' are in the range 0 - 255
    (inclusive).
    'CursorShadowBlue' can use the following target types: X Screen.

  Attribute 'CursorShadowXOffset' (notebook:0.0): 4.
    The valid values for 'CursorShadowXOffset' are in the range 0 - 32
    (inclusive).
    'CursorShadowXOffset' can use the following target types: X Screen.

  Attribute 'CursorShadowYOffset' (notebook:0.0): 2.
    The valid values for 'CursorShadowYOffset' are in the range 0 - 32
    (inclusive).
    'CursorShadowYOffset' can use the following target types: X Screen.

  Attribute 'AssociatedDisplays' (notebook:0.0): 0x00010001.
    'AssociatedDisplays' is a bitmask attribute.
    'AssociatedDisplays' can use the following target types: X Screen.

  Attribute 'InitialPixmapPlacement' (notebook:0.0): 2.
    The valid values for 'InitialPixmapPlacement' are in the range 0 - 4
    (inclusive).
    'InitialPixmapPlacement' can use the following target types: X Screen.

  Attribute 'DynamicTwinview' (notebook:0.0): 1.
    'DynamicTwinview' is an integer attribute.
    'DynamicTwinview' is a read-only attribute.
    'DynamicTwinview' can use the following target types: X Screen.

  Attribute 'MultiGpuDisplayOwner' (notebook:0.0): 0.
    'MultiGpuDisplayOwner' is an integer attribute.
    'MultiGpuDisplayOwner' is a read-only attribute.
    'MultiGpuDisplayOwner' can use the following target types: X Screen.

  Attribute 'GlyphCache' (notebook:0.0): 1.
    The valid values for 'GlyphCache' are in the range 0 - 1 (inclusive).
    'GlyphCache' can use the following target types: X Screen.

  Attribute 'NotebookDisplayChangeLidEvent' (notebook:0.0): 1.
    'NotebookDisplayChangeLidEvent' is an integer attribute.
    'NotebookDisplayChangeLidEvent' can use the following target types: X
    Screen.

  Attribute 'NotebookInternalLCD' (notebook:0.0): 0x00010000.
    'NotebookInternalLCD' is a bitmask attribute.
    'NotebookInternalLCD' is a read-only attribute.
    'NotebookInternalLCD' can use the following target types: X Screen,
    GPU.

  Attribute 'Depth30Allowed' (notebook:0.0): 0.
    'Depth30Allowed' is a boolean attribute; valid values are: 1 (on/true)
    and 0 (off/false).
    'Depth30Allowed' is a read-only attribute.
    'Depth30Allowed' can use the following target types: X Screen, GPU.

  Attribute 'NoScanout' (notebook:0.0): 0.
    'NoScanout' is a boolean attribute; valid values are: 1 (on/true) and 0
    (off/false).
    'NoScanout' is a read-only attribute.
    'NoScanout' can use the following target types: X Screen, GPU.

  Attribute 'XServerUniqueId' (notebook:0.0): 1533514478.
    'XServerUniqueId' is a read-only attribute.
    'XServerUniqueId' can use the following target types: X Screen.

  Attribute 'PixmapCache' (notebook:0.0): 1.
    'PixmapCache' is a boolean attribute; valid values are: 1 (on/true) and
    0 (off/false).
    'PixmapCache' can use the following target types: X Screen.

  Attribute 'PixmapCacheRoundSizeKB' (notebook:0.0): 1024.
    The valid values for 'PixmapCacheRoundSizeKB' are in the range 4 -
    1048576 (inclusive).
    'PixmapCacheRoundSizeKB' can use the following target types: X Screen.

  Attribute 'SyncToVBlank' (notebook:0.0): 0.
    'SyncToVBlank' is a boolean attribute; valid values are: 1 (on/true)
    and 0 (off/false).
    'SyncToVBlank' can use the following target types: X Screen.

  Attribute 'LogAniso' (notebook:0.0): 0.
    The valid values for 'LogAniso' are in the range 0 - 4 (inclusive).
    'LogAniso' can use the following target types: X Screen.

  Attribute 'FSAA' (notebook:0.0): 0.
    Valid values for 'FSAA' are: 0, 1, 5, 7, 8, 9, 10 and 12.
    'FSAA' can use the following target types: X Screen.

  Attribute 'TextureSharpen' (notebook:0.0): 0.
    'TextureSharpen' is a boolean attribute; valid values are: 1 (on/true)
    and 0 (off/false).
    'TextureSharpen' can use the following target types: X Screen.

  Attribute 'AllowFlipping' (notebook:0.0): 1.
    'AllowFlipping' is a boolean attribute; valid values are: 1 (on/true)
    and 0 (off/false).
    'AllowFlipping' can use the following target types: X Screen.

  Attribute 'FSAAAppControlled' (notebook:0.0): 1.
    'FSAAAppControlled' is a boolean attribute; valid values are: 1
    (on/true) and 0 (off/false).
    'FSAAAppControlled' can use the following target types: X Screen.

  Attribute 'LogAnisoAppControlled' (notebook:0.0): 1.
    'LogAnisoAppControlled' is a boolean attribute; valid values are: 1
    (on/true) and 0 (off/false).
    'LogAnisoAppControlled' can use the following target types: X Screen.

  Attribute 'OpenGLImageSettings' (notebook:0.0): 1.
    The valid values for 'OpenGLImageSettings' are in the range 0 - 3
    (inclusive).
    'OpenGLImageSettings' can use the following target types: X Screen.

  Attribute 'FSAAAppEnhanced' (notebook:0.0): 0.
    'FSAAAppEnhanced' is a boolean attribute; valid values are: 1 (on/true)
    and 0 (off/false).
    'FSAAAppEnhanced' can use the following target types: X Screen.

  Attribute 'SliMosaicModeAvailable' (notebook:0.0): 1.
    'SliMosaicModeAvailable' is a boolean attribute; valid values are: 1
    (on/true) and 0 (off/false).
    'SliMosaicModeAvailable' is a read-only attribute.
    'SliMosaicModeAvailable' can use the following target types: X Screen,
    GPU, VCS.

  Attribute 'BusType' (notebook:0.0): 2.
    The valid values for 'BusType' are in the range 0 - 3 (inclusive).
    'BusType' is a read-only attribute.
    'BusType' can use the following target types: X Screen, GPU, SDI Input
    Device.

  Attribute 'PCIEMaxLinkSpeed' (notebook:0.0): 2500.
    'PCIEMaxLinkSpeed' is an integer attribute.
    'PCIEMaxLinkSpeed' is a read-only attribute.
    'PCIEMaxLinkSpeed' can use the following target types: X Screen, GPU,
    SDI Input Device.

  Attribute 'VideoRam' (notebook:0.0): 524288.
    'VideoRam' is an integer attribute.
    'VideoRam' is a read-only attribute.
    'VideoRam' can use the following target types: X Screen, GPU.

  Attribute 'Irq' (notebook:0.0): 16.
    'Irq' is an integer attribute.
    'Irq' is a read-only attribute.
    'Irq' can use the following target types: X Screen, GPU, SDI Input
    Device.

  Attribute 'CUDACores' (notebook:0.0): 32.
    'CUDACores' is an integer attribute.
    'CUDACores' is a read-only attribute.
    'CUDACores' can use the following target types: X Screen, GPU.

  Attribute 'GPUMemoryInterface' (notebook:0.0): 128.
    'GPUMemoryInterface' is an integer attribute.
    'GPUMemoryInterface' is a read-only attribute.
    'GPUMemoryInterface' can use the following target types: X Screen,
    GPU.

  Attribute 'GPUCoreTemp' (notebook:0.0): 57.
    'GPUCoreTemp' is an integer attribute.
    'GPUCoreTemp' is a read-only attribute.
    'GPUCoreTemp' can use the following target types: X Screen, GPU.

  Attribute 'GPU2DClockFreqs' (notebook:0.0): 169,100.
    The valid values for 'GPU2DClockFreqs' are in the ranges 42 - 338, 25 -
    1320 (inclusive).
    'GPU2DClockFreqs' can use the following target types: X Screen, GPU.

  Attribute 'GPU3DClockFreqs' (notebook:0.0): 500,400.
    The valid values for 'GPU3DClockFreqs' are in the ranges 125 - 1000,
    100 - 1320 (inclusive).
    'GPU3DClockFreqs' can use the following target types: X Screen, GPU.

  Attribute 'GPUDefault2DClockFreqs' (notebook:0.0): 169,100.
    'GPUDefault2DClockFreqs' is a packed integer attribute.
    'GPUDefault2DClockFreqs' is a read-only attribute.
    'GPUDefault2DClockFreqs' can use the following target types: X Screen,
    GPU.

  Attribute 'GPUDefault3DClockFreqs' (notebook:0.0): 500,400.
    'GPUDefault3DClockFreqs' is a packed integer attribute.
    'GPUDefault3DClockFreqs' is a read-only attribute.
    'GPUDefault3DClockFreqs' can use the following target types: X Screen,
    GPU.

  Attribute 'GPUCurrentClockFreqs' (notebook:0.0): 500,400.
    'GPUCurrentClockFreqs' is a packed integer attribute.
    'GPUCurrentClockFreqs' is a read-only attribute.
    'GPUCurrentClockFreqs' can use the following target types: X Screen,
    GPU.

  Attribute 'BusRate' (notebook:0.0): 16.
    The valid values for 'BusRate' are in the range 1 - 16 (inclusive).
    'BusRate' is a read-only attribute.
    'BusRate' can use the following target types: X Screen, GPU, SDI Input
    Device.

  Attribute 'PCIEGen' (notebook:0.0): 1.
    'PCIEGen' is an integer attribute.
    'PCIEGen' is a read-only attribute.
    'PCIEGen' can use the following target types: X Screen, GPU, SDI Input
    Device.

  Attribute 'GPUErrors' (notebook:0.0): 0.
    'GPUErrors' is an integer attribute.
    'GPUErrors' is a read-only attribute.
    'GPUErrors' can use the following target types: X Screen.

  Attribute 'GPUPowerSource' (notebook:0.0): 0.
    'GPUPowerSource' is an integer attribute.
    'GPUPowerSource' is a read-only attribute.
    'GPUPowerSource' can use the following target types: X Screen, GPU.

  Attribute 'GPUCurrentPerfMode' (notebook:0.0): 1.
    'GPUCurrentPerfMode' is an integer attribute.
    'GPUCurrentPerfMode' is a read-only attribute.
    'GPUCurrentPerfMode' can use the following target types: X Screen,
    GPU.

  Attribute 'GPUCurrentPerfLevel' (notebook:0.0): 3.
    'GPUCurrentPerfLevel' is an integer attribute.
    'GPUCurrentPerfLevel' is a read-only attribute.
    'GPUCurrentPerfLevel' can use the following target types: X Screen,
    GPU.

  Attribute 'GPUAdaptiveClockState' (notebook:0.0): 1.
    'GPUAdaptiveClockState' is an integer attribute.
    'GPUAdaptiveClockState' is a read-only attribute.
    'GPUAdaptiveClockState' can use the following target types: X Screen,
    GPU.

  Attribute 'GPUPerfModes' (notebook:0.0): perf=0, nvclock=169,
  memclock=100 ; perf=1, nvclock=275, memclock=250 ; perf=2, nvclock=400,
  memclock=400 ; perf=3, nvclock=500, memclock=400 
    'GPUPerfModes' is a string attribute.
    'GPUPerfModes' is a read-only attribute.
    'GPUPerfModes' can use the following target types: X Screen, GPU.

  Attribute 'ECCSupported' (notebook:0.0): 0.
    'ECCSupported' is a boolean attribute; valid values are: 1 (on/true)
    and 0 (off/false).
    'ECCSupported' is a read-only attribute.
    'ECCSupported' can use the following target types: X Screen, GPU.

  Attribute 'ECCConfigurationSupported' (notebook:0.0): 0.
    'ECCConfigurationSupported' is a boolean attribute; valid values are: 1
    (on/true) and 0 (off/false).
    'ECCConfigurationSupported' is a read-only attribute.
    'ECCConfigurationSupported' can use the following target types: X
    Screen, GPU.

  Attribute 'GvoSupported' (notebook:0.0): 0.
    'GvoSupported' is a boolean attribute; valid values are: 1 (on/true)
    and 0 (off/false).
    'GvoSupported' is a read-only attribute.
    'GvoSupported' can use the following target types: X Screen.

  Attribute 'IsGvoDisplay' (notebook:0.0): 0.
    'IsGvoDisplay' is a boolean attribute; valid values are: 1 (on/true)
    and 0 (off/false).
    'IsGvoDisplay' is a read-only attribute.
    'IsGvoDisplay' can use the following target types: X Screen, GPU.

  Attribute 'DigitalVibrance' (notebook:0.0; display device: CRT-0): 0.
    The valid values for 'DigitalVibrance' are in the range -1024 - 1023
    (inclusive).
    'DigitalVibrance' is display device specific.
    'DigitalVibrance' can use the following target types: X Screen, GPU.

  Attribute 'DigitalVibrance' (notebook:0.0; display device: DFP-0): 0.
    The valid values for 'DigitalVibrance' are in the range -1024 - 1023
    (inclusive).
    'DigitalVibrance' is display device specific.
    'DigitalVibrance' can use the following target types: X Screen, GPU.

  Attribute 'RefreshRate' (notebook:0.0; display device: CRT-0): 59,79 Hz.
    'RefreshRate' is an integer attribute.
    'RefreshRate' is a read-only attribute.
    'RefreshRate' is display device specific.
    'RefreshRate' can use the following target types: X Screen, GPU.

  Attribute 'RefreshRate' (notebook:0.0; display device: DFP-0): 59,98 Hz.
    'RefreshRate' is an integer attribute.
    'RefreshRate' is a read-only attribute.
    'RefreshRate' is display device specific.
    'RefreshRate' can use the following target types: X Screen, GPU.

  Attribute 'RefreshRate3' (notebook:0.0; display device: CRT-0): 59,790
  Hz.
    'RefreshRate3' is an integer attribute.
    'RefreshRate3' is a read-only attribute.
    'RefreshRate3' is display device specific.
    'RefreshRate3' can use the following target types: X Screen, GPU.

  Attribute 'RefreshRate3' (notebook:0.0; display device: DFP-0): 59,976
  Hz.
    'RefreshRate3' is an integer attribute.
    'RefreshRate3' is a read-only attribute.
    'RefreshRate3' is display device specific.
    'RefreshRate3' can use the following target types: X Screen, GPU.

  Attribute 'OverscanCompensation' (notebook:0.0; display device: CRT-0):
  0.
    The valid values for 'OverscanCompensation' are in the range 0 - 200
    (inclusive).
    'OverscanCompensation' is display device specific.
    'OverscanCompensation' can use the following target types: X Screen,
    GPU.

  Attribute 'OverscanCompensation' (notebook:0.0; display device: DFP-0):
  0.
    The valid values for 'OverscanCompensation' are in the range 0 - 200
    (inclusive).
    'OverscanCompensation' is display device specific.
    'OverscanCompensation' can use the following target types: X Screen,
    GPU.

  Attribute 'XVideoTextureBrightness' (notebook:0.0): 0.
    The valid values for 'XVideoTextureBrightness' are in the range -1000 -
    1000 (inclusive).
    'XVideoTextureBrightness' can use the following target types: X
    Screen.

  Attribute 'XVideoTextureContrast' (notebook:0.0): 0.
    The valid values for 'XVideoTextureContrast' are in the range -1000 -
    1000 (inclusive).
    'XVideoTextureContrast' can use the following target types: X Screen.

  Attribute 'XVideoTextureHue' (notebook:0.0): 0.
    The valid values for 'XVideoTextureHue' are in the range -1000 - 1000
    (inclusive).
    'XVideoTextureHue' can use the following target types: X Screen.

  Attribute 'XVideoTextureSaturation' (notebook:0.0): 0.
    The valid values for 'XVideoTextureSaturation' are in the range -1000 -
    1000 (inclusive).
    'XVideoTextureSaturation' can use the following target types: X
    Screen.

  Attribute 'XVideoTextureSyncToVBlank' (notebook:0.0): 1.
    The valid values for 'XVideoTextureSyncToVBlank' are in the range 0 - 1
    (inclusive).
    'XVideoTextureSyncToVBlank' can use the following target types: X
    Screen.

  Attribute 'XVideoSyncToDisplay' (notebook:0.0): 0x00000001.
    'XVideoSyncToDisplay' is a bitmask attribute.
    'XVideoSyncToDisplay' can use the following target types: X Screen.

Attributes queryable via notebook:0[gpu:0]:

  Attribute 'OperatingSystem' (notebook:0[gpu:0]): 0.
    The valid values for 'OperatingSystem' are in the range 0 - 2
    (inclusive).
    'OperatingSystem' is a read-only attribute.
    'OperatingSystem' can use the following target types: X Screen, GPU.

  Attribute 'NvidiaDriverVersion' (notebook:0[gpu:0]): 256.44 
    'NvidiaDriverVersion' is a string attribute.
    'NvidiaDriverVersion' is a read-only attribute.
    'NvidiaDriverVersion' can use the following target types: X Screen,
    GPU.

  Attribute 'ConnectedDisplays' (notebook:0[gpu:0]): 0x00010001.
    'ConnectedDisplays' is a bitmask attribute.
    'ConnectedDisplays' is a read-only attribute.
    'ConnectedDisplays' can use the following target types: X Screen, GPU.

  Attribute 'EnabledDisplays' (notebook:0[gpu:0]): 0x00010001.
    'EnabledDisplays' is a bitmask attribute.
    'EnabledDisplays' is a read-only attribute.
    'EnabledDisplays' can use the following target types: X Screen, GPU.

  Attribute 'NotebookInternalLCD' (notebook:0[gpu:0]): 0x00010000.
    'NotebookInternalLCD' is a bitmask attribute.
    'NotebookInternalLCD' is a read-only attribute.
    'NotebookInternalLCD' can use the following target types: X Screen,
    GPU.

  Attribute 'Depth30Allowed' (notebook:0[gpu:0]): 0.
    'Depth30Allowed' is a boolean attribute; valid values are: 1 (on/true)
    and 0 (off/false).
    'Depth30Allowed' is a read-only attribute.
    'Depth30Allowed' can use the following target types: X Screen, GPU.

  Attribute 'NoScanout' (notebook:0[gpu:0]): 0.
    'NoScanout' is a boolean attribute; valid values are: 1 (on/true) and 0
    (off/false).
    'NoScanout' is a read-only attribute.
    'NoScanout' can use the following target types: X Screen, GPU.

  Attribute 'SliMosaicModeAvailable' (notebook:0[gpu:0]): 1.
    'SliMosaicModeAvailable' is a boolean attribute; valid values are: 1
    (on/true) and 0 (off/false).
    'SliMosaicModeAvailable' is a read-only attribute.
    'SliMosaicModeAvailable' can use the following target types: X Screen,
    GPU, VCS.

  Attribute 'BusType' (notebook:0[gpu:0]): 2.
    The valid values for 'BusType' are in the range 0 - 3 (inclusive).
    'BusType' is a read-only attribute.
    'BusType' can use the following target types: X Screen, GPU, SDI Input
    Device.

  Attribute 'PCIEMaxLinkSpeed' (notebook:0[gpu:0]): 2500.
    'PCIEMaxLinkSpeed' is an integer attribute.
    'PCIEMaxLinkSpeed' is a read-only attribute.
    'PCIEMaxLinkSpeed' can use the following target types: X Screen, GPU,
    SDI Input Device.

  Attribute 'VideoRam' (notebook:0[gpu:0]): 524288.
    'VideoRam' is an integer attribute.
    'VideoRam' is a read-only attribute.
    'VideoRam' can use the following target types: X Screen, GPU.

  Attribute 'Irq' (notebook:0[gpu:0]): 16.
    'Irq' is an integer attribute.
    'Irq' is a read-only attribute.
    'Irq' can use the following target types: X Screen, GPU, SDI Input
    Device.

  Attribute 'CUDACores' (notebook:0[gpu:0]): 32.
    'CUDACores' is an integer attribute.
    'CUDACores' is a read-only attribute.
    'CUDACores' can use the following target types: X Screen, GPU.

  Attribute 'GPUMemoryInterface' (notebook:0[gpu:0]): 128.
    'GPUMemoryInterface' is an integer attribute.
    'GPUMemoryInterface' is a read-only attribute.
    'GPUMemoryInterface' can use the following target types: X Screen,
    GPU.

  Attribute 'GPUCoreTemp' (notebook:0[gpu:0]): 57.
    'GPUCoreTemp' is an integer attribute.
    'GPUCoreTemp' is a read-only attribute.
    'GPUCoreTemp' can use the following target types: X Screen, GPU.

  Attribute 'GPU2DClockFreqs' (notebook:0[gpu:0]): 169,100.
    The valid values for 'GPU2DClockFreqs' are in the ranges 42 - 338, 25 -
    1320 (inclusive).
    'GPU2DClockFreqs' can use the following target types: X Screen, GPU.

  Attribute 'GPU3DClockFreqs' (notebook:0[gpu:0]): 500,400.
    The valid values for 'GPU3DClockFreqs' are in the ranges 125 - 1000,
    100 - 1320 (inclusive).
    'GPU3DClockFreqs' can use the following target types: X Screen, GPU.

  Attribute 'GPUDefault2DClockFreqs' (notebook:0[gpu:0]): 169,100.
    'GPUDefault2DClockFreqs' is a packed integer attribute.
    'GPUDefault2DClockFreqs' is a read-only attribute.
    'GPUDefault2DClockFreqs' can use the following target types: X Screen,
    GPU.

  Attribute 'GPUDefault3DClockFreqs' (notebook:0[gpu:0]): 500,400.
    'GPUDefault3DClockFreqs' is a packed integer attribute.
    'GPUDefault3DClockFreqs' is a read-only attribute.
    'GPUDefault3DClockFreqs' can use the following target types: X Screen,
    GPU.

  Attribute 'GPUCurrentClockFreqs' (notebook:0[gpu:0]): 500,400.
    'GPUCurrentClockFreqs' is a packed integer attribute.
    'GPUCurrentClockFreqs' is a read-only attribute.
    'GPUCurrentClockFreqs' can use the following target types: X Screen,
    GPU.

  Attribute 'BusRate' (notebook:0[gpu:0]): 16.
    The valid values for 'BusRate' are in the range 1 - 16 (inclusive).
    'BusRate' is a read-only attribute.
    'BusRate' can use the following target types: X Screen, GPU, SDI Input
    Device.

  Attribute 'PCIDomain' (notebook:0[gpu:0]): 0.
    'PCIDomain' is an integer attribute.
    'PCIDomain' is a read-only attribute.
    'PCIDomain' can use the following target types: GPU, SDI Input Device.

  Attribute 'PCIBus' (notebook:0[gpu:0]): 1.
    'PCIBus' is an integer attribute.
    'PCIBus' is a read-only attribute.
    'PCIBus' can use the following target types: GPU, SDI Input Device.

  Attribute 'PCIDevice' (notebook:0[gpu:0]): 0.
    'PCIDevice' is an integer attribute.
    'PCIDevice' is a read-only attribute.
    'PCIDevice' can use the following target types: GPU, SDI Input Device.

  Attribute 'PCIFunc' (notebook:0[gpu:0]): 0.
    'PCIFunc' is an integer attribute.
    'PCIFunc' is a read-only attribute.
    'PCIFunc' can use the following target types: GPU, SDI Input Device.

  Attribute 'PCIID' (notebook:0[gpu:0]): 4318,1609.
    'PCIID' is a packed integer attribute.
    'PCIID' is a read-only attribute.
    'PCIID' can use the following target types: GPU, SDI Input Device.

  Attribute 'PCIEGen' (notebook:0[gpu:0]): 1.
    'PCIEGen' is an integer attribute.
    'PCIEGen' is a read-only attribute.
    'PCIEGen' can use the following target types: X Screen, GPU, SDI Input
    Device.

  Attribute 'GPUPowerSource' (notebook:0[gpu:0]): 0.
    'GPUPowerSource' is an integer attribute.
    'GPUPowerSource' is a read-only attribute.
    'GPUPowerSource' can use the following target types: X Screen, GPU.

  Attribute 'GPUCurrentPerfMode' (notebook:0[gpu:0]): 1.
    'GPUCurrentPerfMode' is an integer attribute.
    'GPUCurrentPerfMode' is a read-only attribute.
    'GPUCurrentPerfMode' can use the following target types: X Screen,
    GPU.

  Attribute 'GPUCurrentPerfLevel' (notebook:0[gpu:0]): 3.
    'GPUCurrentPerfLevel' is an integer attribute.
    'GPUCurrentPerfLevel' is a read-only attribute.
    'GPUCurrentPerfLevel' can use the following target types: X Screen,
    GPU.

  Attribute 'GPUAdaptiveClockState' (notebook:0[gpu:0]): 1.
    'GPUAdaptiveClockState' is an integer attribute.
    'GPUAdaptiveClockState' is a read-only attribute.
    'GPUAdaptiveClockState' can use the following target types: X Screen,
    GPU.

  Attribute 'GPUPerfModes' (notebook:0[gpu:0]): perf=0, nvclock=169,
  memclock=100 ; perf=1, nvclock=275, memclock=250 ; perf=2, nvclock=400,
  memclock=400 ; perf=3, nvclock=500, memclock=400 
    'GPUPerfModes' is a string attribute.
    'GPUPerfModes' is a read-only attribute.
    'GPUPerfModes' can use the following target types: X Screen, GPU.

  Attribute 'GPUPowerMizerMode' (notebook:0[gpu:0]): 0.
    'GPUPowerMizerMode' is an integer attribute.
    'GPUPowerMizerMode' can use the following target types: GPU.

  Attribute 'ECCSupported' (notebook:0[gpu:0]): 0.
    'ECCSupported' is a boolean attribute; valid values are: 1 (on/true)
    and 0 (off/false).
    'ECCSupported' is a read-only attribute.
    'ECCSupported' can use the following target types: X Screen, GPU.

  Attribute 'ECCConfigurationSupported' (notebook:0[gpu:0]): 0.
    'ECCConfigurationSupported' is a boolean attribute; valid values are: 1
    (on/true) and 0 (off/false).
    'ECCConfigurationSupported' is a read-only attribute.
    'ECCConfigurationSupported' can use the following target types: X
    Screen, GPU.

  Attribute 'IsGvoDisplay' (notebook:0[gpu:0]): 0.
    'IsGvoDisplay' is a boolean attribute; valid values are: 1 (on/true)
    and 0 (off/false).
    'IsGvoDisplay' is a read-only attribute.
    'IsGvoDisplay' can use the following target types: X Screen, GPU.

  Attribute 'DigitalVibrance' (notebook:0[gpu:0]; display device: CRT-0):
  0.
    The valid values for 'DigitalVibrance' are in the range -1024 - 1023
    (inclusive).
    'DigitalVibrance' is display device specific.
    'DigitalVibrance' can use the following target types: X Screen, GPU.

  Attribute 'DigitalVibrance' (notebook:0[gpu:0]; display device: DFP-0):
  0.
    The valid values for 'DigitalVibrance' are in the range -1024 - 1023
    (inclusive).
    'DigitalVibrance' is display device specific.
    'DigitalVibrance' can use the following target types: X Screen, GPU.

  Attribute 'RefreshRate' (notebook:0[gpu:0]; display device: CRT-0): 59,79
  Hz.
    'RefreshRate' is an integer attribute.
    'RefreshRate' is a read-only attribute.
    'RefreshRate' is display device specific.
    'RefreshRate' can use the following target types: X Screen, GPU.

  Attribute 'RefreshRate' (notebook:0[gpu:0]; display device: DFP-0): 59,98
  Hz.
    'RefreshRate' is an integer attribute.
    'RefreshRate' is a read-only attribute.
    'RefreshRate' is display device specific.
    'RefreshRate' can use the following target types: X Screen, GPU.

  Attribute 'RefreshRate3' (notebook:0[gpu:0]; display device: CRT-0):
  59,790 Hz.
    'RefreshRate3' is an integer attribute.
    'RefreshRate3' is a read-only attribute.
    'RefreshRate3' is display device specific.
    'RefreshRate3' can use the following target types: X Screen, GPU.

  Attribute 'RefreshRate3' (notebook:0[gpu:0]; display device: DFP-0):
  59,976 Hz.
    'RefreshRate3' is an integer attribute.
    'RefreshRate3' is a read-only attribute.
    'RefreshRate3' is display device specific.
    'RefreshRate3' can use the following target types: X Screen, GPU.

  Attribute 'OverscanCompensation' (notebook:0[gpu:0]; display device:
  CRT-0): 0.
    The valid values for 'OverscanCompensation' are in the range 0 - 200
    (inclusive).
    'OverscanCompensation' is display device specific.
    'OverscanCompensation' can use the following target types: X Screen,
    GPU.

  Attribute 'OverscanCompensation' (notebook:0[gpu:0]; display device:
  DFP-0): 0.
    The valid values for 'OverscanCompensation' are in the range 0 - 200
    (inclusive).
    'OverscanCompensation' is display device specific.
    'OverscanCompensation' can use the following target types: X Screen,
    GPU.

Attributes queryable via notebook:0[thermalsensor:0]:

  Attribute 'ThermalSensorReading' (notebook:0[thermalsensor:0]): 57.
    The valid values for 'ThermalSensorReading' are in the range 0 - 127
    (inclusive).
    'ThermalSensorReading' is a read-only attribute.
    'ThermalSensorReading' can use the following target types: Thermal
    Sensor.

  Attribute 'ThermalSensorProvider' (notebook:0[thermalsensor:0]): 1.
    'ThermalSensorProvider' is an integer attribute.
    'ThermalSensorProvider' is a read-only attribute.
    'ThermalSensorProvider' can use the following target types: Thermal
    Sensor.

  Attribute 'ThermalSensorTarget' (notebook:0[thermalsensor:0]): 1.
    'ThermalSensorTarget' is an integer attribute.
    'ThermalSensorTarget' is a read-only attribute.
    'ThermalSensorTarget' can use the following target types: Thermal
    Sensor.

____________________________________________

/proc/cmdline
BOOT_IMAGE=/boot/vmlinuz-2.6.32-24-generic root=UUID=2846023d-9f02-4faa-a800-861f102d748e ro splash quiet splash nomodeset video=uvesafb:mode_option=1280x800-24,mtrr=3,scroll=ywrap

____________________________________________

/proc/cpuinfo
processor	: 0
vendor_id	: GenuineIntel
cpu family	: 6
model		: 23
model name	: Intel(R) Core(TM)2 Duo CPU     P8600  @ 2.40GHz
stepping	: 6
cpu MHz		: 800.000
cache size	: 3072 KB
physical id	: 0
siblings	: 2
core id		: 0
cpu cores	: 2
apicid		: 0
initial apicid	: 0
fpu		: yes
fpu_exception	: yes
cpuid level	: 10
wp		: yes
flags		: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx lm constant_tsc arch_perfmon pebs bts rep_good aperfmperf pni dtes64 monitor ds_cpl vmx smx est tm2 ssse3 cx16 xtpr pdcm sse4_1 lahf_lm tpr_shadow vnmi flexpriority
bogomips	: 4788.93
clflush size	: 64
cache_alignment	: 64
address sizes	: 36 bits physical, 48 bits virtual
power management:

processor	: 1
vendor_id	: GenuineIntel
cpu family	: 6
model		: 23
model name	: Intel(R) Core(TM)2 Duo CPU     P8600  @ 2.40GHz
stepping	: 6
cpu MHz		: 800.000
cache size	: 3072 KB
physical id	: 0
siblings	: 2
core id		: 1
cpu cores	: 2
apicid		: 1
initial apicid	: 1
fpu		: yes
fpu_exception	: yes
cpuid level	: 10
wp		: yes
flags		: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx lm constant_tsc arch_perfmon pebs bts rep_good aperfmperf pni dtes64 monitor ds_cpl vmx smx est tm2 ssse3 cx16 xtpr pdcm sse4_1 lahf_lm tpr_shadow vnmi flexpriority
bogomips	: 4788.52
clflush size	: 64
cache_alignment	: 64
address sizes	: 36 bits physical, 48 bits virtual
power management:


____________________________________________

/proc/interrupts
           CPU0       CPU1       
  0:   13810323   14357155   IO-APIC-edge      timer
  1:          2      12532   IO-APIC-edge      i8042
  4:          0          0   IO-APIC-edge      enecir
  8:          1          0   IO-APIC-edge      rtc0
  9:      32016        112   IO-APIC-fasteoi   acpi
 12:          3          0   IO-APIC-edge      i8042
 16:         76      52091   IO-APIC-fasteoi   uhci_hcd:usb3, uhci_hcd:usb7, ohci1394, mmc0, jmb38x_ms:slot0, nvidia
 18:          0          0   IO-APIC-fasteoi   uhci_hcd:usb8
 19:    1236540        293   IO-APIC-fasteoi   ehci_hcd:usb1, uhci_hcd:usb6
 20:     106802          8   IO-APIC-fasteoi   ehci_hcd:usb2, uhci_hcd:usb5
 21:          0          0   IO-APIC-fasteoi   uhci_hcd:usb4
 22:        408      62367   IO-APIC-fasteoi   HDA Intel
 31:          0          0   PCI-MSI-edge      eth0
 32:     775872       1909   PCI-MSI-edge      ahci
 33:    2526830    2613612   PCI-MSI-edge      iwlagn
NMI:          0          0   Non-maskable interrupts
LOC:   80189277   25056776   Local timer interrupts
SPU:          0          0   Spurious interrupts
PMI:          0          0   Performance monitoring interrupts
PND:          0          0   Performance pending work
RES:    2041773    2221270   Rescheduling interrupts
CAL:       4830        436   Function call interrupts
TLB:     368951     586495   TLB shootdowns
TRM:          0          0   Thermal event interrupts
THR:          0          0   Threshold APIC interrupts
MCE:          0          0   Machine check exceptions
MCP:        174        174   Machine check polls
ERR:          1
MIS:          0

____________________________________________

/proc/meminfo
MemTotal:        4027116 kB
MemFree:          719432 kB
Buffers:          173384 kB
Cached:          1642872 kB
SwapCached:            0 kB
Active:          1810844 kB
Inactive:        1163780 kB
Active(anon):    1176508 kB
Inactive(anon):       16 kB
Active(file):     634336 kB
Inactive(file):  1163764 kB
Unevictable:          56 kB
Mlocked:              56 kB
SwapTotal:       3668984 kB
SwapFree:        3668984 kB
Dirty:                 4 kB
Writeback:            60 kB
AnonPages:       1158592 kB
Mapped:           205508 kB
Shmem:             18160 kB
Slab:             133900 kB
SReclaimable:     107656 kB
SUnreclaim:        26244 kB
KernelStack:        3416 kB
PageTables:        42404 kB
NFS_Unstable:          0 kB
Bounce:                0 kB
WritebackTmp:          0 kB
CommitLimit:     5682540 kB
Committed_AS:    2682456 kB
VmallocTotal:   34359738367 kB
VmallocUsed:      144304 kB
VmallocChunk:   34359588348 kB
HardwareCorrupted:     0 kB
HugePages_Total:       0
HugePages_Free:        0
HugePages_Rsvd:        0
HugePages_Surp:        0
Hugepagesize:       2048 kB
DirectMap4k:       86016 kB
DirectMap2M:     4075520 kB

____________________________________________

/proc/modules
cryptd 8116 0 - Live 0xffffffffa0bf8000
aes_x86_64 7912 3 - Live 0xffffffffa0bc7000
aes_generic 27607 1 aes_x86_64, Live 0xffffffffa0bff000
nls_iso8859_1 4633 1 - Live 0xffffffffa0bfb000
nls_cp437 6351 1 - Live 0xffffffffa0bf4000
vfat 10866 1 - Live 0xffffffffa0bef000
fat 55350 1 vfat, Live 0xffffffffa0bdf000
binfmt_misc 7960 1 - Live 0xffffffffa0bab000
rfcomm 40393 4 - Live 0xffffffffa0bd3000
ppdev 6375 0 - Live 0xffffffffa0ba1000
sco 9617 2 - Live 0xffffffffa0bce000
bridge 53184 0 - Live 0xffffffffa0bb8000
stp 2171 1 bridge, Live 0xffffffffa0baf000
bnep 11884 2 - Live 0xffffffffa0ba6000
l2cap 34806 16 rfcomm,bnep, Live 0xffffffffa0b96000
vboxnetadp 5171 0 - Live 0xffffffffa0bb1000
vboxnetflt 14998 0 - Live 0xffffffffa0b8b000
vboxdrv 1792440 2 vboxnetadp,vboxnetflt, Live 0xffffffffa0e61000
snd_hda_codec_nvhdmi 4760 1 - Live 0xffffffffa0b92000
snd_hda_codec_idt 61450 1 - Live 0xffffffffa0b79000
arc4 1473 2 - Live 0xffffffffa0cb0000
snd_hda_intel 25677 4 - Live 0xffffffffa0e58000
snd_hda_codec 85759 3 snd_hda_codec_nvhdmi,snd_hda_codec_idt,snd_hda_intel, Live 0xffffffffa0e36000
snd_hwdep 6924 1 snd_hda_codec, Live 0xffffffffa0cde000
snd_pcm_oss 41394 0 - Live 0xffffffffa0e29000
snd_mixer_oss 16299 1 snd_pcm_oss, Live 0xffffffffa0d10000
snd_pcm 87882 4 snd_hda_intel,snd_hda_codec,snd_pcm_oss, Live 0xffffffffa0e07000
snd_seq_dummy 1782 0 - Live 0xffffffffa005c000
snd_seq_oss 31219 0 - Live 0xffffffffa0dbf000
snd_seq_midi 5829 0 - Live 0xffffffffa00d8000
snd_rawmidi 23420 1 snd_seq_midi, Live 0xffffffffa0ca8000
snd_seq_midi_event 7267 2 snd_seq_oss,snd_seq_midi, Live 0xffffffffa002e000
snd_seq 57481 6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event, Live 0xffffffffa0df6000
iwlagn 121641 0 - Live 0xffffffffa0dcd000
snd_timer 23649 2 snd_pcm,snd_seq, Live 0xffffffffa0cf5000
snd_seq_device 6888 5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq, Live 0xffffffffa0027000
iwlcore 124955 1 iwlagn, Live 0xffffffffa0d9e000
mac80211 238448 2 iwlagn,iwlcore, Live 0xffffffffa0d61000
jmb38x_ms 8643 0 - Live 0xffffffffa0d59000
joydev 11072 0 - Live 0xffffffffa0d51000
uvcvideo 62467 0 - Live 0xffffffffa0d3a000
videodev 40518 1 uvcvideo, Live 0xffffffffa0d29000
v4l1_compat 15495 2 uvcvideo,videodev, Live 0xffffffffa0d23000
v4l2_compat_ioctl32 12020 1 videodev, Live 0xffffffffa0d1e000
btusb 12969 2 - Live 0xffffffffa0d18000
bluetooth 58685 9 rfcomm,sco,bnep,l2cap,btusb, Live 0xffffffffa0cff000
memstick 10121 1 jmb38x_ms, Live 0xffffffffa0cd6000
snd 71106 19 snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device, Live 0xffffffffa0ce1000
sdhci_pci 6700 0 - Live 0xffffffffa0cda000
sdhci 17928 1 sdhci_pci, Live 0xffffffffa0ccf000
psmouse 64576 0 - Live 0xffffffffa0cb7000
serio_raw 4918 0 - Live 0xffffffffa00e0000
lirc_ene0100 7532 0 - Live 0xffffffffa0053000
lirc_dev 11302 1 lirc_ene0100, Live 0xffffffffa0022000
cfg80211 148546 3 iwlagn,iwlcore,mac80211, Live 0xffffffffa0c81000
nvidia 11070680 43 - Live 0xffffffffa00e8000 (P)
soundcore 8052 1 snd, Live 0xffffffffa00e4000
snd_page_alloc 8500 2 snd_hda_intel,snd_pcm, Live 0xffffffffa00db000
hp_accel 12168 0 - Live 0xffffffffa0067000
lis3lv02d 7648 1 hp_accel, Live 0xffffffffa0056000
input_polldev 3106 1 lis3lv02d, Live 0xffffffffa0034000
lp 9336 0 - Live 0xffffffffa0043000
led_class 3764 3 iwlcore,sdhci,hp_accel, Live 0xffffffffa000d000
parport 37160 2 ppdev,lp, Live 0xffffffffa0086000
uvesafb 24962 0 - Live 0xffffffffa00cf000
usbhid 41084 0 - Live 0xffffffffa00c2000
hid 83440 1 usbhid, Live 0xffffffffa00ab000
usb_storage 49833 1 - Live 0xffffffffa009c000
ohci1394 30260 0 - Live 0xffffffffa0092000
ieee1394 94771 1 ohci1394, Live 0xffffffffa006c000
video 20623 0 - Live 0xffffffffa005f000
output 2503 1 video, Live 0xffffffffa0059000
ahci 37870 2 - Live 0xffffffffa0047000
fbcon 39270 71 - Live 0xffffffffa0037000
tileblit 2487 1 fbcon, Live 0xffffffffa0031000
font 8053 1 fbcon, Live 0xffffffffa002a000
bitblit 5811 1 fbcon, Live 0xffffffffa0013000
softcursor 1565 1 bitblit, Live 0xffffffffa000a000
r8169 39650 0 - Live 0xffffffffa0016000
mii 5237 1 r8169, Live 0xffffffffa000f000
intel_agp 29095 0 - Live 0xffffffffa0000000

____________________________________________

/proc/version
Linux version 2.6.32-24-generic (buildd@yellow) (gcc version 4.4.3 (Ubuntu 4.4.3-4ubuntu5) ) #39-Ubuntu SMP Wed Jul 28 05:14:15 UTC 2010

____________________________________________

/proc/pci does not exist

____________________________________________

/proc/iomem
00000000-00000fff : System RAM
00001000-00005fff : reserved
00006000-0009dfff : System RAM
0009e000-0009ffff : reserved
000e0000-000fffff : reserved
00100000-bca98fff : System RAM
  01000000-0154bb16 : Kernel code
  0154bb17-018349cf : Kernel data
  0191e000-01a2fe63 : Kernel bss
bca99000-bca9bfff : ACPI Non-volatile Storage
bca9c000-bdea7fff : System RAM
bdea8000-bdebefff : reserved
bdebf000-bdf85fff : System RAM
bdf86000-bdfbefff : ACPI Non-volatile Storage
bdfbf000-bdfdffff : System RAM
bdfe0000-bdff5fff : ACPI Tables
bdff6000-bdffffff : System RAM
be000000-bfffffff : reserved
c0000000-cfffffff : PCI Bus 0000:01
  c0000000-cfffffff : 0000:01:00.0
d0000000-d2ffffff : PCI Bus 0000:01
  d0000000-d1ffffff : 0000:01:00.0
    d1000000-d13effff : efifb
  d2000000-d2ffffff : 0000:01:00.0
    d2000000-d2ffffff : nvidia
d3000000-d3ffffff : PCI Bus 0000:02
d4000000-d50fffff : PCI Bus 0000:03
  d4000000-d400ffff : 0000:03:00.0
    d4000000-d400ffff : r8169
  d4010000-d4010fff : 0000:03:00.0
    d4010000-d4010fff : r8169
  d4020000-d402ffff : 0000:03:00.0
d5100000-d60fffff : PCI Bus 0000:04
d6100000-d70fffff : PCI Bus 0000:05
d7100000-d80fffff : PCI Bus 0000:06
d8100000-d90fffff : PCI Bus 0000:07
d9100000-da0fffff : PCI Bus 0000:07
da100000-db1fffff : PCI Bus 0000:06
  da100000-da1007ff : 0000:06:00.0
    da100000-da1007ff : ohci1394
  da100800-da1008ff : 0000:06:00.4
  da100900-da1009ff : 0000:06:00.3
    da100900-da1009ff : jmb38x_ms
  da100a00-da100aff : 0000:06:00.2
  da100b00-da100bff : 0000:06:00.1
    da100b00-da100bff : mmc0
  da100c00-da100c7f : 0000:06:00.0
  da100c80-da100cff : 0000:06:00.0
  da100d00-da100d7f : 0000:06:00.0
db200000-dc1fffff : PCI Bus 0000:05
dc200000-dd1fffff : PCI Bus 0000:04
dd200000-de1fffff : PCI Bus 0000:03
de200000-df2fffff : PCI Bus 0000:02
  de200000-de201fff : 0000:02:00.0
    de200000-de201fff : iwlagn
df300000-df303fff : 0000:00:1b.0
  df300000-df303fff : ICH HD audio
df304000-df304fff : 0000:00:1f.6
df305000-df3057ff : 0000:00:1f.2
  df305000-df3057ff : ahci
df305800-df305bff : 0000:00:1d.7
  df305800-df305bff : ehci_hcd
df305c00-df305fff : 0000:00:1a.7
  df305c00-df305fff : ehci_hcd
df306000-df3060ff : 0000:00:1f.3
f8000000-fbffffff : PCI MMCONFIG 0 [00-3f]
  f8000000-fbffffff : reserved
    f8000000-fbffffff : pnp 00:00
      f8000000-fbffffff : pnp 00:02
fec00000-fec00fff : IOAPIC 0
  fec00000-fec00fff : reserved
fed00000-fed003ff : HPET 0
fed10000-fed13fff : reserved
  fed10000-fed13fff : pnp 00:02
fed18000-fed19fff : reserved
  fed18000-fed18fff : pnp 00:02
  fed19000-fed19fff : pnp 00:02
fed1c000-fed1ffff : reserved
  fed1c000-fed1ffff : pnp 00:02
fed20000-fed3ffff : pnp 00:02
fed40000-fed44fff : pnp 00:02
fed45000-fed8ffff : pnp 00:02
fee00000-fee00fff : Local APIC
  fee00000-fee00fff : reserved
    fee00000-fee00fff : pnp 00:02
fff00000-ffffffff : reserved
100000000-13fffffff : System RAM

____________________________________________

/proc/mtrr
reg00: base=0x000000000 (    0MB), size= 2048MB, count=1: write-back
reg01: base=0x0fffe0000 ( 4095MB), size=  128KB, count=1: write-protect
reg02: base=0x0fffd8000 ( 4095MB), size=   32KB, count=1: write-protect
reg03: base=0x080000000 ( 2048MB), size= 1024MB, count=1: write-back
reg04: base=0x0be000000 ( 3040MB), size=   32MB, count=1: uncachable
reg05: base=0x100000000 ( 4096MB), size= 1024MB, count=1: write-back

____________________________________________

/proc/driver/nvidia/version
NVRM version: NVIDIA UNIX x86_64 Kernel Module  256.44  Thu Jul 29 01:22:44 PDT 2010
GCC version:  gcc version 4.4.3 (Ubuntu 4.4.3-4ubuntu5) 

____________________________________________

/proc/driver/nvidia/cards/0
Model: 		 GeForce 9600M GT
IRQ:   		 16
Video BIOS: 	 62.94.1a.00.19
Card Type: 	 PCI-E
DMA Size: 	 40 bits
DMA Mask: 	 0xffffffffff
Bus Location: 	 0000:01.00.0

____________________________________________

/proc/driver/nvidia/warnings/README
The NVIDIA graphics driver tries to detect potential problems
with the host system and warns about them using the system's
logging mechanisms. Important warning message are also logged
to dedicated text files in this directory.

____________________________________________

/proc/driver/nvidia/registry
EnableVia4x: 0
EnableALiAGP: 0
NvAGP: 3
ReqAGPRate: 15
EnableAGPSBA: 0
EnableAGPFW: 0
Mobile: 4294967295
ResmanDebugLevel: 4294967295
RmLogonRC: 1
ModifyDeviceFiles: 1
DeviceFileUID: 0
DeviceFileGID: 0
DeviceFileMode: 438
RemapLimit: 0
UpdateMemoryTypes: 4294967295
UseVBios: 1
RMEdgeIntrCheck: 1
UsePageAttributeTable: 4294967295
EnableMSI: 0
MapRegistersEarly: 0
RegisterForACPIEvents: 1
RegistryDwords: ""

____________________________________________

/proc/acpi/video/VGA/CRT/info
device_id:    0x0100
type:         UNKNOWN
known by bios: no

____________________________________________

/proc/acpi/video/VGA/HDMI/info
device_id:    0x0121
type:         UNKNOWN
known by bios: no

____________________________________________

/proc/acpi/video/VGA/LCD/info
device_id:    0x0118
type:         UNKNOWN
known by bios: no

____________________________________________

/proc/asound/cards
 0 [Intel          ]: HDA-Intel - HDA Intel
                      HDA Intel at 0xdf300000 irq 22

____________________________________________

/proc/asound/pcm
00-00: STAC92xx Analog : STAC92xx Analog : playback 1 : capture 2
00-01: STAC92xx Digital : STAC92xx Digital : playback 1
00-03: NVIDIA HDMI : NVIDIA HDMI : playback 1

____________________________________________

/proc/asound/modules
 0 snd_hda_intel

____________________________________________

/proc/asound/devices
  2:        : timer
  3:        : sequencer
  4: [ 0- 3]: digital audio playback
  5: [ 0- 1]: digital audio playback
  6: [ 0- 0]: digital audio playback
  7: [ 0- 0]: digital audio capture
  8: [ 0- 2]: hardware dependent
  9: [ 0- 1]: hardware dependent
 10: [ 0- 0]: hardware dependent
 11: [ 0]   : control

____________________________________________

/proc/asound/version
Advanced Linux Sound Architecture Driver Version 1.0.21.

____________________________________________

/proc/asound/timers
G0: system timer : 10000.000us (10000000 ticks)
P0-0-0: PCM playback 0-0-0 : SLAVE
P0-0-1: PCM capture 0-0-1 : SLAVE
P0-0-3: PCM capture 0-0-3 : SLAVE
P0-1-0: PCM playback 0-1-0 : SLAVE
P0-3-0: PCM playback 0-3-0 : SLAVE

____________________________________________

/proc/asound/hwdep
00-02: HDA Codec 2
00-01: HDA Codec 1
00-00: HDA Codec 0

____________________________________________

/proc/asound/card0/codec#0
Codec: IDT 92HD71B7X
Address: 0
Function Id: 0x1
Vendor Id: 0x111d76b2
Subsystem Id: 0x103c3603
Revision Id: 0x100302
No Modem Function Group found
Default PCM:
    rates [0x7e0]: 44100 48000 88200 96000 176400 192000
    bits [0xe]: 16 20 24
    formats [0x1]: PCM
Default Amp-In caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
Default Amp-Out caps: ofs=0x7f, nsteps=0x7f, stepsize=0x02, mute=1
GPIO: io=8, o=0, i=0, unsolicited=1, wake=1
  IO[0]: enable=1, dir=1, wake=0, sticky=0, data=1, unsol=0
  IO[1]: enable=0, dir=0, wake=0, sticky=0, data=0, unsol=0
  IO[2]: enable=0, dir=0, wake=0, sticky=0, data=0, unsol=0
  IO[3]: enable=0, dir=0, wake=0, sticky=0, data=0, unsol=0
  IO[4]: enable=0, dir=0, wake=0, sticky=0, data=0, unsol=0
  IO[5]: enable=0, dir=0, wake=0, sticky=0, data=0, unsol=0
  IO[6]: enable=0, dir=0, wake=0, sticky=0, data=0, unsol=0
  IO[7]: enable=0, dir=0, wake=0, sticky=0, data=0, unsol=0
Power-Map: 0x00
Analog Loopback: 0x00
Node 0x0a [Pin Complex] wcaps 0x400181: Stereo
  Pincap 0x0000001c: OUT HP Detect
  Pin Default 0x0221101f: [Jack] HP Out at Ext Front
    Conn = 1/8, Color = Black
    DefAssociation = 0x1, Sequence = 0xf
  Pin-ctls: 0xc0: OUT HP
  Unsolicited: tag=01, enabled=1
  Connection: 3
     0x10 0x11* 0x17
Node 0x0b [Pin Complex] wcaps 0x400081: Stereo
  Pincap 0x00001724: IN Detect
    Vref caps: HIZ 50 GRD 80
  Pin Default 0x02a11020: [Jack] Mic at Ext Front
    Conn = 1/8, Color = Black
    DefAssociation = 0x2, Sequence = 0x0
  Pin-ctls: 0x24: IN VREF_80
  Unsolicited: tag=03, enabled=1
Node 0x0c [Pin Complex] wcaps 0x400081: Stereo
  Pincap 0x00001724: IN Detect
    Vref caps: HIZ 50 GRD 80
  Pin Default 0x40f000f0: [N/A] Other at Ext N/A
    Conn = Unknown, Color = Unknown
    DefAssociation = 0xf, Sequence = 0x0
  Pin-ctls: 0x00: VREF_HIZ
  Unsolicited: tag=00, enabled=0
Node 0x0d [Pin Complex] wcaps 0x400181: Stereo
  Pincap 0x00000014: OUT Detect
  Pin Default 0x90170010: [Fixed] Speaker at Int N/A
    Conn = Analog, Color = Unknown
    DefAssociation = 0x1, Sequence = 0x0
  Pin-ctls: 0x00:
  Unsolicited: tag=00, enabled=0
  Connection: 3
     0x10* 0x11 0x17
Node 0x0e [Pin Complex] wcaps 0x400081: Stereo
  Pincap 0x00001724: IN Detect
    Vref caps: HIZ 50 GRD 80
  Pin Default 0x28a1102e: [Jack] Mic at Sep UNKNOWN
    Conn = 1/8, Color = Black
    DefAssociation = 0x2, Sequence = 0xe
  Pin-ctls: 0x24: IN VREF_80
  Unsolicited: tag=02, enabled=1
Node 0x0f [Pin Complex] wcaps 0x400181: Stereo
  Pincap 0x00000014: OUT Detect
  Pin Default 0x40f000f2: [N/A] Other at Ext N/A
    Conn = Unknown, Color = Unknown
    DefAssociation = 0xf, Sequence = 0x2
  Pin-ctls: 0x00:
  Unsolicited: tag=00, enabled=0
  Connection: 3
     0x10* 0x11 0x17
Node 0x10 [Audio Output] wcaps 0xd0c05: Stereo Amp-Out R/L
  Amp-Out caps: N/A
  Amp-Out vals:  [0x63 0x63]
  Converter: stream=5, channel=0
  Power: setting=D0, actual=D0
  Delay: 13 samples
Node 0x11 [Audio Output] wcaps 0xd0c05: Stereo Amp-Out R/L
  Amp-Out caps: N/A
  Amp-Out vals:  [0x63 0x63]
  Converter: stream=5, channel=0
  Power: setting=D0, actual=D0
  Delay: 13 samples
Node 0x12 [Audio Input] wcaps 0x1d0541: Stereo
  Converter: stream=0, channel=0
  SDI-Select: 0
  Power: setting=D3, actual=D3
  Delay: 13 samples
  Connection: 1
     0x1c
  Processing caps: benign=0, ncoeff=0
Node 0x13 [Audio Input] wcaps 0x1d0541: Stereo
  Converter: stream=0, channel=0
  SDI-Select: 0
  Power: setting=D3, actual=D3
  Delay: 13 samples
  Connection: 1
     0x1d
  Processing caps: benign=0, ncoeff=0
Node 0x14 [Pin Complex] wcaps 0x400100: Mono
  Pincap 0x00000010: OUT
  Pin Default 0x40f000f3: [N/A] Other at Ext N/A
    Conn = Unknown, Color = Unknown
    DefAssociation = 0xf, Sequence = 0x3
  Pin-ctls: 0x00:
  Connection: 1
     0x16
Node 0x15 [Audio Selector] wcaps 0x300101: Stereo
  Connection: 3
     0x10* 0x11 0x17
Node 0x16 [Audio Mixer] wcaps 0x200100: Mono
  Connection: 1
     0x15
Node 0x17 [Audio Mixer] wcaps 0x20010b: Stereo Amp-In
  Amp-In caps: ofs=0x17, nsteps=0x1f, stepsize=0x05, mute=1
  Amp-In vals:  [0x97 0x97] [0x97 0x97] [0x97 0x97] [0x97 0x97] [0x97 0x97]
  Connection: 5
     0x10 0x11 0x27 0x1a 0x1b
Node 0x18 [Pin Complex] wcaps 0x40000d: Stereo Amp-Out
  Amp-Out caps: ofs=0x00, nsteps=0x03, stepsize=0x27, mute=0
  Amp-Out vals:  [0x00 0x00]
  Pincap 0x00000020: IN
  Pin Default 0x90a60370: [Fixed] Mic at Int N/A
    Conn = Digital, Color = Unknown
    DefAssociation = 0x7, Sequence = 0x0
    Misc = NO_PRESENCE
  Pin-ctls: 0x20: IN
Node 0x19 [Pin Complex] wcaps 0x40000d: Stereo Amp-Out
  Amp-Out caps: ofs=0x00, nsteps=0x03, stepsize=0x27, mute=0
  Amp-Out vals:  [0x00 0x00]
  Pincap 0x00000020: IN
  Pin Default 0x40f000f5: [N/A] Other at Ext N/A
    Conn = Unknown, Color = Unknown
    DefAssociation = 0xf, Sequence = 0x5
  Pin-ctls: 0x00:
Node 0x1a [Audio Selector] wcaps 0x30010d: Stereo Amp-Out
  Amp-Out caps: ofs=0x00, nsteps=0x03, stepsize=0x27, mute=0
  Amp-Out vals:  [0x00 0x00]
  Connection: 3
     0x0b* 0x0c 0x0e
Node 0x1b [Audio Selector] wcaps 0x30010d: Stereo Amp-Out
  Amp-Out caps: ofs=0x00, nsteps=0x03, stepsize=0x27, mute=0
  Amp-Out vals:  [0x00 0x00]
  Connection: 3
     0x0b 0x0c 0x0e*
Node 0x1c [Audio Selector] wcaps 0x30090d: Stereo Amp-Out R/L
  Amp-Out caps: ofs=0x00, nsteps=0x0f, stepsize=0x05, mute=1
  Amp-Out vals:  [0x0c 0x0c]
  Connection: 4
     0x1a 0x17 0x18* 0x19
Node 0x1d [Audio Selector] wcaps 0x30090d: Stereo Amp-Out R/L
  Amp-Out caps: ofs=0x00, nsteps=0x0f, stepsize=0x05, mute=1
  Amp-Out vals:  [0x80 0x80]
  Connection: 4
     0x1b* 0x17 0x18 0x19
Node 0x1e [Pin Complex] wcaps 0x400301: Stereo Digital
  Pincap 0x00000010: OUT
  Pin Default 0x214410a0: [Jack] SPDIF Out at Sep Rear
    Conn = RCA, Color = Black
    DefAssociation = 0xa, Sequence = 0x0
  Pin-ctls: 0x40: OUT
  Connection: 1
     0x24
Node 0x1f [Pin Complex] wcaps 0x400701: Stereo Digital
  Pincap 0x00010010: OUT EAPD
  EAPD 0x0:
  Pin Default 0x40f100f5: [N/A] Other at Ext N/A
    Conn = 1/8, Color = Unknown
    DefAssociation = 0xf, Sequence = 0x5
  Pin-ctls: 0x00:
  Power: setting=D0, actual=D0
  Connection: 2
     0x24* 0x25
Node 0x20 [Pin Complex] wcaps 0x400301: Stereo Digital
  Pincap 0x00000010: OUT
  Pin Default 0x40f100f6: [N/A] Other at Ext N/A
    Conn = 1/8, Color = Unknown
    DefAssociation = 0xf, Sequence = 0x6
  Pin-ctls: 0x00:
  Connection: 1
     0x25
Node 0x21 [Audio Output] wcaps 0x40211: Stereo Digital
  Converter: stream=5, channel=0
  Digital: Enabled
  Digital category: 0x0
  PCM:
    rates [0x7e0]: 44100 48000 88200 96000 176400 192000
    bits [0xe]: 16 20 24
    formats [0x5]: PCM AC3
  Delay: 4 samples
Node 0x22 [Audio Output] wcaps 0x40211: Stereo Digital
  Converter: stream=5, channel=0
  Digital: Enabled
  Digital category: 0x0
  PCM:
    rates [0x7e0]: 44100 48000 88200 96000 176400 192000
    bits [0xe]: 16 20 24
    formats [0x5]: PCM AC3
  Delay: 4 samples
Node 0x23 [Vendor Defined Widget] wcaps 0xf00000: Mono
Node 0x24 [Audio Selector] wcaps 0x300101: Stereo
  Connection: 3
     0x21* 0x1c 0x1d
Node 0x25 [Audio Selector] wcaps 0x300101: Stereo
  Connection: 3
     0x22* 0x1c 0x1d
Node 0x26 [Beep Generator Widget] wcaps 0x70000c: Mono Amp-Out
  Amp-Out caps: ofs=0x03, nsteps=0x03, stepsize=0x17, mute=1
  Amp-Out vals:  [0x00]
Node 0x27 [Pin Complex] wcaps 0x400000: Mono
  Pincap 0x00000020: IN
  Pin Default 0x40f000f7: [N/A] Other at Ext N/A
    Conn = Unknown, Color = Unknown
    DefAssociation = 0xf, Sequence = 0x7
  Pin-ctls: 0x00:
Node 0x28 [Volume Knob Widget] wcaps 0x600000: Mono
  Volume-Knob: delta=1, steps=127, direct=1, val=127
  Connection: 2
     0x10 0x11

____________________________________________

/proc/asound/card0/codec#1
Codec: LSI ID 1040
Address: 1
Function Id: 0x2
Vendor Id: 0x11c11040
Subsystem Id: 0x103c137e
Revision Id: 0x100200
Modem Function Group: 0x1

____________________________________________

/proc/asound/card0/codec#2
Codec: Nvidia MCP78 HDMI
Address: 2
Function Id: 0x1
Vendor Id: 0x10de0006
Subsystem Id: 0x10de0101
Revision Id: 0x100000
No Modem Function Group found
Default PCM:
    rates [0x0]:
    bits [0x0]:
    formats [0x0]:
Default Amp-In caps: N/A
Default Amp-Out caps: N/A
GPIO: io=0, o=0, i=0, unsolicited=0, wake=0
Node 0x04 [Audio Output] wcaps 0x211: Stereo Digital
  Converter: stream=0, channel=0
  Digital:
  Digital category: 0x0
  PCM:
    rates [0xc0]: 48000 88200
    bits [0xf]: 8 16 20 24
    formats [0x1]: PCM
Node 0x05 [Pin Complex] wcaps 0x400381: Stereo Digital
  Pincap 0x00000014: OUT Detect
  Pin Default 0x18560110: [Jack] Digital Out at Int HDMI
    Conn = Digital, Color = Unknown
    DefAssociation = 0x1, Sequence = 0x0
    Misc = NO_PRESENCE
  Pin-ctls: 0x40: OUT
  Unsolicited: tag=00, enabled=0
  Connection: 1
     0x04
Node 0x06 [Audio Output] wcaps 0x211: Stereo Digital
  Converter: stream=0, channel=0
  Digital:
  Digital category: 0x0
  PCM:
    rates [0xc0]: 48000 88200
    bits [0xf]: 8 16 20 24
    formats [0x1]: PCM
Node 0x07 [Pin Complex] wcaps 0x400381: Stereo Digital
  Pincap 0x00000014: OUT Detect
  Pin Default 0x58560121: [N/A] Digital Out at Int HDMI
    Conn = Digital, Color = Unknown
    DefAssociation = 0x2, Sequence = 0x1
    Misc = NO_PRESENCE
  Pin-ctls: 0x40: OUT
  Unsolicited: tag=00, enabled=0
  Connection: 1
     0x06
Node 0x08 [Audio Output] wcaps 0x211: Stereo Digital
  Converter: stream=0, channel=0
  Digital:
  Digital category: 0x0
  PCM:
    rates [0xc0]: 48000 88200
    bits [0xf]: 8 16 20 24
    formats [0x1]: PCM
Node 0x09 [Pin Complex] wcaps 0x400381: Stereo Digital
  Pincap 0x00000014: OUT Detect
  Pin Default 0x58560122: [N/A] Digital Out at Int HDMI
    Conn = Digital, Color = Unknown
    DefAssociation = 0x2, Sequence = 0x2
    Misc = NO_PRESENCE
  Pin-ctls: 0x40: OUT
  Unsolicited: tag=00, enabled=0
  Connection: 1
     0x08
Node 0x0a [Audio Output] wcaps 0x211: Stereo Digital
  Converter: stream=0, channel=0
  Digital:
  Digital category: 0x0
  PCM:
    rates [0xc0]: 48000 88200
    bits [0xf]: 8 16 20 24
    formats [0x1]: PCM
Node 0x0b [Pin Complex] wcaps 0x400381: Stereo Digital
  Pincap 0x00000014: OUT Detect
  Pin Default 0x58560123: [N/A] Digital Out at Int HDMI
    Conn = Digital, Color = Unknown
    DefAssociation = 0x2, Sequence = 0x3
    Misc = NO_PRESENCE
  Pin-ctls: 0x40: OUT
  Unsolicited: tag=00, enabled=0
  Connection: 1
     0x0a
Node 0x0c [Audio Output] wcaps 0x211: Stereo Digital
  Converter: stream=0, channel=0
  Digital:
  Digital category: 0x0
  PCM:
    rates [0xc0]: 48000 88200
    bits [0xf]: 8 16 20 24
    formats [0x1]: PCM
Node 0x0d [Pin Complex] wcaps 0x400381: Stereo Digital
  Pincap 0x00000014: OUT Detect
  Pin Default 0x58560124: [N/A] Digital Out at Int HDMI
    Conn = Digital, Color = Unknown
    DefAssociation = 0x2, Sequence = 0x4
    Misc = NO_PRESENCE
  Pin-ctls: 0x40: OUT
  Unsolicited: tag=00, enabled=0
  Connection: 1
     0x0c

____________________________________________

End of NVIDIA bug report log file.
```

---

