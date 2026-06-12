---
title: "nvidia or general problem"
date: 2012-02-15
forum: General Help
---

### Post by eugene10010 on 2012-02-15
hi guys and girls, i might have a problem but i'm not sure if this belongs here please let me know wher if not here.. so here it is.
i have a dell 1530 with nvidia 8400m gs video board in it and everytime i  use apt-get install ______ no matter what it is it'll always somehow  mess my gui up. here's my last attempt at trying apt-get install  nvidia-current: 


Desktop# apt-get install nvidia-current
Reading package lists... Done
Building dependency tree       
Reading state information... Done
nvidia-current is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 2 not upgraded.
1 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Setting up nvidia-current (195.36.24-0ubuntu1~10.04) ...
update-initramfs: deferring update (trigger activated)
Removing old nvidia-current-195.36.24 DKMS files...

------------------------------
Deleting module version: 195.36.24
completely from the DKMS tree.
------------------------------
Done.
Loading new nvidia-current-195.36.24 DKMS files...
First Installation: checking all kernels...
Building only for 2.6.39.4
Building for architecture x86_64
Building initial module for 2.6.39.4

Error! Bad return status for module build on kernel: 2.6.39.4 (x86_64)
Consult the make.log in the build directory
/var/lib/dkms/nvidia-current/195.36.24/build/ for more information.
dpkg: error processing nvidia-current (--configure):
 subprocess installed post-installation script returned error exit status 10
Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-2.6.39.4
Errors were encountered while processing:
 nvidia-current
E: Sub-process /usr/bin/dpkg returned an error code (1)








and here's the output of make.log for just in case you'd need it:

var/lib/dkms/nvidia-current/195.36.24/build# cat make.log 
DKMS make.log for nvidia-current-195.36.24 for kernel 2.6.39.4 (x86_64)
Tue Feb 14 15:28:15 PST 2012
NVIDIA: calling KBUILD...
test -e include/generated/autoconf.h -a -e include/config/auto.conf || (       \
        echo;                                                           \
        echo "  ERROR: Kernel configuration is invalid.";               \
        echo "         include/generated/autoconf.h or include/config/auto.conf are missing.";\
        echo "         Run 'make oldconfig && make prepare' on kernel src to fix it.";  \
        echo;                                                           \
        /bin/false)
mkdir -p /var/lib/dkms/nvidia-current/195.36.24/build/.tmp_versions ; rm  -f /var/lib/dkms/nvidia-current/195.36.24/build/.tmp_versions/*
 
  WARNING: Symbol version dump /usr/src/linux-source-2.6.39.4/Module.symvers
           is missing; modules will have no dependencies and modversions.

make -f scripts/Makefile.build obj=/var/lib/dkms/nvidia-current/195.36.24/build
  cc -Wp,-MD,/var/lib/dkms/nvidia-current/195.36.24/build/.nv.o.d   -nostdinc -isystem /usr/lib/gcc/x86_64-linux-gnu/4.4.3/include  -I/usr/src/linux-source-2.6.39.4/arch/x86/include -Iinclude  -include  include/generated/autoconf.h -D__KERNEL__ -Wall -Wundef  -Wstrict-prototypes -Wno-trigraphs -fno-strict-aliasing -fno-common  -Werror-implicit-function-declaration -Wno-format-security  -fno-delete-null-pointer-checks -O2 -m64 -mtune=generic -mno-red-zone  -mcmodel=kernel -funit-at-a-time -maccumulate-outgoing-args  -fstack-protector -DCONFIG_AS_CFI=1 -DCONFIG_AS_CFI_SIGNAL_FRAME=1  -DCONFIG_AS_CFI_SECTIONS=1 -DCONFIG_AS_FXSAVEQ=1 -pipe -Wno-sign-compare  -fno-asynchronous-unwind-tables -mno-sse -mno-mmx -mno-sse2 -mno-3dnow  -Wframe-larger-than=1024 -fno-omit-frame-pointer  -fno-optimize-sibling-calls -pg -Wdeclaration-after-statement  -Wno-pointer-sign -fno-strict-overflow -fconserve-stack  -I/var/lib/dkms/nvidia-current/195.36.24/build -Wall -Wimplicit  -Wreturn-type -Wswitch -Wformat -Wchar-subscripts -Wparentheses  -Wpointer-arith -Wno-multichar -Werror -mcmodel=kernel -mno-red-zone  -fno-defer-pop -MD -Wsign-compare -Wno-cast-qual -Wno-error -D__KERNEL__  -DMODULE -DNVRM -DNV_VERSION_STRING=\"195.36.24\" -UDEBUG -U_DEBUG  -DNDEBUG  -DMODULE  -D"KBUILD_STR(s)=#s"  -D"KBUILD_BASENAME=KBUILD_STR(nv)"   -D"KBUILD_MODNAME=KBUILD_STR(nvidia)" -c -o  /var/lib/dkms/nvidia-current/195.36.24/build/nv.o  /var/lib/dkms/nvidia-current/195.36.24/build/nv.c
In file included from include/linux/bitops.h:22,
                 from include/linux/kernel.h:17,
                 from include/linux/sched.h:55,
                 from include/linux/utsname.h:35,
                 from /var/lib/dkms/nvidia-current/195.36.24/build/nv-linux.h:27,
                  from /var/lib/dkms/nvidia-current/195.36.24/build/nv.c:14:
/usr/src/linux-source-2.6.39.4/arch/x86/include/asm/bitops.h:  In function ‘set_bit’:
/usr/src/linux-source-2.6.39.4/arch/x86/include/asm/bitops.h: 64: warning: pointer of type ‘void *’ used in arithmetic
/usr/src/linux-source-2.6.39.4/arch/x86/include/asm/bitops.h:  In function ‘clear_bit’:
/usr/src/linux-source-2.6.39.4/arch/x86/include/asm/bitops.h: 102: warning: pointer of type ‘void *’ used in arithmetic
/usr/src/linux-source-2.6.39.4/arch/x86/include/asm/bitops.h:  In function ‘change_bit’:
/usr/src/linux-source-2.6.39.4/arch/x86/include/asm/bitops.h: 178: warning: pointer of type ‘void *’ used in arithmetic
In file included from include/linux/kernel.h:17,
                 from include/linux/sched.h:55,
                 from include/linux/utsname.h:35,
                 from /var/lib/dkms/nvidia-current/195.36.24/build/nv-linux.h:27,
                  from /var/lib/dkms/nvidia-current/195.36.24/build/nv.c:14:
include/linux/bitops.h: In function ‘hweight_long’:
include/linux/bitops.h:49: warning: signed and unsigned type in conditional expression
In file included from include/linux/preempt.h:11,
                 from include/linux/spinlock.h:50,
                 from include/linux/seqlock.h:29,
                 from include/linux/time.h:8,
                 from include/linux/timex.h:56,
                 from include/linux/sched.h:57,
                 from include/linux/utsname.h:35,
                 from /var/lib/dkms/nvidia-current/195.36.24/build/nv-linux.h:27,
                  from /var/lib/dkms/nvidia-current/195.36.24/build/nv.c:14:
include/linux/list.h: In function ‘list_del’:
include/linux/list.h:107: warning: pointer of type ‘void *’ used in arithmetic
include/linux/list.h:108: warning: pointer of type ‘void *’ used in arithmetic
include/linux/list.h: In function ‘hlist_del’:
include/linux/list.h:602: warning: pointer of type ‘void *’ used in arithmetic
include/linux/list.h:603: warning: pointer of type ‘void *’ used in arithmetic
In file included from include/linux/sched.h:82,
                 from include/linux/utsname.h:35,
                 from /var/lib/dkms/nvidia-current/195.36.24/build/nv-linux.h:27,
                  from /var/lib/dkms/nvidia-current/195.36.24/build/nv.c:14:
include/linux/rculist.h: In function ‘list_del_rcu’:
include/linux/rculist.h:112: warning: pointer of type ‘void *’ used in arithmetic
include/linux/rculist.h: In function ‘list_replace_rcu’:
include/linux/rculist.h:158: warning: pointer of type ‘void *’ used in arithmetic
include/linux/rculist.h: In function ‘hlist_del_rcu’:
include/linux/rculist.h:312: warning: pointer of type ‘void *’ used in arithmetic
include/linux/rculist.h: In function ‘hlist_replace_rcu’:
include/linux/rculist.h:332: warning: pointer of type ‘void *’ used in arithmetic
In file included from include/linux/utsname.h:35,
                 from /var/lib/dkms/nvidia-current/195.36.24/build/nv-linux.h:27,
                  from /var/lib/dkms/nvidia-current/195.36.24/build/nv.c:14:
include/linux/sched.h: In function ‘object_is_on_stack’:
include/linux/sched.h:2327: warning: pointer of type ‘void *’ used in arithmetic
In file included from include/linux/rculist_bl.h:7,
                 from include/linux/dcache.h:7,
                 from include/linux/fs.h:377,
                 from include/linux/poll.h:12,
                 from /var/lib/dkms/nvidia-current/195.36.24/build/nv-linux.h:84,
                  from /var/lib/dkms/nvidia-current/195.36.24/build/nv.c:14:
include/linux/list_bl.h: In function ‘hlist_bl_del’:
include/linux/list_bl.h:106: warning: pointer of type ‘void *’ used in arithmetic
include/linux/list_bl.h:107: warning: pointer of type ‘void *’ used in arithmetic
In file included from include/linux/dcache.h:7,
                 from include/linux/fs.h:377,
                 from include/linux/poll.h:12,
                 from /var/lib/dkms/nvidia-current/195.36.24/build/nv-linux.h:84,
                  from /var/lib/dkms/nvidia-current/195.36.24/build/nv.c:14:
include/linux/rculist_bl.h: In function ‘hlist_bl_del_rcu’:
include/linux/rculist_bl.h:76: warning: pointer of type ‘void *’ used in arithmetic
In file included from /usr/src/linux-source-2.6.39.4/arch/x86/include/asm/uaccess.h: 573,
                 from include/linux/poll.h:14,
                 from /var/lib/dkms/nvidia-current/195.36.24/build/nv-linux.h:84,
                  from /var/lib/dkms/nvidia-current/195.36.24/build/nv.c:14:
/usr/src/linux-source-2.6.39.4/arch/x86/include/asm/uaccess_64. h: In function ‘copy_from_user’:
/usr/src/linux-source-2.6.39.4/arch/x86/include/asm/uaccess_64. h:54: warning: comparison between signed and unsigned integer expressions
In file included from /var/lib/dkms/nvidia-current/195.36.24/build/nv.c:14:
/var/lib/dkms/nvidia-current/195.36.24/build/nv-linux.h:90:75:  error: linux/smp_lock.h: No such file or directory
In file included from include/linux/dma-mapping.h:7,
                 from include/asm-generic/pci-dma-compat.h:7,
                 from /usr/src/linux-source-2.6.39.4/arch/x86/include/asm/pci.h:141, 
                 from include/linux/pci.h:1247,
                 from /var/lib/dkms/nvidia-current/195.36.24/build/nv-linux.h:95,
                  from /var/lib/dkms/nvidia-current/195.36.24/build/nv.c:14:
include/linux/scatterlist.h: In function ‘sg_virt’:
include/linux/scatterlist.h:199: warning: pointer of type ‘void *’ used in arithmetic
In file included from /usr/src/linux-source-2.6.39.4/arch/x86/include/asm/dma-mapping. h:43,
                 from include/linux/dma-mapping.h:93,
                 from include/asm-generic/pci-dma-compat.h:7,
                 from /usr/src/linux-source-2.6.39.4/arch/x86/include/asm/pci.h:141, 
                 from include/linux/pci.h:1247,
                 from /var/lib/dkms/nvidia-current/195.36.24/build/nv-linux.h:95,
                  from /var/lib/dkms/nvidia-current/195.36.24/build/nv.c:14:
include/asm-generic/dma-mapping-common.h: In function ‘dma_map_page’:
include/asm-generic/dma-mapping-common.h:77: warning: pointer of type ‘void *’ used in arithmetic
In file included from /var/lib/dkms/nvidia-current/195.36.24/build/nv-linux.h:126,
                  from /var/lib/dkms/nvidia-current/195.36.24/build/nv.c:14:
include/linux/highmem.h: In function ‘zero_user_segments’:
include/linux/highmem.h:197: warning: pointer of type ‘void *’ used in arithmetic
include/linux/highmem.h:200: warning: pointer of type ‘void *’ used in arithmetic
In file included from include/linux/compat.h:16,
                 from /usr/src/linux-source-2.6.39.4/arch/x86/include/asm/mtrr.h:173, 
                 from /var/lib/dkms/nvidia-current/195.36.24/build/nv-linux.h:161,
                  from /var/lib/dkms/nvidia-current/195.36.24/build/nv.c:14:
/usr/src/linux-source-2.6.39.4/arch/x86/include/asm/compat.h:  In function ‘arch_compat_alloc_user_space’:
/usr/src/linux-source-2.6.39.4/arch/x86/include/asm/compat.h: 211: warning: pointer of type ‘void *’ used in arithmetic
/var/lib/dkms/nvidia-current/195.36.24/build/nv.c: At top level:
/var/lib/dkms/nvidia-current/195.36.24/build/nv.c:417: error: unknown field ‘ioctl’ specified in initializer
/var/lib/dkms/nvidia-current/195.36.24/build/nv.c:417: warning: initialization from incompatible pointer type
make[3]: *** [/var/lib/dkms/nvidia-current/195.36.24/build/nv.o] Error 1
make[2]: *** [_module_/var/lib/dkms/nvidia-current/195.36.24/build] Error 2
NVIDIA: left KBUILD.
nvidia.ko failed to build!
make[1]: *** [module] Error 1
make: *** [module] Error 2

---

### Post by grahammechanical on 2012-02-15
What version of Ubuntu are you using? Is it 10.04? Have you tired using the Additional Drivers Utility to activate the driver?

Regards.

---

### Post by Axis Mann on 2012-02-16
I recently installed an Nvidia 8400 GS 512MB for Lucid (10.04) 32 bit.  Lucid was automatically loading the Nouveau driver.  Once that driver gets loaded, none of the tips that anybody had to offer appeared to work for me.  Once I figured out how to prevent the Nouveau driver from loading, I was able to install the latest driver from Nvidia for my video card.  I just kind of bumbled through it.  All those tips people give work for their setup, not yours.  Nvidia seems to be particularly bohersome.  I ended up creating an xorg.conf file and placed it in the /etc/X11 directory in an attempt to prevent Nouveau from loading.  You may already have one present which is loading the driver for you previous setup.   I was shooting for the vesa driver instead.  I also black listed the Nouveau driver although I'm not sure if that was really necessary.   When I rebooted, I held down on the shift key to get to the grub menu where I selected recovery mode and then an option for root without network support (I think).  I then used the sh command to run the driver I downloaded which I think was NVIDIA-Linux-x86-290.10.run and I accepted any suggestions to take a particular action.  The key to the whole solution is to prevent that Nouveau driver from loading and doing a modeset after which all the procedures I folllowed to install the nvidia driver would fail.  I only found a couple examples of loading the nvidia driver that involved preventing the Nouveau driver from loading first.  You might be having a similar problem.  Google the web and look for the instances where someone mentions you have to prevent Nouveau from loading.  There aren't many but if you try what worked for everyone else loading drivers for some other vendor, you will most likely fail as everyone else is doing who tries to load nvidia driver for 3d support.  I used sudo lshw -C Video command to see what driver was installed to start with.  Unfortunately, you reported that you couldn't even get it to boot to the desktop after you installed the Nvidia card so until you resolve that problem, these instructions are of little help.  Good luck!  It took me several days and as many attempts to eventually figure out a procedure that worked for me.  I ended up reloading Ubuntu several times before I finally got it to work with the nvidia driver.  I'm still a Linux newbie!

---

