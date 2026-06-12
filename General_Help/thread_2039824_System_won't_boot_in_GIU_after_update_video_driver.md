---
title: "System won't boot in GIU after update video driver"
date: 2012-08-09
forum: General Help
---

### Post by Jimboland on 2012-08-09
Yesterday I was expermenting with my nvidia GPU settings in the nvidia control panel, trying to see if I could improve something. 

But after my first reboot I noticed that my mouse cursor was not following the movement of my mouse anymore and video's on youtube were not playing smoothly.
So I decided to upgrade my video driver with the original drivers of the nvidia website for the gt520 gpu.

After I screwed that up by entering

sudo apt-get purge remove --nvidia* -y && sh nvidiafile.run

I ended up with a non working system that wouldn't even display the text from the console anymore. So it was completely beyond repair for me.

Today I re-installed everything and found out that Ubuntu 12.04 doesn't display anything after the first boot screen disapears. So normally when u see the installer screen "welcome to ubuntu, what do you want to do" the screen went black.
So I had to install 11.10 first, and then upgrade to 12.04.

I did that, installed some of my programs and later the same problem, animations started to become sluggish.
So I try to install the video drivers again, everything go's well until I want to to start x, and I can't.

This time I am able to use the console, and I spend several hours  to found a solution, but I don't know what to do.

I copied to log file's to a usb key, but I don't know what to look for. 

So if somebody could guide me to the solution of this horrible nvidia problem, I would be thankful!


PS: I'm starting to understand Linus's [frustration]("http://www.youtube.com/watch?v=IVpOyKCNZYw") with nvidia:)


Nvidia-installer log file:

[I]nvidia-installer log file '/var/log/nvidia-installer.log'
creation time: Thu Aug  9 18:18:16 2012
installer version: 295.71

PATH: /usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin

nvidia-installer command line:
    ./nvidia-installer

Using: nvidia-installer ncurses user interface
-> License accepted.
-> Installing NVIDIA driver version 295.71.
-> Running distribution scripts
   executing: '/usr/lib/nvidia/pre-install'...
-> done.
-> The distribution-provided pre-install script failed!  Continue installation anyway? (Answer: Yes)
-> Performing CC sanity check with CC="cc".
-> Performing CC version check with CC="cc".
-> Kernel source path: '/lib/modules/3.2.0-27-generic/build'
-> Kernel output path: '/lib/modules/3.2.0-27-generic/build'
-> Performing rivafb check.
-> Performing nvidiafb check.
-> Performing Xen check.
-> Cleaning kernel module build directory.
   executing: 'cd ./kernel; make clean'...
-> Building kernel module:
   executing: 'cd ./kernel; make module SYSSRC=/lib/modules/3.2.0-27-generic/build SYSOUT=/lib/modules/3.2.0-27-generic/build'...
   NVIDIA: calling KBUILD...
   test -e include/generated/autoconf.h -a -e include/config/auto.conf || (		\
   	echo;								\
   	echo "  ERROR: Kernel configuration is invalid.";		\
   	echo "         include/generated/autoconf.h or include/config/auto.conf are missing.";\
   	echo "         Run 'make oldconfig && make prepare' on kernel src to fix it.";	\
   	echo;								\
   	/bin/false)
   mkdir -p /tmp/selfgz1809/NVIDIA-Linux-x86_64-295.71/kernel/.tmp_versions ; rm -f /tmp/selfgz1809/NVIDIA-Linux-x86_64-295.71/kernel/.tmp_versions/*
   make -f scripts/Makefile.build obj=/tmp/selfgz1809/NVIDIA-Linux-x86_64-295.71/kernel
     cc -Wp,-MD,/tmp/selfgz1809/NVIDIA-Linux-x86_64-295.71/kernel/.nv.o.d  -nostdinc -isystem /usr/lib/gcc/x86_64-linux-gnu/4.6/include  -I/usr/src/linux-headers-3.2.0-27-generic/arch/x86/include -Iarch/x86/include/generated -Iinclude  -include /usr/src/linux-headers-3.2.0-27-generic/include/linux/kconfig.h -Iubuntu/include  -D__KERNEL__ -Wall -Wundef -Wstrict-prototypes -Wno-trigraphs -fno-strict-aliasing -fno-common 
   -Werror-implicit-function-declaration -Wno-format-security -fno-delete-null-pointer-checks -O2 -m64 -mtune=generic -mno-red-zone -mcmodel=kernel -funit-at-a-time -maccumulate-outgoing-args -fstack-protector -DCONFIG_AS_CFI=1 -DCONFIG_AS_CFI_SIGNAL_FRAME=1 -DCONFIG_AS_CFI_SECTIONS=1 -DCONFIG_AS_FXSAVEQ=1 -pipe -Wno-sign-compare -fno-asynchronous-unwind-tables -mno-sse -mno-mmx -mno-sse2 -mno-3dnow -Wframe-larger-than=1024 -Wno-unused-but-set-variable -fno-omit-frame-pointer -fno-optimize-sibling-calls -pg -Wdeclaration-after-statement -Wno-pointer-sign -fno-strict-overflow -fconserve-stack -DCC_HAVE_ASM_GOTO -I/tmp/selfgz1809/NVIDIA-Linux-x86_64-295.71/kernel -Wall -MD -Wsign-compare -Wno-cast-qual -Wno-error -D__KERNEL__ -DMODULE -DNVRM -DNV_VERSION_STRING=\"295.71\" -Wno-unused-function -Wuninitialized -mno-red-zone -mcmodel=kernel -UDEBUG -U_DEBUG -DNDEBUG  -DMODULE  -D"KBUILD_STR(s)=#s" -D"KBUILD_BASENAME=KBUILD_STR(nv)"  -D"KBUILD_MODNAME=KBUILD_STR(nvidia)" -c -o /tmp/selfgz1809/NVIDIA-Linux-x86_64-295.7
   1/kernel/.tmp_nv.o /tmp/selfgz1809/NVIDIA-Linux-x86_64-295.71/kernel/nv.c
   In file included from include/linux/kernel.h:17:0,
                    from include/linux/sched.h:55,
                    from include/linux/utsname.h:35,
                    from /tmp/selfgz1809/NVIDIA-Linux-x86_64-295.71/kernel/nv-linux.h:38,
                    from /tmp/selfgz1809/NVIDIA-Linux-x86_64-295.71/kernel/nv.c:13:
   include/linux/bitops.h: In function &#8216;hweight_long&#8217;:
   include/linux/bitops.h:49:41: warning: signed and unsigned type in conditional expression [-Wsign-compare]
   In file included from /usr/src/linux-headers-3.2.0-27-generic/arch/x86/include/asm/uaccess.h:575:0,
                    from include/linux/poll.h:14,
                    from /tmp/selfgz1809/NVIDIA-Linux-x86_64-295.71/kernel/nv-linux.h:97,
                    from /tmp/selfgz1809/NVIDIA-Linux-x86_64-295.71/kernel/nv.c:13:
   /usr/src/linux-headers-3.2.0-27-generic/arch/x86/include/asm/uaccess_64.h: In function &#8216;copy_from_user&#8217;:
   /usr/src/linux-headers-3.2.0-27-generic/arch/x86/include/asm/uaccess_64.h:53:6: warning: comparison between signed and unsigned integer expressions [-Wsign-compare]
     if [ "-pg" = "-pg" ]; then if [ /tmp/selfgz1809/NVIDIA-Linux-x86_64-295.71/kernel/nv.o != "scripts/mod/empty.o" ]; then /usr/src/linux-headers-3.2.0-27-generic/scripts/recordmcount  "/tmp/selfgz1809/NVIDIA-Linux-x86_64-295.71/kernel/nv.o"; fi; fi;
     cc -Wp,-MD,/tmp/selfgz1809/NVIDIA-Linux-x86_64-295.71/kernel/.nv-acpi.o.d  -nostdinc -isystem /usr/lib/gcc/x86_64-linux-gnu/4.6/include  -I/usr/src/linux-headers-3.2.0-27-generic/arch/x86/include -Iarch/x86/include/generated -Iinclude  -include /usr/src/linux-headers-3.2.0-27-generic/include/linux/kconfig.h -Iubuntu/include  -D__KERNEL__ -Wall -Wundef -Wstrict-prototypes -Wno-trigraphs -fno-strict-aliasing -fno-common -Werror-implicit-function-declaration -Wno-format-security -fno-delete-null-pointer-checks -O2 -m64 -mtune=generic -mno-red-zone -mcmodel=kernel -funit-at-a-time -maccumulate-outgoing-args -fstack-protector -DCONFIG_AS_CFI=1 -DCONF
   IG_AS_CFI_SIGNAL_FRAME=1 -DCONFIG_AS_CFI_SECTIONS=1 -DCONFIG_AS_FXSAVEQ=1 -pipe -Wno-sign-compare -fno-asynchronous-unwind-tables -mno-sse -mno-mmx -mno-sse2 -mno-3dnow -Wframe-larger-than=1024 -Wno-unused-but-set-variable -fno-omit-frame-pointer -fno-optimize-sibling-calls -pg -Wdeclaration-after-statement -Wno-pointer-sign -fno-strict-overflow -fconserve-stack -DCC_HAVE_ASM_GOTO -I/tmp/selfgz1809/NVIDIA-Linux-x86_64-295.71/kernel -Wall -MD -Wsign-compare -Wno-cast-qual -Wno-error -D__KERNEL__ -DMODULE -DNVRM -DNV_VERSION_STRING=\"295.71\" -Wno-unused-function -Wuninitialized -mno-red-zone -mcmodel=kernel -UDEBUG -U_DEBUG -DNDEBUG  -DMODULE  -D"KBUILD_STR(s)=#s" -D"KBUILD_BASENAME=KBUILD_STR(nv_acpi)"  -D"KBUILD_MODNAME=KBUILD_STR(nvidia)" -c -o /tmp/selfgz1809/NVIDIA-Linux-x86_64-295.71/kernel/.tmp_nv-acpi.o /tmp/selfgz1809/NVIDIA-Linux-x86_64-295.71/kernel/nv-acpi.c
   In file included from include/linux/kernel.h:17:0,
                    from include/linux/sched.h:55,
                    from include/linux/utsname.h:35,
                    from /tmp/selfgz1809/NVIDIA-Linux-x86_64-295.71/kernel/nv-linux.h:38,
                    from /tmp/selfgz1809/NVIDIA-Linux-x86_64-295.71/kernel/nv-acpi.c:15:
   include/linux/bitops.h: In function &#8216;hweight_long&#8217;:
   include/linux/bitops.h:49:41: warning: signed and unsigned type in conditional expression [-Wsign-compare]
   In file included from /usr/src/linux-headers-3.2.0-27-generic/arch/x86/include/asm/uaccess.h:575:0,
                    from include/linux/poll.h:14,
                    from /tmp/selfgz1809/NVIDIA-Linux-x86_64-295.71/kernel/nv-linux.h:97,
                    from /tmp/selfgz1809/NVIDIA-Linux-x86_64-295.71/kernel/nv-acpi.c:15:
   /usr/src/linux-headers-3.2.0-27-generic/arch/x86/include/asm/uaccess_64.h: In function &#8216;copy_from_user&#8217;:
   /usr/src/linux-headers-3.2.0-27-generic/arch/x86/include/asm/uaccess_64.h:53:6: warning: comparison between signed and unsigned integer expressions [-Wsign-compare]
     if [ "-pg" = "-pg" ]; then if [ /tmp/selfgz1809/NVIDIA-Linux-x86_64-295.71/kernel/nv-acpi.o != "scripts/mod/empty.o" ]; then /usr/src/linux-headers-3.2.0-27-generic/scripts/recordmcount  "/tmp/selfgz1809/NVIDIA-Linux-x86_64-295.71/kernel/nv-acpi.o"; fi; fi;
     cc -Wp,-MD,/tmp/selfgz1809/NVIDIA-Linux-x86_64-295.71/kernel/.nv-chrdev.o.d  -nostdinc -isystem /usr/lib/gcc/x86_64-linux-gnu/4.6/include  -I/usr/src/linux-headers-3.2.0-27-generic/arch/x86/include -Iarch/x86/include/generated -Iinclude  -include /usr/src/linux-headers-3.2.0-27-generic/include/linux/kconfig.h -Iubuntu/include  -D__KERNEL__ -Wall -Wundef -Wstrict-prototypes -Wno-trigraphs -fno-strict-aliasing -fno-common -Werror-implicit-function-declaration -Wno-format-security -fno-delete-null-pointer-checks -O2 -m64 -mtune=generic -mno-red-zone -mcmodel=kernel -funit-at-a-time -maccumulate-outgoing-args -fstack-protector -DCONFIG_AS_CFI=1 -DCONFIG_AS_CFI_SIGNAL_FRAME=1 -DCONFIG_AS_CFI_SECTIONS=1 -DCONFIG_AS_FXSAVEQ=1 -pipe -Wno-sign-compare -fno-asynchronous-unwind-tables -mno-sse -mno-mmx -mno-sse2 -mno-3dnow -Wframe-larger-than=1024 
   -Wno-unused-but-set-variable -fno-omit-frame-pointer -fno-optimize-sibling-calls -pg -Wdeclaration-after-statement -Wno-pointer-sign -fno-strict-overflow -fconserve-stack -DCC_HAVE_ASM_GOTO -I/tmp/selfgz1809/NVIDIA-Linux-x86_64-295.71/kernel -Wall -MD -Wsign-compare -Wno-cast-qual -Wno-error -D__KERNEL__ -DMODULE -DNVRM -DNV_VERSION_STRING=\"295.71\" -Wno-unused-function -Wuninitialized -mno-red-zone -mcmodel=kernel -UDEBUG -U_DEBUG -DNDEBUG  -DMODULE  -D"KBUILD_STR(s)=#s" -D"KBUILD_BASENAME=KBUILD_STR(nv_chrdev)"  -D"KBUILD_MODNAME=KBUILD_STR(nvidia)" -c -o /tmp/selfgz1809/NVIDIA-Linux-x86_64-295.71/kernel/.tmp_nv-chrdev.o /tmp/selfgz1809/NVIDIA-Linux-x86_64-295.71/kernel/nv-chrdev.c
   In file included from include/linux/kernel.h:17:0,
                    from include/linux/sched.h:55,
                    from include/linux/utsname.h:35,
                    from /tmp/selfgz1809/NVIDIA-Linux-x86_64-295.71/kernel/nv-linux.h:38,
                    from /tmp/selfgz1809/NVIDIA-Linux-x86_64-295.71/kernel/nv-chrdev.c:15:
   include/linux/bitops.h: In function &#8216;hweight_long&#8217;:
   include/linux/bitops.h:49:41: warning: signed and unsigned type in conditional expression [-Wsign-compare]
   In file included from /usr/src/linux-headers-3.2.0-27-generic/arch/x86/include/asm/uaccess.h:575:0,
                    from include/linux/poll.h:14,
                    from /tmp/selfgz1809/NVIDIA-Linux-x86_64-295.71/kernel/nv-linux.h:97,
                    from /tmp/selfgz1809/NVIDIA-Linux-x86_64-295.71/kernel/nv-chrdev.c:15:
   /usr/src/linux-headers-3.2.0-27-generic/arch/x86/include/asm/uaccess_64.h: In function &#8216;copy_from_user&#8217;:
   /usr/src/linux-headers-3.2.0-27-generic/arch/x86/include/asm/uaccess_64.h:53:6: warning: comparison between signed and unsigned integer expressions [-Wsign-compare]
     if [ "-pg" = "-pg" ]; then if [ /tmp/selfgz1809/NVIDIA-Linux-x86_64-295.71/kernel/nv-chrdev.o != "scripts/mod/empty.o" ]; then /usr/src/linux-headers-3.2.0-27-generic/scripts/recordmcount  "/tmp/selfgz1809/NVIDIA-Linux-x86_64-295.71/kernel/nv-chrdev.o"; fi; fi;
     cc -Wp,-MD,/tmp/selfgz1809/NVIDIA-Linux-x86_64-295.71/kernel/.nv-cray.o.d  -nostdinc -isystem /usr/lib/gcc/x86_64-linux-gnu/4.6/include  -I/usr/src/linux-headers-3.2.0-27-generic/arch/x86/include -Iarch/x86/include/generated -Iinclude  -include /usr/src/linux-headers-3.2.0-27-generic/include/linux/kconfig.h -Iubuntu/include  -D__KERNEL__ -Wall -Wundef -Wstrict-prototypes -Wno-trigraphs -fno-strict-aliasing -fno-common -Werror-implicit-function-declaration -Wno-format-security -fno-delete-null-pointer-checks -O2 -m64 -mtune=generic -mno-red-zone -mcmodel=kernel -funit-at-a-time -maccumulate-outgoing-args -fstack-protector -DCONFIG_AS_CFI=1 -DCONFIG_AS_CFI_SIGNAL_FRAME=1 -DCONFIG_AS_CFI_SECTIONS=1 -DCONFIG_AS_FXSAVEQ=1 -pipe -Wno-sign-compare -fno-asynchronous-unwind-tables -mno-sse -mno-mmx -mno-sse2 -mno-3dnow -Wframe-larger-than=1024 -Wno-unused-but-set-variable -fno-omit-frame-pointer -fno-optimize-sibling-calls -pg -Wdeclaration-after-statement -Wno-pointer-sign -fno-strict-overflow -fconserve-stack -DCC_HAVE_A
   SM_GOTO -I/tmp/selfgz1809/NVIDIA-Linux-x86_64-295.71/kernel -Wall -MD -Wsign-compare -Wno-cast-qual -Wno-error -D__KERNEL__ -DMODULE -DNVRM -DNV_VERSION_STRING=\"295.71\" -Wno-unused-function -Wuninitialized -mno-red-zone -mcmodel=kernel -UDEBUG -U_DEBUG -DNDEBUG  -DMODULE  -D"KBUILD_STR(s)=#s" -D"KBUILD_BASENAME=KBUILD_STR(nv_cray)"  -D"KBUILD_MODNAME=KBUILD_STR(nvidia)" -c -o /tmp/selfgz1809/NVIDIA-Linux-x86_64-295.71/kernel/.tmp_nv-cray.o /tmp/selfgz1809/NVIDIA-Linux-x86_64-295.71/kernel/nv-cray.c
   In file included from include/linux/kernel.h:17:0,
                    from include/linux/sched.h:55,
                    from include/linux/utsname.h:35,
                    from /tmp/selfgz1809/NVIDIA-Linux-x86_64-295.71/kernel/nv-linux.h:38,
                    from /tmp/selfgz1809/NVIDIA-Linux-x86_64-295.71/kernel/nv-cray.c:15:
   include/linux/bitops.h: In function &#8216;hweight_long&#8217;:
   include/linux/bitops.h:49:41: warning: signed and unsigned type in conditional expression [-Wsign-compare]
   In file included from /usr/src/linux-headers-3.2.0-27-generic/arch/x86/include/asm/uaccess.h:575:0,
                    from include/linux/poll.h:14,
                    from /tmp/selfgz1809/NVIDIA-Linux-x86_64-295.71/kernel/nv-linux.h:97,
                    from /tmp/selfgz1809/NVIDIA-Linux-x86_64-295.71/kernel/nv-cray.c:15:
   /usr/src/linux-headers-3.2.0-27-generic/arch/x86/include/asm/uaccess_64.h: In function &#8216;copy_from_user&#8217;:
   /usr/src/linux-headers-3.2.0-27-generic/arch/x86/include/asm/uaccess_64.h:53:6: warning: comparison between signed and unsigned integer expressions [-Wsign-compare]
     if [ "-pg" = "-pg" ]; then if [ /tmp/selfgz1809/NVIDIA-Linux-x86_64-295.71/kernel/nv-cray.o != "scripts/mod/empty.o" ]; then /usr/src/linux-headers-3.2.0-27-generic/scripts/recordmcount  "/tmp/selfgz1809/NVIDIA-Linux-x86_64-295.71/kernel/nv-cray.o"; fi; fi;
     cc -Wp,-MD,/tmp/selfgz1809/NVIDIA-Linux-x86_64-295.71/kernel/.nv-gvi.o.d  -nostdinc -isystem /usr/lib/gcc/x86_64-linux-gnu/4.6/include  -I/usr/src/linux-headers-3.2.0-27-generic/arch/x86/include -Iarch/x86/include/generated -Iinclude  -include /usr/src/linux-headers-3.2.0-27-generic/include/linux/kconfig.h -Iubuntu/include  -D__KERNEL__ -Wall -Wundef -Wstrict-prototypes -Wno-trigraphs -fno-strict-aliasing -fno-common -Werror-implicit-function-declaration -Wno-format-security -fno-delete-null-pointer-checks -O2 -m64 -mtune=generic -mno-red-zone -mcmodel=kernel -funit-at-a-time -maccumulate-outgoing-args -fstack-protector -DCONFIG_AS_CFI=1 -DCONFIG_AS_CFI_SIGNAL_FRAME=1 -DCONFIG_AS_CFI_SECTIONS=1 -DCONFIG_AS_FXSAVEQ=1 -pipe -Wno-sign-compare -fno-asynchronous-unwind-tables -mno-sse -mno-mmx -mno-sse2 -mno-3dnow -Wframe-larger-than=1024 -Wno-unused-but-set-variable -fno-omit-frame-pointer -fno-optimize-sibling-calls -pg -Wdeclaration-after-statement -Wno-pointer-sign -fno-strict-overflow -fconserve-stack -DCC_HAVE_ASM_GOTO -I/tmp/selfgz1809/NVIDIA-Linux-x86_64-295.71/kernel -Wall -MD -Wsign-compare -Wno-cast-qual -Wno-error -D__KERNEL__ -DMODULE -DNVRM -DNV_VERSION_STRING=\"295.71\" -Wno-unused-function -Wuni
   nitialized -mno-red-zone -mcmodel=kernel -UDEBUG -U_DEBUG -DNDEBUG  -DMODULE  -D"KBUILD_STR(s)=#s" -D"KBUILD_BASENAME=KBUILD_STR(nv_gvi)"  -D"KBUILD_MODNAME=KBUILD_STR(nvidia)" -c -o /tmp/selfgz1809/NVIDIA-Linux-x86_64-295.71/kernel/.tmp_nv-gvi.o /tmp/selfgz1809/NVIDIA-Linux-x86_64-295.71/kernel/nv-gvi.c
   In file included from include/linux/kernel.h:17:0,
                    from include/linux/sched.h:55,
                    from include/linux/utsname.h:35,
                    from /tmp/selfgz1809/NVIDIA-Linux-x86_64-295.71/kernel/nv-linux.h:38,
                    from /tmp/selfgz1809/NVIDIA-Linux-x86_64-295.71/kernel/nv-gvi.c:15:
   include/linux/bitops.h: In function &#8216;hweight_long&#8217;:
   include/linux/bitops.h:49:41: warning: signed and unsigned type in conditional expression [-Wsign-compare]
   In file included from /usr/src/linux-headers-3.2.0-27-generic/arch/x86/include/asm/uaccess.h:575:0,
                    from include/linux/poll.h:14,
                    from /tmp/selfgz1809/NVIDIA-Linux-x86_64-295.71/kernel/nv-linux.h:97,
                    from /tmp/selfgz1809/NVIDIA-Linux-x86_64-295.71/kernel/nv-gvi.c:15:
   /usr/src/linux-headers-3.2.0-27-generic/arch/x86/include/asm/uaccess_64.h: In function &#8216;copy_from_user&#8217;:
   /usr/src/linux-headers-3.2.0-27-generic/arch/x86/include/asm/uaccess_64.h:53:6: warning: comparison between signed and unsigned integer expressions [-Wsign-compare]
     if [ "-pg" = "-pg" ]; then if [ /tmp/selfgz1809/NVIDIA-Linux-x86_64-295.71/kernel/nv-gvi.o != "scripts/mod/empty.o" ]; then /usr/src/linux-headers-3.2.0-27-generic/scripts/recordmcount  "/tmp/selfgz1809/NVIDIA-Linux-x86_64-295.71/kernel/nv-gvi.o"; fi; fi;
     cc -Wp,-MD,/tmp/selfgz1809/NVIDIA-Linux-x86_64-295.71/kernel/.nv-i2c.o.d  -nostdinc -isystem /usr/lib/gcc/x86_64-linux-gnu/4.6/include  -I/usr/src/linux-headers-3.2.0-27-generic/arch/x86/include -Iarch/x86/include/generated -Iinclude  -include /usr/src/linux-headers-3.2.0-27-generic/include/linux/kconfig.h -Iubuntu/include  -D__KERNEL__ -Wall -Wundef -Wstrict-prototypes -Wno-trigraphs -fno-strict-alias
   ing -fno-common -Werror-implicit-function-declaration -Wno-format-security -fno-delete-null-pointer-checks -O2 -m64 -mtune=generic -mno-red-zone -mcmodel=kernel -funit-at-a-time -maccumulate-outgoing-args -fstack-protector -DCONFIG_AS_CFI=1 -DCONFIG_AS_CFI_SIGNAL_FRAME=1 -DCONFIG_AS_CFI_SECTIONS=1 -DCONFIG_AS_FXSAVEQ=1 -pipe -Wno-sign-compare -fno-asynchronous-unwind-tables -mno-sse -mno-mmx -mno-sse2 -mno-3dnow -Wframe-larger-than=1024 -Wno-unused-but-set-variable -fno-omit-frame-pointer -fno-optimize-sibling-calls -pg -Wdeclaration-after-statement -Wno-pointer-sign -fno-strict-overflow -fconserve-stack -DCC_HAVE_ASM_GOTO -I/tmp/selfgz1809/NVIDIA-Linux-x86_64-295.71/kernel -Wall -MD -Wsign-compare -Wno-cast-qual -Wno-error -D__KERNEL__ -DMODULE -DNVRM -DNV_VERSION_STRING=\"295.71\" -Wno-unused-function -Wuninitialized -mno-red-zone -mcmodel=kernel -UDEBUG -U_DEBUG -DNDEBUG  -DMODULE  -D"KBUILD_STR(s)=#s" -D"KBUILD_BASENAME=KBUILD_STR(nv_i2c)"  -D"KBUILD_MODNAME=KBUILD_STR(nvidia)" -c -o /tmp/selfgz1809/NVIDI
   A-Linux-x86_64-295.71/kernel/.tmp_nv-i2c.o /tmp/selfgz1809/NVIDIA-Linux-x86_64-295.71/kernel/nv-i2c.c
   In file included from include/linux/kernel.h:17:0,
                    from include/linux/sched.h:55,
                    from include/linux/utsname.h:35,
                    from /tmp/selfgz1809/NVIDIA-Linux-x86_64-295.71/kernel/nv-linux.h:38,
                    from /tmp/selfgz1809/NVIDIA-Linux-x86_64-295.71/kernel/nv-i2c.c:15:
   include/linux/bitops.h: In function &#8216;hweight_long&#8217;:
   include/linux/bitops.h:49:41: warning: signed and unsigned type in conditional expression [-Wsign-compare]
   In file included from /usr/src/linux-headers-3.2.0-27-generic/arch/x86/include/asm/uaccess.h:575:0,
                    from include/linux/poll.h:14,
                    from /tmp/selfgz1809/NVIDIA-Linux-x86_64-295.71/kernel/nv-linux.h:97,
                    from /tmp/selfgz1809/NVIDIA-Linux-x86_64-295.71/kernel/nv-i2c.c:15:
   /usr/src/linux-headers-3.2.0-27-generic/arch/x86/include/asm/uaccess_64.h: In function &#8216;copy_from_user&#8217;:
   /usr/src/linux-headers-3.2.0-27-generic/arch/x86/include/asm/uaccess_64.h:53:6: warning: comparison between signed and unsigned integer expressions [-Wsign-compare]
     if [ "-pg" = "-pg" ]; then if [ /tmp/selfgz1809/NVIDIA-Linux-x86_64-295.71/kernel/nv-i2c.o != "scripts/mod/empty.o" ]; then /usr/src/linux-headers-3.2.0-27-generic/scripts/recordmcount  "/tmp/selfgz1809/NVIDIA-Linux-x86_64-295.71/kernel/nv-i2c.o"; fi; fi;
     cc -Wp,-MD,/tmp/selfgz1809/NVIDIA-Linux-x86_64-295.71/kernel/.nv-mempool.o.d  -nostdinc -isystem /usr/lib/gcc/x86_64-linux-gnu/4.6/include  -I/usr/src/linux-headers-3.2.0-27-generic/arch/x86/include -Iarch/x86/include/generated -Iinclude  -include /usr/src/linux-headers-3.2.0-27-generic/include/linux/kconfig.h -Iubuntu/include  -D__KERNEL__ -Wall -Wundef -Wstrict-prototypes -Wno-trigraphs -fno-strict-aliasing -fno-common -Werror-implicit-function-declaration -Wno-format-security -fno-delete-null-pointer-checks -O2 -m64 -mtune=generic -mno-red-zone -mcmodel=kernel -funit-at-a-time -maccumulate-outgoing-
   args -fstack-protector -DCONFIG_AS_CFI=1 -DCONFIG_AS_CFI_SIGNAL_FRAME=1 -DCONFIG_AS_CFI_SECTIONS=1 -DCONFIG_AS_FXSAVEQ=1 -pipe -Wno-sign-compare -fno-asynchronous-unwind-tables -mno-sse -mno-mmx -mno-sse2 -mno-3dnow -Wframe-larger-than=1024 -Wno-unused-but-set-variable -fno-omit-frame-pointer -fno-optimize-sibling-calls -pg -Wdeclaration-after-statement -Wno-pointer-sign -fno-strict-overflow -fconserve-stack -DCC_HAVE_ASM_GOTO -I/tmp/selfgz1809/NVIDIA-Linux-x86_64-295.71/kernel -Wall -MD -Wsign-compare -Wno-cast-qual -Wno-error -D__KERNEL__ -DMODULE -DNVRM -DNV_VERSION_STRING=\"295.71\" -Wno-unused-function -Wuninitialized -mno-red-zone -mcmodel=kernel -UDEBUG -U_DEBUG -DNDEBUG  -DMODULE  -D"KBUILD_STR(s)=#s" -D"KBUILD_BASENAME=KBUILD_STR(nv_mempool)"  -D"KBUILD_MODNAME=KBUILD_STR(nvidia)" -c -o /tmp/selfgz1809/NVIDIA-Linux-x86_64-295.71/kernel/.tmp_nv-mempool.o /tmp/selfgz1809/NVIDIA-Linux-x86_64-295.71/kernel/nv-mempool.c
   In file included from include/linux/kernel.h:17:0,
                    from include/linux/sched.h:55,
                    from include/linux/utsname.h:35,
                    from /tmp/selfgz1809/NVIDIA-Linux-x86_64-295.71/kernel/nv-linux.h:38,
                    from /tmp/selfgz1809/NVIDIA-Linux-x86_64-295.71/kernel/nv-mempool.c:15:
   include/linux/bitops.h: In function &#8216;hweight_long&#8217;:
   include/linux/bitops.h:49:41: warning: signed and unsigned type in conditional expression [-Wsign-compare]
   In file included from /usr/src/linux-headers-3.2.0-27-generic/arch/x86/include/asm/uaccess.h:575:0,
                    from include/linux/poll.h:14,
                    from /tmp/selfgz1809/NVIDIA-Linux-x86_64-295.71/kernel/nv-linux.h:97,
                    from /tmp/selfgz1809/NVIDIA-Linux-x86_64-295.71/kernel/nv-mempool.c:15:
   /usr/src/linux-headers-3.2.0-27-generic/arch/x86/include/asm/uaccess_64.h: In function &#8216;copy_from_user&#8217;:
   /usr/src/linux-headers-3.2.0-27-generic/arch/x86/include/asm/uaccess_64.h:53:6: warning: comparison between signed and unsigned integer expressions [-Wsign-compare]
     if [ "-pg" = "-pg" ]; then if [ /tmp/selfgz1809/NVIDIA-Linux-x86_64-295.71/kernel/nv-mempool.o != "scripts/mod/empty.o" ]; then /usr/src/linux-headers-3.2.0-27-generic/scripts/recordmcount  "/tmp/selfgz1809/NVIDIA-Linux-x86_64-295.71/kernel/nv-mempool.o"; fi; fi;
     cc -Wp,-MD,/tmp/selfgz1809/NVIDIA-Linux-x86_64-295.71/kernel/.nv-mlock.o.d  -nostdinc -isystem /usr/lib/gcc/x86_64-linux-gnu/4.6/include  -I/usr/src/linux-headers-3.2.0-27-generic/arch/x86/include -Iarch/x86/include/generated -Iinclude  -include /usr/src/linux-headers-3.2.0-27-generic/include/linux/kconfig.h -Iubuntu/include  -D__KERNEL__ -Wall -Wundef -Wstrict-prototypes -Wno-trigraphs -fno-strict-aliasing -fno-common -Werror-implicit-function-declaration -Wno-format-security -fno-delete-null-pointer-checks -O2 -m64 -mtune=generic -mno-red-zone -mcmodel=kernel -funit-at-a-time -maccumulate-outgoing-args -fstack-protector -DCONFIG_AS_CFI=1 -DCONFIG_AS_CFI_SIGNAL_FRAME=1 -DCONFIG_AS_CFI_SECTIONS=1 -DCONFIG_AS_FXSAVEQ=1 -pipe -Wno-sign-compare -fno-asynchronous-unwind-tabl
   es -mno-sse -mno-mmx -mno-sse2 -mno-3dnow -Wframe-larger-than=1024 -Wno-unused-but-set-variable -fno-omit-frame-pointer -fno-optimize-sibling-calls -pg -Wdeclaration-after-statement -Wno-pointer-sign -fno-strict-overflow -fconserve-stack -DCC_HAVE_ASM_GOTO -I/tmp/selfgz1809/NVIDIA-Linux-x86_64-295.71/kernel -Wall -MD -Wsign-compare -Wno-cast-qual -Wno-error -D__KERNEL__ -DMODULE -DNVRM -DNV_VERSION_STRING=\"295.71\" -Wno-unused-function -Wuninitialized -mno-red-zone -mcmodel=kernel -UDEBUG -U_DEBUG -DNDEBUG  -DMODULE  -D"KBUILD_STR(s)=#s" -D"KBUILD_BASENAME=KBUILD_STR(nv_mlock)"  -D"KBUILD_MODNAME=KBUILD_STR(nvidia)" -c -o /tmp/selfgz1809/NVIDIA-Linux-x86_64-295.71/kernel/.tmp_nv-mlock.o /tmp/selfgz1809/NVIDIA-Linux-x86_64-295.71/kernel/nv-mlock.c
   In file included from include/linux/kernel.h:17:0,
                    from include/linux/sched.h:55,
                    from include/linux/utsname.h:35,
                    from /tmp/selfgz1809/NVIDIA-Linux-x86_64-295.71/kernel/nv-linux.h:38,
                    from /tmp/selfgz1809/NVIDIA-Linux-x86_64-295.71/kernel/nv-mlock.c:15:
   include/linux/bitops.h: In function &#8216;hweight_long&#8217;:
   include/linux/bitops.h:49:41: warning: signed and unsigned type in conditional expression [-Wsign-compare]
   In file included from /usr/src/linux-headers-3.2.0-27-generic/arch/x86/include/asm/uaccess.h:575:0,
                    from include/linux/poll.h:14,
                    from /tmp/selfgz1809/NVIDIA-Linux-x86_64-295.71/kernel/nv-linux.h:97,
                    from /tmp/selfgz1809/NVIDIA-Linux-x86_64-295.71/kernel/nv-mlock.c:15:
   /usr/src/linux-headers-3.2.0-27-generic/arch/x86/include/asm/uaccess_64.h: In function &#8216;copy_from_user&#8217;:
   /usr/src/linux-headers-3.2.0-27-generic/arch/x86/include/asm/uaccess_64.h:53:6: warning: comparison between signed and unsigned integer expressions [-Wsign-compare]
     if [ "-pg" = "-pg" ]; then if [ /tmp/selfgz1809/NVIDIA-Linux-x86_64-295.71/kernel/nv-mlock.o != "scripts/mod/empty.o" ]; then /usr/src/linux-headers-3.2.0-27-generic/scripts/recordmcount  "/tmp/selfgz1809/NVIDIA-Linux-x86_64-295.71/kernel/nv-mlock.o"; fi; fi;
     cc -Wp,-MD,/tmp/selfgz1809/NVIDIA-Linux-x86_64-295.71/kernel/.nv-mmap.o.d  -nostdinc -isystem /usr/lib/gcc/x86_64-linux-gnu/4.6/include  -I/usr/src/linux-headers-3.2.0-27-generic/arch/x86/include -Iarch/x86/include/generated -Iinclude  -include /usr/src/linux-headers-3.2.0-27-generic/include/linux/kconfig.h -Iubuntu/include  -D__KERNEL__ -Wall -Wundef -Wstrict-prototypes -Wno-trigraphs -fno-strict-aliasing -fno-common -Werror-implicit-function-declaration -Wno-format-security -fno-delete-null-pointer-checks -O2 -m64 -mtune=generic -mno-red-zone -mcmodel=kernel -funit-at-a-time -maccumulate-outgoing-args -fstack-protector -DCONFIG_AS_CFI=1 -DCONFIG_AS_CFI_SIGNAL_FRAME=1 -DCONFIG_AS_CFI_SECTIONS=1 -DCONFIG_AS_FXSAVEQ=1 -pipe -Wno-sign-compare -fno-asynchronous-unwind-tables -mno-sse -mno-mmx -mno-sse2 -mno-3dnow -Wframe-larger-than=1024 -Wno-unused-but-set-variable -fno-omit-frame-pointer -fno-optimize-sibling-calls -pg -Wdeclaration-after-statement -Wno-po
   inter-sign -fno-strict-overflow -fconserve-stack -DCC_HAVE_ASM_GOTO -I/tmp/selfgz1809/NVIDIA-Linux-x86_64-295.71/kernel -Wall -MD -Wsign-compare -Wno-cast-qual -Wno-error -D__KERNEL__ -DMODULE -DNVRM -DNV_VERSION_STRING=\"295.71\" -Wno-unused-function -Wuninitialized -mno-red-zone -mcmodel=kernel -UDEBUG -U_DEBUG -DNDEBUG  -DMODULE  -D"KBUILD_STR(s)=#s" -D"KBUILD_BASENAME=KBUILD_STR(nv_mmap)"  -D"KBUILD_MODNAME=KBUILD_STR(nvidia)" -c -o /tmp/selfgz1809/NVIDIA-Linux-x86_64-295.71/kernel/.tmp_nv-mmap.o /tmp/selfgz1809/NVIDIA-Linux-x86_64-295.71/kernel/nv-mmap.c
   In file included from include/linux/kernel.h:17:0,
                    from include/linux/sched.h:55,
                    from include/linux/utsname.h:35,
                    from /tmp/selfgz1809/NVIDIA-Linux-x86_64-295.71/kernel/nv-linux.h:38,
                    from /tmp/selfgz1809/NVIDIA-Linux-x86_64-295.71/kernel/nv-mmap.c:15:
   include/linux/bitops.h: In function &#8216;hweight_long&#8217;:
   include/linux/bitops.h:49:41: warning: signed and unsigned type in conditional expression [-Wsign-compare]
   In file included from /usr/src/linux-headers-3.2.0-27-generic/arch/x86/include/asm/uaccess.h:575:0,
                    from include/linux/poll.h:14,
                    from /tmp/selfgz1809/NVIDIA-Linux-x86_64-295.71/kernel/nv-linux.h:97,
                    from /tmp/selfgz1809/NVIDIA-Linux-x86_64-295.71/kernel/nv-mmap.c:15:
   /usr/src/linux-headers-3.2.0-27-generic/arch/x86/include/asm/uaccess_64.h: In function &#8216;copy_from_user&#8217;:
   /usr/src/linux-headers-3.2.0-27-generic/arch/x86/include/asm/uaccess_64.h:53:6: warning: comparison between signed and unsigned integer expressions [-Wsign-compare]
     if [ "-pg" = "-pg" ]; then if [ /tmp/selfgz1809/NVIDIA-Linux-x86_64-295.71/kernel/nv-mmap.o != "scripts/mod/empty.o" ]; then /usr/src/linux-headers-3.2.0-27-generic/scripts/recordmcount  "/tmp/selfgz1809/NVIDIA-Linux-x86_64-295.71/kernel/nv-mmap.o"; fi; fi;
     cc -Wp,-MD,/tmp/selfgz1809/NVIDIA-Linux-x86_64-295.71/kernel/.nv-p2p.o.d  -nostdinc -isystem /usr/lib/gcc/x86_64-linux-gnu/4.6/include  -I/usr/src/linux-headers-3.2.0-27-generic/arch/x86/include -Iarch/x86/include/generated -Iinclude  -include /usr/src/linux-headers-3.2.0-27-generic/include/linux/kconfig.h -Iubuntu/include  -D__KERNEL__ -Wall -Wundef -Wstrict-prototypes -Wno-trigraphs -fno-strict-aliasing -fno-common -Werror-implicit-function-declaration -Wno-format-security -fno-delete-null-pointer-checks -O2 -m64 -mtune=generic -mno-red-zone -mcmodel=kernel -funit-at-a-time -maccumulate-outgoing-args -fstack-protector -DCONFIG_AS_CFI=1 -DCONFIG_AS_CFI_SIGNAL_FRAME=1 -DCONFIG_AS_CFI_SECTIONS=1 -DCONFIG_AS_FXSAVEQ=1 -pipe -Wno-sign-compare -fno-asynchronous-unwind-tables -mno-sse -mno-mmx -mno-sse2 -mno-3dnow -Wframe-larger-than=1024 -Wno-unused-but-set-variable -fno-omit-frame-pointer -fno-optimize-sibling-calls -pg -Wdeclaration-after-statement -Wno-pointer-sign -fno-strict-overflow -fconserve-stack -DCC_HAVE_ASM_GOTO -I/tmp/selfgz1809/NVIDIA-Linux-x86_64-295.71/kernel -Wall -MD -Wsign-compare -Wno-cast-qual -Wno-error -D__KERNEL__ -DMODULE -DNV
   RM -DNV_VERSION_STRING=\"295.71\" -Wno-unused-function -Wuninitialized -mno-red-zone -mcmodel=kernel -UDEBUG -U_DEBUG -DNDEBUG  -DMODULE  -D"KBUILD_STR(s)=#s" -D"KBUILD_BASENAME=KBUILD_STR(nv_p2p)"  -D"KBUILD_MODNAME=KBUILD_STR(nvidia)" -c -o /tmp/selfgz1809/NVIDIA-Linux-x86_64-295.71/kernel/.tmp_nv-p2p.o /tmp/selfgz1809/NVIDIA-Linux-x86_64-295.71/kernel/nv-p2p.c
   In file included from include/linux/kernel.h:17:0,
                    from include/linux/sched.h:55,
                    from include/linux/utsname.h:35,
                    from /tmp/selfgz1809/NVIDIA-Linux-x86_64-295.71/kernel/nv-linux.h:38,
                    from /tmp/selfgz1809/NVIDIA-Linux-x86_64-295.71/kernel/nv-p2p.c:15:
   include/linux/bitops.h: In function &#8216;hweight_long&#8217;:
   include/linux/bitops.h:49:41: warning: signed and unsigned type in conditional expression [-Wsign-compare]
   In file included from /usr/src/linux-headers-3.2.0-27-generic/arch/x86/include/asm/uaccess.h:575:0,
                    from include/linux/poll.h:14,
                    from /tmp/selfgz1809/NVIDIA-Linux-x86_64-295.71/kernel/nv-linux.h:97,
                    from /tmp/selfgz1809/NVIDIA-Linux-x86_64-295.71/kernel/nv-p2p.c:15:
   /usr/src/linux-headers-3.2.0-27-generic/arch/x86/include/asm/uaccess_64.h: In function &#8216;copy_from_user&#8217;:
   /usr/src/linux-headers-3.2.0-27-generic/arch/x86/include/asm/uaccess_64.h:53:6: warning: comparison between signed and unsigned integer expressions [-Wsign-compare]
     if [ "-pg" = "-pg" ]; then if [ /tmp/selfgz1809/NVIDIA-Linux-x86_64-295.71/kernel/nv-p2p.o != "scripts/mod/empty.o" ]; then /usr/src/linux-headers-3.2.0-27-generic/scripts/recordmcount  "/tmp/selfgz1809/NVIDIA-Linux-x86_64-295.71/kernel/nv-p2p.o"; fi; fi;
     cc -Wp,-MD,/tmp/selfgz1809/NVIDIA-Linux-x86_64-295.71/kernel/.nv-pat.o.d  -nostdinc -isystem /usr/lib/gcc/x86_64-linux-gnu/4.6/include  -I/usr/src/linux-headers-3.2.0-27-generic/arch/x86/include -Iarch/x86/include/generated -Iinclude  -include /usr/src/linux-headers-3.2.0-27-generic/include/linux/kconfig.h -Iubuntu/include  -D__KERNEL__ -Wall 
   -Wundef -Wstrict-prototypes -Wno-trigraphs -fno-strict-aliasing -fno-common -Werror-implicit-function-declaration -Wno-format-security -fno-delete-null-pointer-checks -O2 -m64 -mtune=generic -mno-red-zone -mcmodel=kernel -funit-at-a-time -maccumulate-outgoing-args -fstack-protector -DCONFIG_AS_CFI=1 -DCONFIG_AS_CFI_SIGNAL_FRAME=1 -DCONFIG_AS_CFI_SECTIONS=1 -DCONFIG_AS_FXSAVEQ=1 -pipe -Wno-sign-compare -fno-asynchronous-unwind-tables -mno-sse -mno-mmx -mno-sse2 -mno-3dnow -Wframe-larger-than=1024 -Wno-unused-but-set-variable -fno-omit-frame-pointer -fno-optimize-sibling-calls -pg -Wdeclaration-after-statement -Wno-pointer-sign -fno-strict-overflow -fconserve-stack -DCC_HAVE_ASM_GOTO -I/tmp/selfgz1809/NVIDIA-Linux-x86_64-295.71/kernel -Wall -MD -Wsign-compare -Wno-cast-qual -Wno-error -D__KERNEL__ -DMODULE -DNVRM -DNV_VERSION_STRING=\"295.71\" -Wno-unused-function -Wuninitialized -mno-red-zone -mcmodel=kernel -UDEBUG -U_DEBUG -DNDEBUG  -DMODULE  -D"KBUILD_STR(s)=#s" -D"KBUILD_BASENAME=KBUILD_STR(nv_pat)"  -D"KB
   UILD_MODNAME=KBUILD_STR(nvidia)" -c -o /tmp/selfgz1809/NVIDIA-Linux-x86_64-295.71/kernel/.tmp_nv-pat.o /tmp/selfgz1809/NVIDIA-Linux-x86_64-295.71/kernel/nv-pat.c
   In file included from include/linux/kernel.h:17:0,
                    from include/linux/sched.h:55,
                    from include/linux/utsname.h:35,
                    from /tmp/selfgz1809/NVIDIA-Linux-x86_64-295.71/kernel/nv-linux.h:38,
                    from /tmp/selfgz1809/NVIDIA-Linux-x86_64-295.71/kernel/nv-pat.c:15:
   include/linux/bitops.h: In function &#8216;hweight_long&#8217;:
   include/linux/bitops.h:49:41: warning: signed and unsigned type in conditional expression [-Wsign-compare]
   In file included from /usr/src/linux-headers-3.2.0-27-generic/arch/x86/include/asm/uaccess.h:575:0,
                    from include/linux/poll.h:14,
                    from /tmp/selfgz1809/NVIDIA-Linux-x86_64-295.71/kernel/nv-linux.h:97,
                    from /tmp/selfgz1809/NVIDIA-Linux-x86_64-295.71/kernel/nv-pat.c:15:
   /usr/src/linux-headers-3.2.0-27-generic/arch/x86/include/asm/uaccess_64.h: In function &#8216;copy_from_user&#8217;:
   /usr/src/linux-headers-3.2.0-27-generic/arch/x86/include/asm/uaccess_64.h:53:6: warning: comparison between signed and unsigned integer expressions [-Wsign-compare]
     if [ "-pg" = "-pg" ]; then if [ /tmp/selfgz1809/NVIDIA-Linux-x86_64-295.71/kernel/nv-pat.o != "scripts/mod/empty.o" ]; then /usr/src/linux-headers-3.2.0-27-generic/scripts/recordmcount  "/tmp/selfgz1809/NVIDIA-Linux-x86_64-295.71/kernel/nv-pat.o"; fi; fi;
     cc -Wp,-MD,/tmp/selfgz1809/NVIDIA-Linux-x86_64-295.71/kernel/.nv-procfs.o.d  -nostdinc -isystem /usr/lib/gcc/x86_64-linux-gnu/4.6/include  -I/usr/src/linux-headers-3.2.0-27-generic/arch/x86/include -Iarch/x86/include/generated -Iinclude  -include /usr/src/linux-headers-3.2.0-27-generic/include/linux/kconfig.h -Iubuntu/include  -D__KERNEL__ -Wall -Wundef -Wstrict-prototypes -Wno-trigraphs -fno-strict-aliasing -fno-common -Werror-implicit-function-declaration -Wno-format-security -fno-delete-null-pointer-checks -O2 -m64 -mtune=generic -mno-red-z
   one -mcmodel=kernel -funit-at-a-time -maccumulate-outgoing-args -fstack-protector -DCONFIG_AS_CFI=1 -DCONFIG_AS_CFI_SIGNAL_FRAME=1 -DCONFIG_AS_CFI_SECTIONS=1 -DCONFIG_AS_FXSAVEQ=1 -pipe -Wno-sign-compare -fno-asynchronous-unwind-tables -mno-sse -mno-mmx -mno-sse2 -mno-3dnow -Wframe-larger-than=1024 -Wno-unused-but-set-variable -fno-omit-frame-pointer -fno-optimize-sibling-calls -pg -Wdeclaration-after-statement -Wno-pointer-sign -fno-strict-overflow -fconserve-stack -DCC_HAVE_ASM_GOTO -I/tmp/selfgz1809/NVIDIA-Linux-x86_64-295.71/kernel -Wall -MD -Wsign-compare -Wno-cast-qual -Wno-error -D__KERNEL__ -DMODULE -DNVRM -DNV_VERSION_STRING=\"295.71\" -Wno-unused-function -Wuninitialized -mno-red-zone -mcmodel=kernel -UDEBUG -U_DEBUG -DNDEBUG  -DMODULE  -D"KBUILD_STR(s)=#s" -D"KBUILD_BASENAME=KBUILD_STR(nv_procfs)"  -D"KBUILD_MODNAME=KBUILD_STR(nvidia)" -c -o /tmp/selfgz1809/NVIDIA-Linux-x86_64-295.71/kernel/.tmp_nv-procfs.o /tmp/selfgz1809/NVIDIA-Linux-x86_64-295.71/kernel/nv-procfs.c
   In file included from include/linux/kernel.h:17:0,
                    from include/linux/sched.h:55,
                    from include/linux/utsname.h:35,
                    from /tmp/selfgz1809/NVIDIA-Linux-x86_64-295.71/kernel/nv-linux.h:38,
                    from /tmp/selfgz1809/NVIDIA-Linux-x86_64-295.71/kernel/nv-procfs.c:15:
   include/linux/bitops.h: In function &#8216;hweight_long&#8217;:
   include/linux/bitops.h:49:41: warning: signed and unsigned type in conditional expression [-Wsign-compare]
   In file included from /usr/src/linux-headers-3.2.0-27-generic/arch/x86/include/asm/uaccess.h:575:0,
                    from include/linux/poll.h:14,
                    from /tmp/selfgz1809/NVIDIA-Linux-x86_64-295.71/kernel/nv-linux.h:97,
                    from /tmp/selfgz1809/NVIDIA-Linux-x86_64-295.71/kernel/nv-procfs.c:15:
   /usr/src/linux-headers-3.2.0-27-generic/arch/x86/include/asm/uaccess_64.h: In function &#8216;copy_from_user&#8217;:
   /usr/src/linux-headers-3.2.0-27-generic/arch/x86/include/asm/uaccess_64.h:53:6: warning: comparison between signed and unsigned integer expressions [-Wsign-compare]
   /tmp/selfgz1809/NVIDIA-Linux-x86_64-295.71/kernel/nv-procfs.c: In function &#8216;nv_procfs_add_text_file&#8217;:
   /tmp/selfgz1809/NVIDIA-Linux-x86_64-295.71/kernel/nv-procfs.c:671:5: warning: the comparison will always evaluate as &#8216;true&#8217; for the address of &#8216;nv_procfs_read_text_file&#8217; will never be NULL [-Waddress]
   /tmp/selfgz1809/NVIDIA-Linux-x86_64-295.71/kernel/nv-procfs.c: In function &#8216;nv_register_procfs&#8217;:
   /tmp/selfgz1809/NVIDIA-Linux-x86_64-295.71/kernel/nv-procfs.c:716:13: warning: the comparison will always evaluate as &#8216;true&#8217; for the address of &#8216;nv_procfs_read_params&#8217; will never be NULL [-Waddress]
   /tmp/selfgz1809/NVIDIA-Linux-x86_64-295.71/kernel/nv-procfs.c:732:13: warning: the comparison will always evaluate as &#8216;true&#8217; for the address of &#8216;nv_procfs_write_registry&#8217; will never be NULL [-Waddress]
   /tmp/selfgz1809/NVIDIA-Linux-x86_64-295.71/kernel/nv-procfs.c:732:13: warning: the comparison will always evaluate as &#8216;true&#8217; for the address of &#8216;nv_procfs_read_registry&#8217; will never be NULL [-Waddress]
   /tmp/selfgz1809/NVIDIA-Linux-x86_64-295.71/kernel/nv-procfs.c:732:13: warning: the comparison will always evaluate as &#8216;true&#8217; for the address of &#8216;nv_procfs_write_registry&#8217; will never be NULL [-Waddress]
   /tmp/selfgz1809/NVIDIA-Linux-x86_64-295.71/kernel/nv-procfs.c:756:13: warning: the comparison will always evaluate as &#8216;true&#8217; for the address of &#8216;nv_procfs_read_version&#8217; will never be NULL [-Waddress]
   /tmp/selfgz1809/NVIDIA-Linux-x86_64-295.71/kernel/nv-procfs.c:774:17: warning: the comparison will always evaluate as &#8216;true&#8217; for the address of &#8216;nv_procfs_read_gpu_info&#8217; will never be NULL [-Waddress]
   /tmp/selfgz1809/NVIDIA-Linux-x86_64-295.71/kernel/nv-procfs.c:779:17: warning: the comparison will always evaluate as &#8216;true&#8217; for the address of &#8216;nv_procfs_write_registry&#8217; will never be NULL [-Waddress]
   /tmp/selfgz1809/NVIDIA-Linux-x86_64-295.71/kernel/nv-procfs.c:779:17: warning: the comparison will always evaluate as &#8216;true&#8217; for the address of &#8216;nv_procfs_read_registry&#8217; will never be NULL [-Waddress]
   /tmp/selfgz1809/NVIDIA-Linux-x86_64-295.71/kernel/nv-procfs.c:779:17: warning: the comparison will always evaluate as &#8216;true&#8217; for the address of &#8216;nv_procfs_write_registry&#8217; will never be NULL [-Waddress]
   /tmp/selfgz1809/NVIDIA-Linux-x86_64-295.71/kernel/nv-procfs.c:792:21: warning: the comparison will always evaluate as &#8216;true&#8217; for the address of &#8216;nv_procfs_read_agp_status&#8217; will never be NULL [-Waddress]
   /tmp/selfgz1809/NVIDIA-Linux-x86_64-295.71/kernel/nv-procfs.c:797:21: warning: the comparison will always evaluate as &#8216;true&#8217; for the address of &#8216;nv_procfs_read_agp_info&#8217; will never be NULL [-Waddress]
   /tmp/selfgz1809/NVIDIA-Linux-x86_64-295.71/kernel/nv-procfs.c:802:21: warning: the comparison will always evaluate as &#8216;true&#8217; for the address of &#8216;nv_procfs_read_agp_info&#8217; will never be NULL [-Waddress]
     if [ "-pg" = "-pg" ]; then if [ /tmp/selfgz1809/NVIDIA-Linux-x86_64-295.71/kernel/nv-procfs.o != "scripts/mod/empty.o" ]; then /usr/src/linux-headers-3.2.0-27-generic/scripts/recordmcount  "/tmp/selfgz1809/NVIDIA-Linux-x86_64-295.71/kernel/nv-procfs.o"; fi; fi;
     cc -Wp,-MD,/tmp/selfgz1809/NVIDIA-Linux-x86_64-295.71/kernel/.nv-usermap.o.d  -nostdinc -isystem /usr/lib/gcc/x86_64-linux-gnu/4.6/include  -I/usr/src/linux-headers-3.2.0-27-generic/arch/x86/include -Iarch/x86/include/generated -Iinclude  -include /usr/src/linux-headers-3.2.0-27-generic/include/linux/kconfig.h -Iubuntu/include  -D__KERNEL__ -Wall -Wundef -Wstrict-prototypes -Wno-trigraphs -fno-strict-aliasing -fno-common -Werror-implicit-function-declaration -Wno-format-security -fno-delete-null-pointer-checks -O2 -m64 -mtune=generic -mno-red-zone -mcmodel=kernel -funit-at-a-time -maccumulate-outgoing-args -fstack-protector -DCONFIG_AS_CFI=1 -DCONFIG_AS_CFI_SIGNAL_FRAME=1 -DCONFIG_AS_CFI_SECTIONS=1 -DCONFIG_AS_FXSAVEQ=1 -pipe -Wno-sign-compare -fno-asynchronous-unwind-tables -mno-sse -mno-mmx -mno-sse2 -mno-3dnow -Wframe-larger-than=1024 -Wno-unused-but-set-vari
   able -fno-omit-frame-pointer -fno-optimize-sibling-calls -pg -Wdeclaration-after-statement -Wno-pointer-sign -fno-strict-overflow -fconserve-stack -DCC_HAVE_ASM_GOTO -I/tmp/selfgz1809/NVIDIA-Linux-x86_64-295.71/kernel -Wall -MD -Wsign-compare -Wno-cast-qual -Wno-error -D__KERNEL__ -DMODULE -DNVRM -DNV_VERSION_STRING=\"295.71\" -Wno-unused-function -Wuninitialized -mno-red-zone -mcmodel=kernel -UDEBUG -U_DEBUG -DNDEBUG  -DMODULE  -D"KBUILD_STR(s)=#s" -D"KBUILD_BASENAME=KBUILD_STR(nv_usermap)"  -D"KBUILD_MODNAME=KBUILD_STR(nvidia)" -c -o /tmp/selfgz1809/NVIDIA-Linux-x86_64-295.71/kernel/.tmp_nv-usermap.o /tmp/selfgz1809/NVIDIA-Linux-x86_64-295.71/kernel/nv-usermap.c
   In file included from include/linux/kernel.h:17:0,
                    from include/linux/sched.h:55,
                    from include/linux/utsname.h:35,
                    from /tmp/selfgz1809/NVIDIA-Linux-x86_64-295.71/kernel/nv-linux.h:38,
                    from /tmp/selfgz1809/NVIDIA-Linux-x86_64-295.71/kernel/nv-usermap.c:15:
   include/linux/bitops.h: In function &#8216;hweight_long&#8217;:
   include/linux/bitops.h:49:41: warning: signed and unsigned type in conditional expression [-Wsign-compare]
   In file included from /usr/src/linux-headers-3.2.0-27-generic/arch/x86/include/asm/uaccess.h:575:0,
                    from include/linux/poll.h:14,
                    from /tmp/selfgz1809/NVIDIA-Linux-x86_64-295.71/kernel/nv-linux.h:97,
                    from /tmp/selfgz1809/NVIDIA-Linux-x86_64-295.71/kernel/nv-usermap.c:15:
   /usr/src/linux-headers-3.2.0-27-generic/arch/x86/include/asm/uaccess_64.h: In function &#8216;copy_from_user&#8217;:
   /usr/src/linux-headers-3.2.0-27-generic/arch/x86/include/asm/uaccess_64.h:53:6: warning: comparison between signed and unsigned integer expressions [-Wsign-compare]
     if [ "-pg" = "-pg" ]; then if [ /tmp/selfgz1809/NVIDIA-Linux-x86_64-295.71/kernel/nv-usermap.o != "scripts/mod/empty.o" ]; then /usr/src/linux-headers-3.2.0-27-generic/scripts/recordmcount  "/tmp/selfgz1809/NVIDIA-Linux-x86_64-295.71/kernel/nv-usermap.o"; fi; fi;
     cc -Wp,-MD,/tmp/selfgz1809/NVIDIA-Linux-x86_64-295.71/kernel/.nv-vm.o.d  -nostdinc -isystem /usr/lib/gcc/x86_64-linux-gnu/4.6/include  -I/usr/src/linux-headers-3.2.0-27-generic/arch/x86/include -Iarch/x86/include/generated -Iinclude  -include /usr/src/linux-headers-3.2.0-27-generic/include/linux/kconfig.h -Iubuntu/include  -D__KERNEL__ -Wall -Wundef -Wstrict-prototypes -Wno-trigraphs -fno-strict-aliasing -fno-common -Werror-implicit-function-declaration -Wno-format-security -fno-delete-null-pointer-checks -O2 -m64 -mtune=generic -mno-red-zone -mcmodel=kernel -funit-at-a-time -maccumulate-outgoing-args -fstack-protector -DCONFIG_AS_CFI=1 -DCONFIG_AS_CFI_SIGNAL_FRAME=1 -DCONFIG_AS_CFI_SECTIONS=1 -DCONFIG_AS_FXSAVEQ=1 -pipe -Wno-sign-compare -fno-asynchronous-unwind-tables -mno-sse -mno-mmx -mno-sse2 -mno-3dnow -Wframe-larger-than=1024 -Wno-unused-but-set-variable -fno-omit-frame-pointer -fno-optimize-sibling-calls -pg -Wdeclaration-after-statement -Wno-pointer-sign -fno-strict-overflow -fconserve-stack -DCC_HAVE_ASM_GOTO -I/tmp/self
   gz1809/NVIDIA-Linux-x86_64-295.71/kernel -Wall -MD -Wsign-compare -Wno-cast-qual -Wno-error -D__KERNEL__ -DMODULE -DNVRM -DNV_VERSION_STRING=\"295.71\" -Wno-unused-function -Wuninitialized -mno-red-zone -mcmodel=kernel -UDEBUG -U_DEBUG -DNDEBUG  -DMODULE  -D"KBUILD_STR(s)=#s" -D"KBUILD_BASENAME=KBUILD_STR(nv_vm)"  -D"KBUILD_MODNAME=KBUILD_STR(nvidia)" -c -o /tmp/selfgz1809/NVIDIA-Linux-x86_64-295.71/kernel/.tmp_nv-vm.o /tmp/selfgz1809/NVIDIA-Linux-x86_64-295.71/kernel/nv-vm.c
   In file included from include/linux/kernel.h:17:0,
                    from include/linux/sched.h:55,
                    from include/linux/utsname.h:35,
                    from /tmp/selfgz1809/NVIDIA-Linux-x86_64-295.71/kernel/nv-linux.h:38,
                    from /tmp/selfgz1809/NVIDIA-Linux-x86_64-295.71/kernel/nv-vm.c:14:
   include/linux/bitops.h: In function &#8216;hweight_long&#8217;:
   include/linux/bitops.h:49:41: warning: signed and unsigned type in conditional expression [-Wsign-compare]
   In file included from /usr/src/linux-headers-3.2.0-27-generic/arch/x86/include/asm/uaccess.h:575:0,
                    from include/linux/poll.h:14,
                    from /tmp/selfgz1809/NVIDIA-Linux-x86_64-295.71/kernel/nv-linux.h:97,
                    from /tmp/selfgz1809/NVIDIA-Linux-x86_64-295.71/kernel/nv-vm.c:14:
   /usr/src/linux-headers-3.2.0-27-generic/arch/x86/include/asm/uaccess_64.h: In function &#8216;copy_from_user&#8217;:
   /usr/src/linux-headers-3.2.0-27-generic/arch/x86/include/asm/uaccess_64.h:53:6: warning: comparison between signed and unsigned integer expressions [-Wsign-compare]
     if [ "-pg" = "-pg" ]; then if [ /tmp/selfgz1809/NVIDIA-Linux-x86_64-295.71/kernel/nv-vm.o != "scripts/mod/empty.o" ]; then /usr/src/linux-headers-3.2.0-27-generic/scripts/recordmcount  "/tmp/selfgz1809/NVIDIA-Linux-x86_64-295.71/kernel/nv-vm.o"; fi; fi;
     cc -Wp,-MD,/tmp/selfgz1809/NVIDIA-Linux-x86_64-295.71/kernel/.nv-vtophys.o.d  -nostdinc -isystem /usr/lib/gcc/x86_64-linux-gnu/4.6/include  -I/usr/src/linux-headers-3.2.0-27-generic/arch/x86/include -Iarch/x86/include/generated -Iinclude  -include /usr/src/linux-headers-3.2.0-27-generic/include/linux/kconfig.h -Iubuntu/include  -D__KERNEL__ -Wall -Wundef -Wstrict-prototypes -Wno-trigraphs -fno-strict-aliasing -fno-common -Werror-implicit-function-declaration -Wno-format-security -fno-delete-null-pointer-checks -O2 -m64 -mtune=generic -mno-red-zone -mcmodel=kernel -funit-at-a-time -maccumulate-outgoing-args -fstack-protector -DCONFIG_AS_CFI=1 -DCONFIG_AS_CFI_SIGNAL_FRAME=1 -DCONFIG_AS_CFI_SECTIONS=1 -DCONFIG_AS_FXSAVEQ=1 -pipe -Wno-sign-compare -fno-asynchronous-unwind-tables -mno-sse -mno-mmx -mno-sse2 -mno-3dnow -Wframe-larger-than=1024 -Wno-unused-but-set-variable -fno-omit-frame-pointer -fno-optimize-sibling-calls -pg -Wdeclaration-after-statement -Wno-pointer-sign -fno-strict-overflow -fconserve-stack -DCC_HAVE_ASM_GOTO -I/tmp/selfgz1809/NVIDIA-Linux-x86_64-295.71/kernel -Wall -MD -Wsign-compare -Wno-cast-qual -Wno-error -D__KERNEL__ -DMODULE -DNVRM -DNV_VERSION_STRING=\"295.71\" -Wno-unused-function -Wuninitialized -mno-red-zone -mcm
   odel=kernel -UDEBUG -U_DEBUG -DNDEBUG  -DMODULE  -D"KBUILD_STR(s)=#s" -D"KBUILD_BASENAME=KBUILD_STR(nv_vtophys)"  -D"KBUILD_MODNAME=KBUILD_STR(nvidia)" -c -o /tmp/selfgz1809/NVIDIA-Linux-x86_64-295.71/kernel/.tmp_nv-vtophys.o /tmp/selfgz1809/NVIDIA-Linux-x86_64-295.71/kernel/nv-vtophys.c
   In file included from include/linux/kernel.h:17:0,
                    from include/linux/sched.h:55,
                    from include/linux/utsname.h:35,
                    from /tmp/selfgz1809/NVIDIA-Linux-x86_64-295.71/kernel/nv-linux.h:38,
                    from /tmp/selfgz1809/NVIDIA-Linux-x86_64-295.71/kernel/nv-vtophys.c:15:
   include/linux/bitops.h: In function &#8216;hweight_long&#8217;:
   include/linux/bitops.h:49:41: warning: signed and unsigned type in conditional expression [-Wsign-compare]
   In file included from /usr/src/linux-headers-3.2.0-27-generic/arch/x86/include/asm/uaccess.h:575:0,
                    from include/linux/poll.h:14,
                    from /tmp/selfgz1809/NVIDIA-Linux-x86_64-295.71/kernel/nv-linux.h:97,
                    from /tmp/selfgz1809/NVIDIA-Linux-x86_64-295.71/kernel/nv-vtophys.c:15:
   /usr/src/linux-headers-3.2.0-27-generic/arch/x86/include/asm/uaccess_64.h: In function &#8216;copy_from_user&#8217;:
   /usr/src/linux-headers-3.2.0-27-generic/arch/x86/include/asm/uaccess_64.h:53:6: warning: comparison between signed and unsigned integer expressions [-Wsign-compare]
     if [ "-pg" = "-pg" ]; then if [ /tmp/selfgz1809/NVIDIA-Linux-x86_64-295.71/kernel/nv-vtophys.o != "scripts/mod/empty.o" ]; then /usr/src/linux-headers-3.2.0-27-generic/scripts/recordmcount  "/tmp/selfgz1809/NVIDIA-Linux-x86_64-295.71/kernel/nv-vtophys.o"; fi; fi;
     cc -Wp,-MD,/tmp/selfgz1809/NVIDIA-Linux-x86_64-295.71/kernel/.os-agp.o.d  -nostdinc -isystem /usr/lib/gcc/x86_64-linux-gnu/4.6/include  -I/usr/src/linux-headers-3.2.0-27-generic/arch/x86/include -Iarch/x86/include/generated -Iinclude  -include /usr/src/linux-headers-3.2.0-27-generic/include/linux/kconfig.h -Iubuntu/include  -D__KERNEL__ -Wall -Wundef -Wstrict-prototypes -Wno-trigraphs -fno-strict-aliasi
   ng -fno-common -Werror-implicit-function-declaration -Wno-format-security -fno-delete-null-pointer-checks -O2 -m64 -mtune=generic -mno-red-zone -mcmodel=kernel -funit-at-a-time -maccumulate-outgoing-args -fstack-protector -DCONFIG_AS_CFI=1 -DCONFIG_AS_CFI_SIGNAL_FRAME=1 -DCONFIG_AS_CFI_SECTIONS=1 -DCONFIG_AS_FXSAVEQ=1 -pipe -Wno-sign-compare -fno-asynchronous-unwind-tables -mno-sse -mno-mmx -mno-sse2 -mno-3dnow -Wframe-larger-than=1024 -Wno-unused-but-set-variable -fno-omit-frame-pointer -fno-optimize-sibling-calls -pg -Wdeclaration-after-statement -Wno-pointer-sign -fno-strict-overflow -fconserve-stack -DCC_HAVE_ASM_GOTO -I/tmp/selfgz1809/NVIDIA-Linux-x86_64-295.71/kernel -Wall -MD -Wsign-compare -Wno-cast-qual -Wno-error -D__KERNEL__ -DMODULE -DNVRM -DNV_VERSION_STRING=\"295.71\" -Wno-unused-function -Wuninitialized -mno-red-zone -mcmodel=kernel -UDEBUG -U_DEBUG -DNDEBUG  -DMODULE  -D"KBUILD_STR(s)=#s" -D"KBUILD_BASENAME=KBUILD_STR(os_agp)"  -D"KBUILD_MODNAME=KBUILD_STR(nvidia)" -c -o /tmp/selfgz1809/NVIDIA
   -Linux-x86_64-295.71/kernel/.tmp_os-agp.o /tmp/selfgz1809/NVIDIA-Linux-x86_64-295.71/kernel/os-agp.c
   In file included from include/linux/kernel.h:17:0,
                    from include/linux/sched.h:55,
                    from include/linux/utsname.h:35,
                    from /tmp/selfgz1809/NVIDIA-Linux-x86_64-295.71/kernel/nv-linux.h:38,
                    from /tmp/selfgz1809/NVIDIA-Linux-x86_64-295.71/kernel/os-agp.c:24:
   include/linux/bitops.h: In function &#8216;hweight_long&#8217;:
   include/linux/bitops.h:49:41: warning: signed and unsigned type in conditional expression [-Wsign-compare]
   In file included from /usr/src/linux-headers-3.2.0-27-generic/arch/x86/include/asm/uaccess.h:575:0,
                    from include/linux/poll.h:14,
                    from /tmp/selfgz1809/NVIDIA-Linux-x86_64-295.71/kernel/nv-linux.h:97,
                    from /tmp/selfgz1809/NVIDIA-Linux-x86_64-295.71/kernel/os-agp.c:24:
   /usr/src/linux-headers-3.2.0-27-generic/arch/x86/include/asm/uaccess_64.h: In function &#8216;copy_from_user&#8217;:
   /usr/src/linux-headers-3.2.0-27-generic/arch/x86/include/asm/uaccess_64.h:53:6: warning: comparison between signed and unsigned integer expressions [-Wsign-compare]
     if [ "-pg" = "-pg" ]; then if [ /tmp/selfgz1809/NVIDIA-Linux-x86_64-295.71/kernel/os-agp.o != "scripts/mod/empty.o" ]; then /usr/src/linux-headers-3.2.0-27-generic/scripts/recordmcount  "/tmp/selfgz1809/NVIDIA-Linux-x86_64-295.71/kernel/os-agp.o"; fi; fi;
     cc -Wp,-MD,/tmp/selfgz1809/NVIDIA-Linux-x86_64-295.71/kernel/.os-interface.o.d  -nostdinc -isystem /usr/lib/gcc/x86_64-linux-gnu/4.6/include  -I/usr/src/linux-headers-3.2.0-27-generic/arch/x86/include -Iarch/x86/include/generated -Iinclude  -include /usr/src/linux-headers-3.2.0-27-generic/include/linux/kconfig.h -Iubuntu/include  -D__KERNEL__ -Wall -Wundef -Wstrict-prototypes -Wno-trigraphs -fno-strict-aliasing -fno-common -Werror-implicit-function-declaration -Wno-format-security -fno-delete-null-pointer-checks -O2 -m64 -mtune=generic -mno-red-zone -mcmodel=kernel -funit-at-a-time -maccumulate-outgoing
   -args -fstack-protector -DCONFIG_AS_CFI=1 -DCONFIG_AS_CFI_SIGNAL_FRAME=1 -DCONFIG_AS_CFI_SECTIONS=1 -DCONFIG_AS_FXSAVEQ=1 -pipe -Wno-sign-compare -fno-asynchronous-unwind-tables -mno-sse -mno-mmx -mno-sse2 -mno-3dnow -Wframe-larger-than=1024 -Wno-unused-but-set-variable -fno-omit-frame-pointer -fno-optimize-sibling-calls -pg -Wdeclaration-after-statement -Wno-pointer-sign -fno-strict-overflow -fconserve-stack -DCC_HAVE_ASM_GOTO -I/tmp/selfgz1809/NVIDIA-Linux-x86_64-295.71/kernel -Wall -MD -Wsign-compare -Wno-cast-qual -Wno-error -D__KERNEL__ -DMODULE -DNVRM -DNV_VERSION_STRING=\"295.71\" -Wno-unused-function -Wuninitialized -mno-red-zone -mcmodel=kernel -UDEBUG -U_DEBUG -DNDEBUG  -DMODULE  -D"KBUILD_STR(s)=#s" -D"KBUILD_BASENAME=KBUILD_STR(os_interface)"  -D"KBUILD_MODNAME=KBUILD_STR(nvidia)" -c -o /tmp/selfgz1809/NVIDIA-Linux-x86_64-295.71/kernel/.tmp_os-interface.o /tmp/selfgz1809/NVIDIA-Linux-x86_64-295.71/kernel/os-interface.c
   In file included from include/linux/kernel.h:17:0,
                    from include/linux/sched.h:55,
                    from include/linux/utsname.h:35,
                    from /tmp/selfgz1809/NVIDIA-Linux-x86_64-295.71/kernel/nv-linux.h:38,
                    from /tmp/selfgz1809/NVIDIA-Linux-x86_64-295.71/kernel/os-interface.c:26:
   include/linux/bitops.h: In function &#8216;hweight_long&#8217;:
   include/linux/bitops.h:49:41: warning: signed and unsigned type in conditional expression [-Wsign-compare]
   In file included from /usr/src/linux-headers-3.2.0-27-generic/arch/x86/include/asm/uaccess.h:575:0,
                    from include/linux/poll.h:14,
                    from /tmp/selfgz1809/NVIDIA-Linux-x86_64-295.71/kernel/nv-linux.h:97,
                    from /tmp/selfgz1809/NVIDIA-Linux-x86_64-295.71/kernel/os-interface.c:26:
   /usr/src/linux-headers-3.2.0-27-generic/arch/x86/include/asm/uaccess_64.h: In function &#8216;copy_from_user&#8217;:
   /usr/src/linux-headers-3.2.0-27-generic/arch/x86/include/asm/uaccess_64.h:53:6: warning: comparison between signed and unsigned integer expressions [-Wsign-compare]
     if [ "-pg" = "-pg" ]; then if [ /tmp/selfgz1809/NVIDIA-Linux-x86_64-295.71/kernel/os-interface.o != "scripts/mod/empty.o" ]; then /usr/src/linux-headers-3.2.0-27-generic/scripts/recordmcount  "/tmp/selfgz1809/NVIDIA-Linux-x86_64-295.71/kernel/os-interface.o"; fi; fi;
     cc -Wp,-MD,/tmp/selfgz1809/NVIDIA-Linux-x86_64-295.71/kernel/.os-mtrr.o.d  -nostdinc -isystem /usr/lib/gcc/x86_64-linux-gnu/4.6/include  -I/usr/src/linux-headers-3.2.0-27-generic/arch/x86/include -Iarch/x86/include/generated -Iinclude  -include /usr/src/linux-headers-3.2.0-27-generic/include/linux/kconfig.h -Iubuntu/include  -D__KERNEL__ -Wall -Wundef -Wstrict-prototypes -Wno-trigraphs -fno-strict-aliasing -fno-common -Werror-implicit-function-declaration -Wno-format-security -fno-delete-null-pointer-checks -O2 -m64 -mtune=generic -mno-red-zone -mcmodel=kernel -funit-at-a-time -maccumulate-outgoing-args -fstack-protector -DCONFIG_AS_CFI=1 -DCONFIG_AS_CFI_SIGNAL_FRAME=1 -DCONFIG_AS_CFI_SECTIONS=1 -DCONFIG_AS_FXSAVEQ=1 -pipe -Wno-sign-compare -fno-asynchrono
   us-unwind-tables -mno-sse -mno-mmx -mno-sse2 -mno-3dnow -Wframe-larger-than=1024 -Wno-unused-but-set-variable -fno-omit-frame-pointer -fno-optimize-sibling-calls -pg -Wdeclaration-after-statement -Wno-pointer-sign -fno-strict-overflow -fconserve-stack -DCC_HAVE_ASM_GOTO -I/tmp/selfgz1809/NVIDIA-Linux-x86_64-295.71/kernel -Wall -MD -Wsign-compare -Wno-cast-qual -Wno-error -D__KERNEL__ -DMODULE -DNVRM -DNV_VERSION_STRING=\"295.71\" -Wno-unused-function -Wuninitialized -mno-red-zone -mcmodel=kernel -UDEBUG -U_DEBUG -DNDEBUG  -DMODULE  -D"KBUILD_STR(s)=#s" -D"KBUILD_BASENAME=KBUILD_STR(os_mtrr)"  -D"KBUILD_MODNAME=KBUILD_STR(nvidia)" -c -o /tmp/selfgz1809/NVIDIA-Linux-x86_64-295.71/kernel/.tmp_os-mtrr.o /tmp/selfgz1809/NVIDIA-Linux-x86_64-295.71/kernel/os-mtrr.c
   In file included from include/linux/kernel.h:17:0,
                    from include/linux/sched.h:55,
                    from include/linux/utsname.h:35,
                    from /tmp/selfgz1809/NVIDIA-Linux-x86_64-295.71/kernel/nv-linux.h:38,
                    from /tmp/selfgz1809/NVIDIA-Linux-x86_64-295.71/kernel/os-mtrr.c:15:
   include/linux/bitops.h: In function &#8216;hweight_long&#8217;:
   include/linux/bitops.h:49:41: warning: signed and unsigned type in conditional expression [-Wsign-compare]
   In file included from /usr/src/linux-headers-3.2.0-27-generic/arch/x86/include/asm/uaccess.h:575:0,
                    from include/linux/poll.h:14,
                    from /tmp/selfgz1809/NVIDIA-Linux-x86_64-295.71/kernel/nv-linux.h:97,
                    from /tmp/selfgz1809/NVIDIA-Linux-x86_64-295.71/kernel/os-mtrr.c:15:
   /usr/src/linux-headers-3.2.0-27-generic/arch/x86/include/asm/uaccess_64.h: In function &#8216;copy_from_user&#8217;:
   /usr/src/linux-headers-3.2.0-27-generic/arch/x86/include/asm/uaccess_64.h:53:6: warning: comparison between signed and unsigned integer expressions [-Wsign-compare]
     if [ "-pg" = "-pg" ]; then if [ /tmp/selfgz1809/NVIDIA-Linux-x86_64-295.71/kernel/os-mtrr.o != "scripts/mod/empty.o" ]; then /usr/src/linux-headers-3.2.0-27-generic/scripts/recordmcount  "/tmp/selfgz1809/NVIDIA-Linux-x86_64-295.71/kernel/os-mtrr.o"; fi; fi;
     cc -Wp,-MD,/tmp/selfgz1809/NVIDIA-Linux-x86_64-295.71/kernel/.os-registry.o.d  -nostdinc -isystem /usr/lib/gcc/x86_64-linux-gnu/4.6/include  -I/usr/src/linux-headers-3.2.0-27-generic/arch/x86/include -Iarch/x86/include/generated -Iinclude  -include /usr/src/linux-headers-3.2.0-27-generic/include/linux/kconfig.h -Iubuntu/include  -D__KERNEL__ -Wall -Wundef -Wstrict-prototypes -Wno-trigraphs -fno-strict-aliasing -fno-common -Werror-implicit-function-declaration -Wno-format-security -fno-delete-null-pointer-checks -O2 -m64 -mtune=generic -mno-red-zone -mcmodel=kernel -funit-at-a-time -maccumulate-outgoing-args -fstack-protector -DCONFIG_AS_CFI=1 -DCONFIG_AS_CFI_SIGNAL_FRAME=1 -DCONFIG_AS_CFI_SECTIONS=1 -DCONFIG_AS_FXSAVEQ=1 -pipe -Wno-sign-compare -fno-asynchronous-unwind-tables -mno-sse -mno-mmx -mno-sse2 -mno-3dnow -Wframe-larger-than=1024 -Wno-unused-but-set-variable -fno-omit-frame-pointer -fno-optimize-sibling-calls -pg -Wdeclaration-after-statem
   ent -Wno-pointer-sign -fno-strict-overflow -fconserve-stack -DCC_HAVE_ASM_GOTO -I/tmp/selfgz1809/NVIDIA-Linux-x86_64-295.71/kernel -Wall -MD -Wsign-compare -Wno-cast-qual -Wno-error -D__KERNEL__ -DMODULE -DNVRM -DNV_VERSION_STRING=\"295.71\" -Wno-unused-function -Wuninitialized -mno-red-zone -mcmodel=kernel -UDEBUG -U_DEBUG -DNDEBUG  -DMODULE  -D"KBUILD_STR(s)=#s" -D"KBUILD_BASENAME=KBUILD_STR(os_registry)"  -D"KBUILD_MODNAME=KBUILD_STR(nvidia)" -c -o /tmp/selfgz1809/NVIDIA-Linux-x86_64-295.71/kernel/.tmp_os-registry.o /tmp/selfgz1809/NVIDIA-Linux-x86_64-295.71/kernel/os-registry.c
   In file included from include/linux/kernel.h:17:0,
                    from include/linux/sched.h:55,
                    from include/linux/utsname.h:35,
                    from /tmp/selfgz1809/NVIDIA-Linux-x86_64-295.71/kernel/nv-linux.h:38,
                    from /tmp/selfgz1809/NVIDIA-Linux-x86_64-295.71/kernel/os-registry.c:15:
   include/linux/bitops.h: In function &#8216;hweight_long&#8217;:
   include/linux/bitops.h:49:41: warning: signed and unsigned type in conditional expression [-Wsign-compare]
   In file included from /usr/src/linux-headers-3.2.0-27-generic/arch/x86/include/asm/uaccess.h:575:0,
                    from include/linux/poll.h:14,
                    from /tmp/selfgz1809/NVIDIA-Linux-x86_64-295.71/kernel/nv-linux.h:97,
                    from /tmp/selfgz1809/NVIDIA-Linux-x86_64-295.71/kernel/os-registry.c:15:
   /usr/src/linux-headers-3.2.0-27-generic/arch/x86/include/asm/uaccess_64.h: In function &#8216;copy_from_user&#8217;:
   /usr/src/linux-headers-3.2.0-27-generic/arch/x86/include/asm/uaccess_64.h:53:6: warning: comparison between signed and unsigned integer expressions [-Wsign-compare]
     if [ "-pg" = "-pg" ]; then if [ /tmp/selfgz1809/NVIDIA-Linux-x86_64-295.71/kernel/os-registry.o != "scripts/mod/empty.o" ]; then /usr/src/linux-headers-3.2.0-27-generic/scripts/recordmcount  "/tmp/selfgz1809/NVIDIA-Linux-x86_64-295.71/kernel/os-registry.o"; fi; fi;
     cc -Wp,-MD,/tmp/selfgz1809/NVIDIA-Linux-x86_64-295.71/kernel/.os-smp.o.d  -nostdinc -isystem /usr/lib/gcc/x86_64-linux-gnu/4.6/include  -I/usr/src/linux-headers-3.2.0-27-generic/arch/x86/include -Iarch/x86/include/generated -Iinclude  -include /usr/src/linux-headers-3.2.0-27-generic/include/linux/kconfig.h -Iubuntu/include  -D__KERNEL__ -Wall -Wundef -Wstrict-prototypes -Wno-trigraphs -fno-strict-aliasing -fno-common -Werror-implicit-function-declaration -Wno-format-security -fno-delete-null-pointer-checks -O2 -m64 -mtune=generic -mno-red-zone -mcmodel=kernel -funit-at-a-time -maccumulate-outgoing-args -fstack-protector -DCONFIG_AS_CFI=1 -DCONFIG_AS_CFI_SIGNAL_FRAME=1 -DCONFIG_AS_CFI_SECTIONS=1 -DCONFIG_AS_FXSAVEQ=1 -pipe -Wno-sign-compare -fno-asynchronous-unwind-tables -mno-sse -mno-mmx -mno-sse2 -mno-3dnow -Wframe-larger-than=1024 -Wno-unused-but-set-variable -fno-omit-frame-pointer -fno-optimize-sibling-calls -pg -Wdeclaration-after-statement -Wno-pointer-sign -fno-strict-overflow -fconserve-stack -DCC_HAVE_ASM_GOTO -I/tmp/selfgz1809/NVIDIA-Linux-x86_64-295.71/kernel -Wall -MD -Wsign-compare -Wno-cast-qua
   l -Wno-error -D__KERNEL__ -DMODULE -DNVRM -DNV_VERSION_STRING=\"295.71\" -Wno-unused-function -Wuninitialized -mno-red-zone -mcmodel=kernel -UDEBUG -U_DEBUG -DNDEBUG  -DMODULE  -D"KBUILD_STR(s)=#s" -D"KBUILD_BASENAME=KBUILD_STR(os_smp)"  -D"KBUILD_MODNAME=KBUILD_STR(nvidia)" -c -o /tmp/selfgz1809/NVIDIA-Linux-x86_64-295.71/kernel/.tmp_os-smp.o /tmp/selfgz1809/NVIDIA-Linux-x86_64-295.71/kernel/os-smp.c
   In file included from include/linux/kernel.h:17:0,
                    from include/linux/sched.h:55,
                    from include/linux/utsname.h:35,
                    from /tmp/selfgz1809/NVIDIA-Linux-x86_64-295.71/kernel/nv-linux.h:38,
                    from /tmp/selfgz1809/NVIDIA-Linux-x86_64-295.71/kernel/os-smp.c:15:
   include/linux/bitops.h: In function &#8216;hweight_long&#8217;:
   include/linux/bitops.h:49:41: warning: signed and unsigned type in conditional expression [-Wsign-compare]
   In file included from /usr/src/linux-headers-3.2.0-27-generic/arch/x86/include/asm/uaccess.h:575:0,
                    from include/linux/poll.h:14,
                    from /tmp/selfgz1809/NVIDIA-Linux-x86_64-295.71/kernel/nv-linux.h:97,
                    from /tmp/selfgz1809/NVIDIA-Linux-x86_64-295.71/kernel/os-smp.c:15:
   /usr/src/linux-headers-3.2.0-27-generic/arch/x86/include/asm/uaccess_64.h: In function &#8216;copy_from_user&#8217;:
   /usr/src/linux-headers-3.2.0-27-generic/arch/x86/include/asm/uaccess_64.h:53:6: warning: comparison between signed and unsigned integer expressions [-Wsign-compare]
     if [ "-pg" = "-pg" ]; then if [ /tmp/selfgz1809/NVIDIA-Linux-x86_64-295.71/kernel/os-smp.o != "scripts/mod/empty.o" ]; then /usr/src/linux-headers-3.2.0-27-generic/scripts/recordmcount  "/tmp/selfgz1809/NVIDIA-Linux-x86_64-295.71/kernel/os-smp.o"; fi; fi;
     cc -Wp,-MD,/tmp/selfgz1809/NVIDIA-Linux-x86_64-295.71/kernel/.os-usermap.o.d  -nostdinc -isystem /usr/lib/gcc/x86_64-linux-gnu/4.6/include  -I/usr/src/linux-headers-3.2.0-27-generic/arch/x86/include -Iarch/x86/include/generated -Iinclude  -include /usr/src/linux-headers-3.2.0-27-generic/include/linux/kcon
   fig.h -Iubuntu/include  -D__KERNEL__ -Wall -Wundef -Wstrict-prototypes -Wno-trigraphs -fno-strict-aliasing -fno-common -Werror-implicit-function-declaration -Wno-format-security -fno-delete-null-pointer-checks -O2 -m64 -mtune=generic -mno-red-zone -mcmodel=kernel -funit-at-a-time -maccumulate-outgoing-args -fstack-protector -DCONFIG_AS_CFI=1 -DCONFIG_AS_CFI_SIGNAL_FRAME=1 -DCONFIG_AS_CFI_SECTIONS=1 -DCONFIG_AS_FXSAVEQ=1 -pipe -Wno-sign-compare -fno-asynchronous-unwind-tables -mno-sse -mno-mmx -mno-sse2 -mno-3dnow -Wframe-larger-than=1024 -Wno-unused-but-set-variable -fno-omit-frame-pointer -fno-optimize-sibling-calls -pg -Wdeclaration-after-statement -Wno-pointer-sign -fno-strict-overflow -fconserve-stack -DCC_HAVE_ASM_GOTO -I/tmp/selfgz1809/NVIDIA-Linux-x86_64-295.71/kernel -Wall -MD -Wsign-compare -Wno-cast-qual -Wno-error -D__KERNEL__ -DMODULE -DNVRM -DNV_VERSION_STRING=\"295.71\" -Wno-unused-function -Wuninitialized -mno-red-zone -mcmodel=kernel -UDEBUG -U_DEBUG -DNDEBUG  -DMODULE  -D"KBUILD_STR(s)=#s" -D
   "KBUILD_BASENAME=KBUILD_STR(os_usermap)"  -D"KBUILD_MODNAME=KBUILD_STR(nvidia)" -c -o /tmp/selfgz1809/NVIDIA-Linux-x86_64-295.71/kernel/.tmp_os-usermap.o /tmp/selfgz1809/NVIDIA-Linux-x86_64-295.71/kernel/os-usermap.c
   In file included from include/linux/kernel.h:17:0,
                    from include/linux/sched.h:55,
                    from include/linux/utsname.h:35,
                    from /tmp/selfgz1809/NVIDIA-Linux-x86_64-295.71/kernel/nv-linux.h:38,
                    from /tmp/selfgz1809/NVIDIA-Linux-x86_64-295.71/kernel/os-usermap.c:15:
   include/linux/bitops.h: In function &#8216;hweight_long&#8217;:
   include/linux/bitops.h:49:41: warning: signed and unsigned type in conditional expression [-Wsign-compare]
   In file included from /usr/src/linux-headers-3.2.0-27-generic/arch/x86/include/asm/uaccess.h:575:0,
                    from include/linux/poll.h:14,
                    from /tmp/selfgz1809/NVIDIA-Linux-x86_64-295.71/kernel/nv-linux.h:97,
                    from /tmp/selfgz1809/NVIDIA-Linux-x86_64-295.71/kernel/os-usermap.c:15:
   /usr/src/linux-headers-3.2.0-27-generic/arch/x86/include/asm/uaccess_64.h: In function &#8216;copy_from_user&#8217;:
   /usr/src/linux-headers-3.2.0-27-generic/arch/x86/include/asm/uaccess_64.h:53:6: warning: comparison between signed and unsigned integer expressions [-Wsign-compare]
     if [ "-pg" = "-pg" ]; then if [ /tmp/selfgz1809/NVIDIA-Linux-x86_64-295.71/kernel/os-usermap.o != "scripts/mod/empty.o" ]; then /usr/src/linux-headers-3.2.0-27-generic/scripts/recordmcount  "/tmp/selfgz1809/NVIDIA-Linux-x86_64-295.71/kernel/os-usermap.o"; fi; fi;
     ld -m elf_x86_64   -r -o /tmp/selfgz1809/NVIDIA-Linux-x86_64-295.71/kernel/nvidia.o /tmp/selfgz1809/NVIDIA-Linux-x86_64-295.71/kernel/nv-kernel.o /tmp/selfgz1809/NVIDIA-Linux-x86_64-295.71/kernel/nv.o /tmp/selfgz1809/NVIDIA-Linux-x86_64-295.71/kernel/nv-acpi.o /tmp/selfgz1809/NVIDIA-Linux-x86_64-295.71/kernel/nv-chrdev.o /tmp/selfgz1809/NVIDIA-Linux-x86_64-295.71/kernel/nv-cray.o /tmp/selfgz1809/NVIDIA-Linux-x86_64-295.71/kernel/nv-gvi.o /tmp/selfgz1809/NVIDIA-Linux-x86_64-
   295.71/kernel/nv-i2c.o /tmp/selfgz1809/NVIDIA-Linux-x86_64-295.71/kernel/nv-mempool.o /tmp/selfgz1809/NVIDIA-Linux-x86_64-295.71/kernel/nv-mlock.o /tmp/selfgz1809/NVIDIA-Linux-x86_64-295.71/kernel/nv-mmap.o /tmp/selfgz1809/NVIDIA-Linux-x86_64-295.71/kernel/nv-p2p.o /tmp/selfgz1809/NVIDIA-Linux-x86_64-295.71/kernel/nv-pat.o /tmp/selfgz1809/NVIDIA-Linux-x86_64-295.71/kernel/nv-procfs.o /tmp/selfgz1809/NVIDIA-Linux-x86_64-295.71/kernel/nv-usermap.o /tmp/selfgz1809/NVIDIA-Linux-x86_64-295.71/kernel/nv-vm.o /tmp/selfgz1809/NVIDIA-Linux-x86_64-295.71/kernel/nv-vtophys.o /tmp/selfgz1809/NVIDIA-Linux-x86_64-295.71/kernel/os-agp.o /tmp/selfgz1809/NVIDIA-Linux-x86_64-295.71/kernel/os-interface.o /tmp/selfgz1809/NVIDIA-Linux-x86_64-295.71/kernel/os-mtrr.o /tmp/selfgz1809/NVIDIA-Linux-x86_64-295.71/kernel/os-registry.o /tmp/selfgz1809/NVIDIA-Linux-x86_64-295.71/kernel/os-smp.o /tmp/selfgz1809/NVIDIA-Linux-x86_64-295.71/kernel/os-usermap.o 
   (cat /dev/null;   echo kernel//tmp/selfgz1809/NVIDIA-Linux-x86_64-295.71/kernel/nvidia.ko;) > /tmp/selfgz1809/NVIDIA-Linux-x86_64-295.71/kernel/modules.order
   make -f /usr/src/linux-headers-3.2.0-27-generic/scripts/Makefile.modpost
     scripts/mod/modpost -m -a -i /usr/src/linux-headers-3.2.0-27-generic/Module.symvers -I /tmp/selfgz1809/NVIDIA-Linux-x86_64-295.71/kernel/Module.symvers  -o /tmp/selfgz1809/NVIDIA-Linux-x86_64-295.71/kernel/Module.symvers -S -w  -s
   WARNING: could not find /tmp/selfgz1809/NVIDIA-Linux-x86_64-295.71/kernel/.nv-kernel.o.cmd for /tmp/selfgz1809/NVIDIA-Linux-x86_64-295.71/kernel/nv-kernel.o
     cc -Wp,-MD,/tmp/selfgz1809/NVIDIA-Linux-x86_64-295.71/kernel/.nvidia.mod.o.d  -nostdinc -isystem /usr/lib/gcc/x86_64-linux-gnu/4.6/include  -I/usr/src/linux-headers-3.2.0-27-generic/arch/x86/include -Iarch/x86/include/generated -Iinclude  -include /usr/src/linux-headers-3.2.0-27-generic/include/linux/kconfig.h -Iubuntu/include  -D__KERNEL__ -Wall -Wundef -Wstrict-prototypes -Wno-trigraphs -fno-strict-aliasing -fno-common -Werror-implicit-function-declaration -Wno-format-security
    -fno-delete-null-pointer-checks -O2 -m64 -mtune=generic -mno-red-zone -mcmodel=kernel -funit-at-a-time -maccumulate-outgoing-args -fstack-protector -DCONFIG_AS_CFI=1 -DCONFIG_AS_CFI_SIGNAL_FRAME=1 -DCONFIG_AS_CFI_SECTIONS=1 -DCONFIG_AS_FXSAVEQ=1 -pipe -Wno-sign-compare -fno-asynchronous-unwind-tables -mno-sse -mno-mmx -mno-sse2 -mno-3dnow -Wframe-larger-than=1024 -Wno-unused-but-set-variable -fno-omit-frame-pointer -fno-optimize-sibling-calls -pg -Wdeclaration-after-statement -Wno-pointer-sign -fno-strict-overflow -fconserve-stack -DCC_HAVE_ASM_GOTO -I/tmp/selfgz1809/NVIDIA-Linux-x86_64-295.71/kernel -Wall -MD -Wsign-compare -Wno-cast-qual -Wno-error -D__KERNEL__ -DMODULE -DNVRM -DNV_VERSION_STRING=\"295.71\" -Wno-unused-function -Wuninitialized -mno-red-zone -mcmodel=kernel -UDEBUG -U_DEBUG -DNDEBUG  -D"KBUILD_STR(s)=#s" -D"KBUILD_BASENAME=KBUILD_STR(nvidia.mod)"  -D"KBUILD_MODNAME=KBUILD_STR(nvidia)" -DMODULE  -c -o /tmp/selfgz1809/NVIDIA-Linux-x86_64-295.71/kernel/nvidia.mod.o /tmp/selfgz1809/NVIDIA-Linux
   -x86_64-295.71/kernel/nvidia.mod.c
   In file included from include/linux/kernel.h:17:0,
                    from include/linux/cache.h:4,
                    from include/linux/time.h:7,
                    from include/linux/stat.h:60,
                    from include/linux/module.h:10,
                    from /tmp/selfgz1809/NVIDIA-Linux-x86_64-295.71/kernel/nvidia.mod.c:1:
   include/linux/bitops.h: In function &#8216;hweight_long&#8217;:
   include/linux/bitops.h:49:41: warning: signed and unsigned type in conditional expression [-Wsign-compare]
     ld -r -m elf_x86_64 -T /usr/src/linux-headers-3.2.0-27-generic/scripts/module-common.lds --build-id  -o /tmp/selfgz1809/NVIDIA-Linux-x86_64-295.71/kernel/nvidia.ko /tmp/selfgz1809/NVIDIA-Linux-x86_64-295.71/kernel/nvidia.o /tmp/selfgz1809/NVIDIA-Linux-x86_64-295.71/kernel/nvidia.mod.o
   NVIDIA: left KBUILD.
-> done.
-> Kernel module compilation complete.
-> Kernel messages:
[   16.844519] input: HDA NVidia Line-Out Surround as /devices/pci0000:00/0000:00:06.1/sound/card0/input13
[   16.844576] input: HDA NVidia Line-Out Front as /devices/pci0000:00/0000:00:06.1/sound/card0/input14
[   16.845243] ACPI: PCI Interrupt Link [APC7] enabled at IRQ 16
[   16.845250] snd_hda_intel 0000:05:00.1: PCI INT B -> Link[APC7] -> GSI 16 (level, low) -> IRQ 16
[   16.845253] hda_intel: Disabling MSI
[   16.845304] snd_hda_intel 0000:05:00.1: setting latency timer to 64
[   17.292028] HDMI status: Codec=0 Pin=4 Presence_Detect=0 ELD_Valid=0
[   17.300027] HDMI status: Codec=0 Pin=5 Presence_Detect=0 ELD_Valid=0
[   17.300126] input: HDA NVidia HDMI/DP,pcm=7 as /devices/pci0000:00/0000:00:0f.0/0000:05:00.1/sound/card1/input15
[   17.300286] input: HDA NVidia HDMI/DP,pcm=3 as /devices/pci0000:00/0000:00:0f.0/0000:05:00.1/sound/card1/input16
[   17.765580] vesafb: mode is 1280x800x32, linelength=5120, pages=0
[   17.765584] vesafb: scrolling: redraw
[   17.765587] vesafb: Truecolor: size=8:8:8:8, shift=24:16:8:0
[   17.766435] vesafb: framebuffer at 0xe7000000, mapped to 0xffffc90005880000, using 4032k, total 4032k
[   17.766678] Console: switching to colour frame buffer device 160x50
[   17.766700] fb0: VESA VGA frame buffer device
[   17.785124] init: plymouth-splash main process (1373) terminated with status 1
[   17.799552] init: lightdm main process (1378) killed by TERM signal
[   26.368015] eth0: no IPv6 routers present
[   72.717330] nvidia 0000:05:00.0: PCI INT A disabled
[  108.631411] nvidia 0000:05:00.0: PCI INT A -> Link[APC6] -> GSI 16 (level, low) -> IRQ 16
[  108.631422] nvidia 0000:05:00.0: setting latency timer to 64
[  108.631427] vgaarb: device changed decodes: PCI:0000:05:00.0,olddecodes=none,decodes=none:owns=io+mem
[  108.631669] NVRM: loading NVIDIA UNIX x86_64 Kernel Module  295.71  Thu Aug  2 19:22:08 PDT 2012
[  108.637288] nvidia 0000:05:00.0: PCI INT A disabled
-> Installing both new and classic TLS OpenGL libraries.
-> Installing classic TLS 32bit OpenGL libraries.
-> Install NVIDIA's 32-bit compatibility OpenGL libraries? (Answer: Yes)
-> Searching for conflicting X files:
-> done.
-> Searching for conflicting OpenGL files:
-> done.
-> Installing 'NVIDIA Accelerated Graphics Driver for Linux-x86_64' (295.71):
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
-> Would you like to run the nvidia-xconfig utility to automatically update your X configuration file so that the NVIDIA X driver will be used when you restart X?  Any pre-existing X configuration file will be backed up. (Answer: Yes)
-> Your X configuration file has been successfully updated.  Installation of the NVIDIA Accelerated Graphics Driver for Linux-x86_64 (version: 295.71) is now complete.[/I]

---

### Post by Jimboland on 2012-08-09
Its partly fixed, 

what I did is follow this guide:
[I][B]First purge your nvidia-current installation.

Reboot. Then:

Posted by whatthefunk on the precise fixes page

Code:
sudo add-apt-repository ppa:ubuntu-x-swat/x-updates
 sudo apt-get update
 sudo apt-get install nvidia-current=295.33-0ubuntu1~precise~xup1[/B][/I]

from [here]("http://ubuntuforums.org/showthread.php?t=1967419&highlight=nvidia").

The only difference I did is:

sudo apt-get install nvidia-current WITHOUT "=295.33-0ubuntu1~precise~xup1"

After that it still didn't work unstill I did:

Sudo apt-get update && sudo apt-get upgrade -y 

En rebooted. After that I could see my screen again.

But now I have an other problem, I'm asked for he password at logon, I enter it and the logon screen keeps comming back.
I allready tried changing the password, and the guest account is working fine. So I have to find the solution for that as well.

---

