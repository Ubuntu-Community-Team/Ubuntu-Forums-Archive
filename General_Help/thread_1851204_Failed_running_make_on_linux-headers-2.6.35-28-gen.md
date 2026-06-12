---
title: "Failed running make on linux-headers-2.6.35-28-generic"
date: 2011-09-27
forum: General Help
---

### Post by avenpace on 2011-09-27
So I got power outage several days ago and it made my ext4 main root partition keep having Filesystem state: not clean
That flag keep there although I've run e2fsck dozen of times so in the end I disable the ext4 journal
But when I finally manage to boot my ubuntu main root partition, I found lost quite amount of files and had to reinstall it again
The most frustrating is when I tried to install virtualbox where it need to compile it kernel module
Running "/etc/init.d/vboxdriver setup" gave me following

> 
Uninstalling modules from DKMS
  removing old DKMS module vboxhost version  4.1.2

------------------------------
Deleting module version: 4.1.2
completely from the DKMS tree.
------------------------------
Done.
Attempting to install using DKMS

Creating symlink /var/lib/dkms/vboxhost/4.1.2/source ->
                 /usr/src/vboxhost-4.1.2

DKMS: add Completed.

Kernel preparation unnecessary for this kernel.  Skipping...

Building module:
cleaning build area....
make KERNELRELEASE=2.6.35-28-generic -C /lib/modules/2.6.35-28-generic/build M=/var/lib/dkms/vboxhost/4.1.2/build....(bad exit status: 2)
0
0
Failed to install using DKMS, attempting to install without
make KBUILD_VERBOSE=1 SUBDIRS=/tmp/vbox.0 SRCROOT=/tmp/vbox.0 -C /lib/modules/2.6.35-28-generic/build modules
test -e include/generated/autoconf.h -a -e include/config/auto.conf || (		\
	echo;								\
	echo "  ERROR: Kernel configuration is invalid.";		\
	echo "         include/generated/autoconf.h or include/config/auto.conf are missing.";\
	echo "         Run 'make oldconfig && make prepare' on kernel src to fix it.";	\
	echo;								\
	/bin/false)
mkdir -p /tmp/vbox.0/.tmp_versions ; rm -f /tmp/vbox.0/.tmp_versions/*
make -f scripts/Makefile.build obj=/tmp/vbox.0
  gcc -Wp,-MD,/tmp/vbox.0/linux/.SUPDrv-linux.o.d  -nostdinc -isystem include  -I/usr/src/linux-headers-2.6.35-28-generic/arch/x86/include -Iinclude  -include include/generated/autoconf.h -Iubuntu/include  -D__KERNEL__ -Wall -Wundef -Wstrict-prototypes -Wno-trigraphs -fno-strict-aliasing -fno-common -Werror-implicit-function-declaration -Wno-format-security -fno-delete-null-pointer-checks -O2 -m32 -msoft-float -mregparm=3 -freg-struct-return -mpreferred-stack-boundary=2 -march=i686 -mtune=generic -maccumulate-outgoing-args -Wa,-mtune=generic32 -ffreestanding -fstack-protector -DCONFIG_AS_CFI=1 -DCONFIG_AS_CFI_SIGNAL_FRAME=1 -DCONFIG_AS_CFI_SECTIONS=1 -pipe -Wno-sign-compare -fno-asynchronous-unwind-tables -mno-sse -mno-mmx -mno-sse2 -mno-3dnow -Wframe-larger-than=1024 -fno-omit-frame-pointer -fno-optimize-sibling-calls -pg -Wdeclaration-after-statement -Wno-pointer-sign -fno-strict-overflow -fconserve-stack -include /tmp/vbox.0/include/VBox/SUPDrvMangling.h -I/lib/modules/2.6.35-28-generic/build/include -I/tmp/vbox.0/ -I/tmp/vbox.0/include -I/tmp/vbox.0/r0drv/linux -I/tmp/vbox.0/vboxdrv/ -I/tmp/vbox.0/vboxdrv/include -I/tmp/vbox.0/vboxdrv/r0drv/linux -D__KERNEL__ -DMODULE -DRT_OS_LINUX -DIN_RING0 -DIN_RT_R0 -DIN_SUP_R0 -DVBOX -DRT_WITH_VBOX -DVBOX_WITH_HARDENING -DCONFIG_VBOXDRV_AS_MISC -DRT_ARCH_X86 -DVBOX_WITH_64_BITS_GUESTS  -DMODULE -D"KBUILD_STR(s)=#s" -D"KBUILD_BASENAME=KBUILD_STR(SUPDrv_linux)"  -D"KBUILD_MODNAME=KBUILD_STR(vboxdrv)"  -c -o /tmp/vbox.0/linux/.tmp_SUPDrv-linux.o /tmp/vbox.0/linux/SUPDrv-linux.c
In file included from /tmp/vbox.0/include/VBox/types.h:30,
                 from /tmp/vbox.0/linux/../SUPDrvInternal.h:35,
                 from /tmp/vbox.0/linux/SUPDrv-linux.c:31:
/tmp/vbox.0/include/iprt/types.h:96: fatal error: stddef.h: No such file or directory
compilation terminated.
make[2]: *** [/tmp/vbox.0/linux/SUPDrv-linux.o] Error 1
make[1]: *** [_module_/tmp/vbox.0] Error 2
make: *** [vboxdrv] Error 2


I ran "uname -r" gave me 2.6.35-28-generic
Then I went to /usr/src/linux-headers-2.6.35-28-generic/ and ran "make oldconfig && make prepare" but it throw me errors as follow

> 
  HOSTCC  scripts/basic/fixdep
In file included from scripts/basic/fixdep.c:108:
/usr/include/sys/mman.h:58: error: expected declaration specifiers or ‘...’ before ‘size_t’
/usr/include/sys/mman.h:77: error: expected declaration specifiers or ‘...’ before ‘size_t’
/usr/include/sys/mman.h:82: error: expected declaration specifiers or ‘...’ before ‘size_t’
/usr/include/sys/mman.h:90: error: expected declaration specifiers or ‘...’ before ‘size_t’
/usr/include/sys/mman.h:95: error: expected declaration specifiers or ‘...’ before ‘size_t’
/usr/include/sys/mman.h:99: error: expected declaration specifiers or ‘...’ before ‘size_t’
/usr/include/sys/mman.h:104: error: expected declaration specifiers or ‘...’ before ‘size_t’
/usr/include/sys/mman.h:107: error: expected declaration specifiers or ‘...’ before ‘size_t’
/usr/include/sys/mman.h:124: error: expected declaration specifiers or ‘...’ before ‘size_t’
In file included from scripts/basic/fixdep.c:109:
/usr/include/unistd.h:357: error: expected declaration specifiers or ‘...’ before ‘size_t’
/usr/include/unistd.h:363: error: expected declaration specifiers or ‘...’ before ‘size_t’
/usr/include/unistd.h:373: error: expected declaration specifiers or ‘...’ before ‘size_t’
/usr/include/unistd.h:381: error: expected declaration specifiers or ‘...’ before ‘size_t’
/usr/include/unistd.h:508: error: expected declaration specifiers or ‘...’ before ‘size_t’
In file included from scripts/basic/fixdep.c:109:
/usr/include/unistd.h:620: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘confstr’
/usr/include/unistd.h:793: error: expected declaration specifiers or ‘...’ before ‘size_t’
/usr/include/unistd.h:829: error: expected declaration specifiers or ‘...’ before ‘size_t’
/usr/include/unistd.h:840: error: expected declaration specifiers or ‘...’ before ‘size_t’
/usr/include/unistd.h:876: error: expected declaration specifiers or ‘...’ before ‘size_t’
In file included from scripts/basic/fixdep.c:109:
/usr/include/unistd.h:898: error: expected declaration specifiers or ‘...’ before ‘size_t’
/usr/include/unistd.h:905: error: expected declaration specifiers or ‘...’ before ‘size_t’
/usr/include/unistd.h:916: error: expected declaration specifiers or ‘...’ before ‘size_t’
/usr/include/unistd.h:918: error: expected declaration specifiers or ‘...’ before ‘size_t’
/usr/include/unistd.h:936: error: expected declaration specifiers or ‘...’ before ‘size_t’
/usr/include/unistd.h:937: error: expected declaration specifiers or ‘...’ before ‘size_t’
In file included from /usr/include/unistd.h:1157,
                 from scripts/basic/fixdep.c:109:
/usr/include/bits/unistd.h:24: error: expected declaration specifiers or ‘...’ before ‘size_t’
/usr/include/bits/unistd.h:25: error: expected declaration specifiers or ‘...’ before ‘size_t’
/usr/include/bits/unistd.h:26: error: expected declaration specifiers or ‘...’ before ‘size_t’
/usr/include/bits/unistd.h:28: error: expected declaration specifiers or ‘...’ before ‘size_t’
/usr/include/bits/unistd.h:28: error: expected declaration specifiers or ‘...’ before ‘size_t’
/usr/include/bits/unistd.h:35: error: expected declaration specifiers or ‘...’ before ‘size_t’
/usr/include/bits/unistd.h: In function ‘read’:
/usr/include/bits/unistd.h:37: error: ‘size_t’ undeclared (first use in this function)
/usr/include/bits/unistd.h:37: error: (Each undeclared identifier is reported only once
/usr/include/bits/unistd.h:37: error: for each function it appears in.)
/usr/include/bits/unistd.h:39: error: ‘__nbytes’ undeclared (first use in this function)
/usr/include/bits/unistd.h:40: error: too many arguments to function ‘__read_chk’
/usr/include/bits/unistd.h:43: error: too many arguments to function ‘__read_chk_warn’
/usr/include/bits/unistd.h:45: error: too many arguments to function ‘__read_alias’
/usr/include/bits/unistd.h: At top level:
/usr/include/bits/unistd.h:125: error: expected declaration specifiers or ‘...’ before ‘size_t’
/usr/include/bits/unistd.h:126: error: expected declaration specifiers or ‘...’ before ‘size_t’
/usr/include/bits/unistd.h:128: error: expected declaration specifiers or ‘...’ before ‘size_t’
/usr/include/bits/unistd.h:132: error: expected declaration specifiers or ‘...’ before ‘size_t’
/usr/include/bits/unistd.h:132: error: expected declaration specifiers or ‘...’ before ‘size_t’
/usr/include/bits/unistd.h:140: error: expected declaration specifiers or ‘...’ before ‘size_t’
/usr/include/bits/unistd.h: In function ‘readlink’:
/usr/include/bits/unistd.h:143: error: ‘size_t’ undeclared (first use in this function)
/usr/include/bits/unistd.h:145: error: ‘__len’ undeclared (first use in this function)
/usr/include/bits/unistd.h:146: error: too many arguments to function ‘__readlink_chk’
/usr/include/bits/unistd.h:149: error: too many arguments to function ‘__readlink_chk_warn’
/usr/include/bits/unistd.h:151: error: too many arguments to function ‘__readlink_alias’
/usr/include/bits/unistd.h: At top level:
/usr/include/bits/unistd.h:157: error: expected declaration specifiers or ‘...’ before ‘size_t’
/usr/include/bits/unistd.h:158: error: expected declaration specifiers or ‘...’ before ‘size_t’
/usr/include/bits/unistd.h:160: error: expected declaration specifiers or ‘...’ before ‘size_t’
/usr/include/bits/unistd.h:165: error: expected declaration specifiers or ‘...’ before ‘size_t’
/usr/include/bits/unistd.h:165: error: expected declaration specifiers or ‘...’ before ‘size_t’
/usr/include/bits/unistd.h:174: error: expected declaration specifiers or ‘...’ before ‘size_t’
/usr/include/bits/unistd.h: In function ‘readlinkat’:
/usr/include/bits/unistd.h:177: error: ‘size_t’ undeclared (first use in this function)
/usr/include/bits/unistd.h:179: error: ‘__len’ undeclared (first use in this function)
/usr/include/bits/unistd.h:180: error: too many arguments to function ‘__readlinkat_chk’
/usr/include/bits/unistd.h:184: error: too many arguments to function ‘__readlinkat_chk_warn’
/usr/include/bits/unistd.h:186: error: too many arguments to function ‘__readlinkat_alias’
/usr/include/bits/unistd.h: At top level:
/usr/include/bits/unistd.h:190: error: expected declaration specifiers or ‘...’ before ‘size_t’
/usr/include/bits/unistd.h:190: error: expected declaration specifiers or ‘...’ before ‘size_t’
/usr/include/bits/unistd.h:192: error: expected declaration specifiers or ‘...’ before ‘size_t’
/usr/include/bits/unistd.h:194: error: expected declaration specifiers or ‘...’ before ‘size_t’
/usr/include/bits/unistd.h:194: error: expected declaration specifiers or ‘...’ before ‘size_t’
/usr/include/bits/unistd.h:201: error: expected declaration specifiers or ‘...’ before ‘size_t’
/usr/include/bits/unistd.h: In function ‘getcwd’:
/usr/include/bits/unistd.h:203: error: ‘size_t’ undeclared (first use in this function)
/usr/include/bits/unistd.h:205: error: ‘__size’ undeclared (first use in this function)
/usr/include/bits/unistd.h:206: error: too many arguments to function ‘__getcwd_chk’
/usr/include/bits/unistd.h:209: error: too many arguments to function ‘__getcwd_chk_warn’
/usr/include/bits/unistd.h:211: error: too many arguments to function ‘__getcwd_alias’
/usr/include/bits/unistd.h: At top level:
/usr/include/bits/unistd.h:215: error: expected declaration specifiers or ‘...’ before ‘size_t’
/usr/include/bits/unistd.h: In function ‘getwd’:
/usr/include/bits/unistd.h:224: error: ‘size_t’ undeclared (first use in this function)
/usr/include/bits/unistd.h:225: error: too many arguments to function ‘__getwd_chk’
/usr/include/bits/unistd.h: At top level:
/usr/include/bits/unistd.h:230: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘__confstr_chk’
/usr/include/bits/unistd.h:232: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘__confstr_alias’
/usr/include/bits/unistd.h:234: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘__confstr_chk_warn’
/usr/include/bits/unistd.h:241: error: expected ‘,’ or ‘;’ before ‘confstr’
/usr/include/bits/unistd.h:255: error: expected declaration specifiers or ‘...’ before ‘size_t’
/usr/include/bits/unistd.h:259: error: expected declaration specifiers or ‘...’ before ‘size_t’
/usr/include/bits/unistd.h: In function ‘getgroups’:
/usr/include/bits/unistd.h:271: error: too many arguments to function ‘__getgroups_chk’
/usr/include/bits/unistd.h:274: error: too many arguments to function ‘__getgroups_chk_warn’
/usr/include/bits/unistd.h: At top level:
/usr/include/bits/unistd.h:280: error: expected declaration specifiers or ‘...’ before ‘size_t’
/usr/include/bits/unistd.h:281: error: expected declaration specifiers or ‘...’ before ‘size_t’
/usr/include/bits/unistd.h:282: error: expected declaration specifiers or ‘...’ before ‘size_t’
/usr/include/bits/unistd.h:285: error: expected declaration specifiers or ‘...’ before ‘size_t’
/usr/include/bits/unistd.h:285: error: expected declaration specifiers or ‘...’ before ‘size_t’
/usr/include/bits/unistd.h:292: error: expected declaration specifiers or ‘...’ before ‘size_t’
/usr/include/bits/unistd.h: In function ‘ttyname_r’:
/usr/include/bits/unistd.h:296: error: ‘__buflen’ undeclared (first use in this function)
/usr/include/bits/unistd.h:297: error: too many arguments to function ‘__ttyname_r_chk’
/usr/include/bits/unistd.h:300: error: too many arguments to function ‘__ttyname_r_chk_warn’
/usr/include/bits/unistd.h:302: error: too many arguments to function ‘__ttyname_r_alias’
/usr/include/bits/unistd.h: At top level:
/usr/include/bits/unistd.h:307: error: expected declaration specifiers or ‘...’ before ‘size_t’
/usr/include/bits/unistd.h:307: error: expected declaration specifiers or ‘...’ before ‘size_t’
/usr/include/bits/unistd.h:309: error: expected declaration specifiers or ‘...’ before ‘size_t’
/usr/include/bits/unistd.h:311: error: expected declaration specifiers or ‘...’ before ‘size_t’
/usr/include/bits/unistd.h:311: error: expected declaration specifiers or ‘...’ before ‘size_t’
/usr/include/bits/unistd.h:318: error: expected declaration specifiers or ‘...’ before ‘size_t’
/usr/include/bits/unistd.h: In function ‘getlogin_r’:
/usr/include/bits/unistd.h:322: error: ‘__buflen’ undeclared (first use in this function)
/usr/include/bits/unistd.h:323: error: too many arguments to function ‘__getlogin_r_chk’
/usr/include/bits/unistd.h:326: error: too many arguments to function ‘__getlogin_r_chk_warn’
/usr/include/bits/unistd.h:328: error: too many arguments to function ‘__getlogin_r_alias’
/usr/include/bits/unistd.h: At top level:
/usr/include/bits/unistd.h:334: error: expected declaration specifiers or ‘...’ before ‘size_t’
/usr/include/bits/unistd.h:334: error: expected declaration specifiers or ‘...’ before ‘size_t’
/usr/include/bits/unistd.h:336: error: expected declaration specifiers or ‘...’ before ‘size_t’
/usr/include/bits/unistd.h:338: error: expected declaration specifiers or ‘...’ before ‘size_t’
/usr/include/bits/unistd.h:338: error: expected declaration specifiers or ‘...’ before ‘size_t’
/usr/include/bits/unistd.h:345: error: expected declaration specifiers or ‘...’ before ‘size_t’
/usr/include/bits/unistd.h: In function ‘gethostname’:
/usr/include/bits/unistd.h:349: error: ‘__buflen’ undeclared (first use in this function)
/usr/include/bits/unistd.h:350: error: too many arguments to function ‘__gethostname_chk’
/usr/include/bits/unistd.h:353: error: too many arguments to function ‘__gethostname_chk_warn’
/usr/include/bits/unistd.h:355: error: too many arguments to function ‘__gethostname_alias’
/usr/include/bits/unistd.h: At top level:
/usr/include/bits/unistd.h:361: error: expected declaration specifiers or ‘...’ before ‘size_t’
/usr/include/bits/unistd.h:361: error: expected declaration specifiers or ‘...’ before ‘size_t’
/usr/include/bits/unistd.h:363: error: expected declaration specifiers or ‘...’ before ‘size_t’
/usr/include/bits/unistd.h:366: error: expected declaration specifiers or ‘...’ before ‘size_t’
/usr/include/bits/unistd.h:366: error: expected declaration specifiers or ‘...’ before ‘size_t’
/usr/include/bits/unistd.h:374: error: expected declaration specifiers or ‘...’ before ‘size_t’
/usr/include/bits/unistd.h: In function ‘getdomainname’:
/usr/include/bits/unistd.h:378: error: ‘__buflen’ undeclared (first use in this function)
/usr/include/bits/unistd.h:379: error: too many arguments to function ‘__getdomainname_chk’
/usr/include/bits/unistd.h:382: error: too many arguments to function ‘__getdomainname_chk_warn’
/usr/include/bits/unistd.h:384: error: too many arguments to function ‘__getdomainname_alias’
In file included from scripts/basic/fixdep.c:111:
/usr/include/string.h: At top level:
/usr/include/string.h:45: error: expected declaration specifiers or ‘...’ before ‘size_t’
/usr/include/string.h:49: error: expected declaration specifiers or ‘...’ before ‘size_t’
/usr/include/string.h:58: error: expected declaration specifiers or ‘...’ before ‘size_t’
/usr/include/string.h:65: error: expected declaration specifiers or ‘...’ before ‘size_t’
/usr/include/string.h:68: error: expected declaration specifiers or ‘...’ before ‘size_t’
/usr/include/string.h:95: error: expected declaration specifiers or ‘...’ before ‘size_t’
/usr/include/string.h:132: error: expected declaration specifiers or ‘...’ before ‘size_t’
/usr/include/string.h:140: error: expected declaration specifiers or ‘...’ before ‘size_t’
/usr/include/string.h:146: error: expected declaration specifiers or ‘...’ before ‘size_t’
/usr/include/string.h:153: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘strxfrm’
In file included from scripts/basic/fixdep.c:111:
/usr/include/string.h:168: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘strxfrm_l’
/usr/include/string.h:183: error: expected declaration specifiers or ‘...’ before ‘size_t’
/usr/include/string.h:284: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘strcspn’
/usr/include/string.h:288: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘strspn’
/usr/include/string.h:399: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘strlen’
/usr/include/string.h:406: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘strnlen’
/usr/include/string.h:427: error: expected declaration specifiers or ‘...’ before ‘size_t’
/usr/include/string.h:451: error: expected declaration specifiers or ‘...’ before ‘size_t’
/usr/include/string.h:455: error: expected declaration specifiers or ‘...’ before ‘size_t’
/usr/include/string.h:459: error: expected declaration specifiers or ‘...’ before ‘size_t’
/usr/include/string.h:462: error: expected declaration specifiers or ‘...’ before ‘size_t’
/usr/include/string.h:540: error: expected declaration specifiers or ‘...’ before ‘size_t’
/usr/include/string.h:577: error: expected declaration specifiers or ‘...’ before ‘size_t’
/usr/include/string.h:580: error: expected declaration specifiers or ‘...’ before ‘size_t’
In file included from /usr/include/string.h:637,
                 from scripts/basic/fixdep.c:111:
/usr/include/bits/string2.h:969: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘__strcspn_c1’
/usr/include/bits/string2.h:971: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘__strcspn_c1’
/usr/include/bits/string2.h:979: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘__strcspn_c2’
/usr/include/bits/string2.h:982: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘__strcspn_c2’
/usr/include/bits/string2.h:991: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘__strcspn_c3’
/usr/include/bits/string2.h:994: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘__strcspn_c3’
/usr/include/bits/string2.h:1045: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘__strspn_c1’
/usr/include/bits/string2.h:1047: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘__strspn_c1’
/usr/include/bits/string2.h:1056: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘__strspn_c2’
/usr/include/bits/string2.h:1059: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘__strspn_c2’
/usr/include/bits/string2.h:1068: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘__strspn_c3’
/usr/include/bits/string2.h:1071: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘__strspn_c3’
/usr/include/bits/string2.h: In function ‘__strpbrk_c2’:
/usr/include/bits/string2.h:1129: error: expected ‘;’ before ‘__s’
/usr/include/bits/string2.h: In function ‘__strpbrk_c3’:
/usr/include/bits/string2.h:1142: error: expected ‘;’ before ‘__s’
In file included from /usr/include/bits/string2.h:1298,
                 from /usr/include/string.h:637,
                 from scripts/basic/fixdep.c:111:
/usr/include/stdlib.h: At top level:
/usr/include/stdlib.h:471: error: expected ‘)’ before ‘__size’
/usr/include/stdlib.h:473: error: expected ‘)’ before ‘__nmemb’
In file included from /usr/include/string.h:637,
                 from scripts/basic/fixdep.c:111:
/usr/include/bits/string2.h:1322: error: expected declaration specifiers or ‘...’ before ‘size_t’
In file included from /usr/include/string.h:642,
                 from scripts/basic/fixdep.c:111:
/usr/include/bits/string3.h:49: error: expected declaration specifiers or ‘...’ before ‘size_t’
/usr/include/bits/string3.h: In function ‘memcpy’:
/usr/include/bits/string3.h:52: error: ‘__len’ undeclared (first use in this function)
/usr/include/bits/string3.h: At top level:
/usr/include/bits/string3.h:56: error: expected declaration specifiers or ‘...’ before ‘size_t’
/usr/include/bits/string3.h: In function ‘memmove’:
/usr/include/bits/string3.h:59: error: ‘__len’ undeclared (first use in this function)
/usr/include/bits/string3.h: At top level:
/usr/include/bits/string3.h:78: error: expected declaration specifiers or ‘...’ before ‘size_t’
/usr/include/bits/string3.h: In function ‘memset’:
/usr/include/bits/string3.h:80: error: ‘__len’ undeclared (first use in this function)
/usr/include/bits/string3.h: At top level:
/usr/include/bits/string3.h:91: error: expected declaration specifiers or ‘...’ before ‘size_t’
/usr/include/bits/string3.h: In function ‘bcopy’:
/usr/include/bits/string3.h:94: error: ‘__len’ undeclared (first use in this function)
/usr/include/bits/string3.h: At top level:
/usr/include/bits/string3.h:98: error: expected declaration specifiers or ‘...’ before ‘size_t’
/usr/include/bits/string3.h: In function ‘bzero’:
/usr/include/bits/string3.h:100: error: ‘__len’ undeclared (first use in this function)
/usr/include/bits/string3.h: At top level:
/usr/include/bits/string3.h:120: error: expected declaration specifiers or ‘...’ before ‘size_t’
/usr/include/bits/string3.h: In function ‘strncpy’:
/usr/include/bits/string3.h:123: error: ‘__len’ undeclared (first use in this function)
/usr/include/bits/string3.h: At top level:
/usr/include/bits/string3.h:127: error: expected declaration specifiers or ‘...’ before ‘size_t’
/usr/include/bits/string3.h:128: error: expected declaration specifiers or ‘...’ before ‘size_t’
/usr/include/bits/string3.h:129: error: expected declaration specifiers or ‘...’ before ‘size_t’
/usr/include/bits/string3.h:134: error: expected declaration specifiers or ‘...’ before ‘size_t’
/usr/include/bits/string3.h: In function ‘stpncpy’:
/usr/include/bits/string3.h:137: error: ‘__n’ undeclared (first use in this function)
/usr/include/bits/string3.h:138: error: too many arguments to function ‘__stpncpy_chk’
/usr/include/bits/string3.h:139: error: too many arguments to function ‘__stpncpy_alias’
/usr/include/bits/string3.h: At top level:
/usr/include/bits/string3.h:151: error: expected declaration specifiers or ‘...’ before ‘size_t’
/usr/include/bits/string3.h: In function ‘strncat’:
/usr/include/bits/string3.h:154: error: ‘__len’ undeclared (first use in this function)
In file included from scripts/basic/fixdep.c:112:
/usr/include/stdlib.h: At top level:
/usr/include/stdlib.h:140: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘__ctype_get_mb_cur_max’
/usr/include/stdlib.h:337: error: expected declaration specifiers or ‘...’ before ‘size_t’
/usr/include/stdlib.h:367: error: expected declaration specifiers or ‘...’ before ‘size_t’
/usr/include/stdlib.h:369: error: nonnull argument with out-of-range operand number (argument 1, operand 4)
/usr/include/stdlib.h:485: error: expected declaration specifiers or ‘...’ before ‘size_t’
In file included from /usr/include/stdlib.h:497,
                 from scripts/basic/fixdep.c:112:
/usr/include/alloca.h:33: error: expected ‘)’ before ‘__size’
In file included from scripts/basic/fixdep.c:112:
/usr/include/stdlib.h:503: error: expected ‘)’ before ‘__size’
/usr/include/stdlib.h:508: error: expected declaration specifiers or ‘...’ before ‘size_t’
/usr/include/stdlib.h:508: error: expected declaration specifiers or ‘...’ before ‘size_t’
/usr/include/stdlib.h:756: error: expected declaration specifiers or ‘...’ before ‘size_t’
/usr/include/stdlib.h:756: error: expected declaration specifiers or ‘...’ before ‘size_t’
/usr/include/stdlib.h:757: error: nonnull argument with out-of-range operand number (argument 1, operand 5)
/usr/include/stdlib.h:761: error: expected declaration specifiers or ‘...’ before ‘size_t’
/usr/include/stdlib.h:761: error: expected declaration specifiers or ‘...’ before ‘size_t’
/usr/include/stdlib.h:762: error: nonnull argument with out-of-range operand number (argument 1, operand 4)
/usr/include/stdlib.h:840: error: expected declaration specifiers or ‘...’ before ‘size_t’
/usr/include/stdlib.h:843: error: expected declaration specifiers or ‘...’ before ‘size_t’
/usr/include/stdlib.h:847: error: expected declaration specifiers or ‘...’ before ‘size_t’
/usr/include/stdlib.h:851: error: expected declaration specifiers or ‘...’ before ‘size_t’
/usr/include/stdlib.h:860: error: expected declaration specifiers or ‘...’ before ‘size_t’
/usr/include/stdlib.h:863: error: expected ‘)’ before ‘*’ token
/usr/include/stdlib.h:867: error: expected declaration specifiers or ‘...’ before ‘wchar_t’
/usr/include/stdlib.h:871: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘mbstowcs’
/usr/include/stdlib.h:874: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘wcstombs’
In file included from /usr/include/stdlib.h:955,
                 from scripts/basic/fixdep.c:112:
/usr/include/bits/stdlib.h:26: error: expected declaration specifiers or ‘...’ before ‘size_t’
/usr/include/bits/stdlib.h:30: error: expected declaration specifiers or ‘...’ before ‘size_t’
/usr/include/bits/stdlib.h: In function ‘realpath’:
/usr/include/bits/stdlib.h:46: error: too many arguments to function ‘__realpath_chk’
/usr/include/bits/stdlib.h: At top level:
/usr/include/bits/stdlib.h:53: error: expected declaration specifiers or ‘...’ before ‘size_t’
/usr/include/bits/stdlib.h:54: error: expected declaration specifiers or ‘...’ before ‘size_t’
/usr/include/bits/stdlib.h:55: error: expected declaration specifiers or ‘...’ before ‘size_t’
/usr/include/bits/stdlib.h:58: error: expected declaration specifiers or ‘...’ before ‘size_t’
/usr/include/bits/stdlib.h:58: error: expected declaration specifiers or ‘...’ before ‘size_t’
/usr/include/bits/stdlib.h:65: error: expected declaration specifiers or ‘...’ before ‘size_t’
/usr/include/bits/stdlib.h: In function ‘ptsname_r’:
/usr/include/bits/stdlib.h:69: error: ‘__buflen’ undeclared (first use in this function)
/usr/include/bits/stdlib.h:70: error: too many arguments to function ‘__ptsname_r_chk’
/usr/include/bits/stdlib.h:72: error: too many arguments to function ‘__ptsname_r_chk_warn’
/usr/include/bits/stdlib.h:74: error: too many arguments to function ‘__ptsname_r_alias’
/usr/include/bits/stdlib.h: At top level:
/usr/include/bits/stdlib.h:78: error: expected declaration specifiers or ‘...’ before ‘wchar_t’
/usr/include/bits/stdlib.h:78: error: expected declaration specifiers or ‘...’ before ‘size_t’
/usr/include/bits/stdlib.h:80: error: expected declaration specifiers or ‘...’ before ‘wchar_t’
/usr/include/bits/stdlib.h:84: error: expected declaration specifiers or ‘...’ before ‘wchar_t’
/usr/include/bits/stdlib.h: In function ‘wctomb’:
/usr/include/bits/stdlib.h:94: error: ‘__wchar’ undeclared (first use in this function)
/usr/include/bits/stdlib.h:94: error: too many arguments to function ‘__wctomb_chk’
/usr/include/bits/stdlib.h:95: error: too many arguments to function ‘__wctomb_alias’
/usr/include/bits/stdlib.h: At top level:
/usr/include/bits/stdlib.h:99: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘__mbstowcs_chk’
/usr/include/bits/stdlib.h:102: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘__mbstowcs_alias’
/usr/include/bits/stdlib.h:106: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘__mbstowcs_chk_warn’
/usr/include/bits/stdlib.h:114: error: expected ‘,’ or ‘;’ before ‘mbstowcs’
/usr/include/bits/stdlib.h:131: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘__wcstombs_chk’
/usr/include/bits/stdlib.h:134: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘__wcstombs_alias’
/usr/include/bits/stdlib.h:138: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘__wcstombs_chk_warn’
/usr/include/bits/stdlib.h:145: error: expected ‘,’ or ‘;’ before ‘wcstombs’
In file included from /usr/include/tr1/cstdarg:32,
                 from /usr/include/stdarg.h:32,
                 from /usr/include/libio.h:53,
                 from /usr/include/stdio.h:75,
                 from scripts/basic/fixdep.c:113:
/usr/include/cstdarg:56: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘:’ token
In file included from /usr/include/stdio.h:75,
                 from scripts/basic/fixdep.c:113:
/usr/include/libio.h:332: error: expected specifier-qualifier-list before ‘size_t’
/usr/include/libio.h:364: error: expected declaration specifiers or ‘...’ before ‘size_t’
/usr/include/libio.h:373: error: expected declaration specifiers or ‘...’ before ‘size_t’
/usr/include/libio.h:491: error: expected declaration specifiers or ‘...’ before ‘__gnuc_va_list’
/usr/include/libio.h:493: error: expected declaration specifiers or ‘...’ before ‘__gnuc_va_list’
/usr/include/libio.h:495: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘_IO_sgetn’
In file included from scripts/basic/fixdep.c:113:
/usr/include/stdio.h:80: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘va_list’
In file included from scripts/basic/fixdep.c:113:
/usr/include/stdio.h:316: error: expected declaration specifiers or ‘...’ before ‘size_t’
/usr/include/stdio.h:322: error: expected declaration specifiers or ‘...’ before ‘size_t’
/usr/include/stdio.h:334: error: expected declaration specifiers or ‘...’ before ‘size_t’
/usr/include/stdio.h:341: error: expected declaration specifiers or ‘...’ before ‘size_t’
/usr/include/stdio.h:369: error: expected declaration specifiers or ‘...’ before ‘__gnuc_va_list’
/usr/include/stdio.h:374: error: expected declaration specifiers or ‘...’ before ‘__gnuc_va_list’
/usr/include/stdio.h:377: error: expected declaration specifiers or ‘...’ before ‘__gnuc_va_list’
/usr/include/stdio.h:383: error: expected declaration specifiers or ‘...’ before ‘size_t’
/usr/include/stdio.h:385: error: format string argument not a string type
/usr/include/stdio.h:387: error: expected declaration specifiers or ‘...’ before ‘size_t’
/usr/include/stdio.h:388: error: expected declaration specifiers or ‘...’ before ‘__gnuc_va_list’
/usr/include/stdio.h:389: error: format string argument not a string type
/usr/include/stdio.h:415: error: expected declaration specifiers or ‘...’ before ‘__gnuc_va_list’
/usr/include/stdio.h:474: error: expected declaration specifiers or ‘...’ before ‘__gnuc_va_list’
/usr/include/stdio.h:481: error: expected declaration specifiers or ‘...’ before ‘__gnuc_va_list’
/usr/include/stdio.h:486: error: expected declaration specifiers or ‘...’ before ‘__gnuc_va_list’
/usr/include/stdio.h:496: error: expected declaration specifiers or ‘...’ before ‘__gnuc_va_list’
/usr/include/stdio.h:501: error: expected declaration specifiers or ‘...’ before ‘__gnuc_va_list’
/usr/include/stdio.h:504: error: expected declaration specifiers or ‘...’ before ‘__gnuc_va_list’
/usr/include/stdio.h:659: error: expected declaration specifiers or ‘...’ before ‘size_t’
/usr/include/stdio.h:662: error: expected declaration specifiers or ‘...’ before ‘size_t’
/usr/include/stdio.h:672: error: expected declaration specifiers or ‘...’ before ‘size_t’
/usr/include/stdio.h:702: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘fread’
/usr/include/stdio.h:708: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘fwrite’
/usr/include/stdio.h:730: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘fread_unlocked’
/usr/include/stdio.h:732: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘fwrite_unlocked’
In file included from /usr/include/stdio.h:930,
                 from scripts/basic/fixdep.c:113:
/usr/include/bits/stdio2.h:24: error: expected declaration specifiers or ‘...’ before ‘size_t’
/usr/include/bits/stdio2.h:26: error: expected declaration specifiers or ‘...’ before ‘size_t’
/usr/include/bits/stdio2.h:28: error: expected declaration specifiers or ‘...’ before ‘__gnuc_va_list’
/usr/include/bits/stdio2.h:44: error: expected declaration specifiers or ‘...’ before ‘__gnuc_va_list’
/usr/include/bits/stdio2.h: In function ‘vsprintf’:
/usr/include/bits/stdio2.h:48: error: ‘__ap’ undeclared (first use in this function)
/usr/include/bits/stdio2.h: At top level:
/usr/include/bits/stdio2.h:53: error: expected declaration specifiers or ‘...’ before ‘size_t’
/usr/include/bits/stdio2.h:54: error: expected declaration specifiers or ‘...’ before ‘size_t’
/usr/include/bits/stdio2.h:56: error: expected declaration specifiers or ‘...’ before ‘size_t’
/usr/include/bits/stdio2.h:57: error: expected declaration specifiers or ‘...’ before ‘size_t’
/usr/include/bits/stdio2.h:58: error: expected declaration specifiers or ‘...’ before ‘__gnuc_va_list’
/usr/include/bits/stdio2.h:62: error: expected declaration specifiers or ‘...’ before ‘size_t’
/usr/include/bits/stdio2.h: In function ‘snprintf’:
/usr/include/bits/stdio2.h:65: error: ‘__n’ undeclared (first use in this function)
/usr/include/bits/stdio2.h: At top level:
/usr/include/bits/stdio2.h:75: error: expected declaration specifiers or ‘...’ before ‘size_t’
/usr/include/bits/stdio2.h:75: error: expected declaration specifiers or ‘...’ before ‘__gnuc_va_list’
/usr/include/bits/stdio2.h: In function ‘vsnprintf’:
/usr/include/bits/stdio2.h:78: error: ‘__n’ undeclared (first use in this function)
/usr/include/bits/stdio2.h:79: error: ‘__ap’ undeclared (first use in this function)
/usr/include/bits/stdio2.h: At top level:
/usr/include/bits/stdio2.h:90: error: expected declaration specifiers or ‘...’ before ‘__gnuc_va_list’
/usr/include/bits/stdio2.h:92: error: expected declaration specifiers or ‘...’ before ‘__gnuc_va_list’
/usr/include/bits/stdio2.h:115: error: expected declaration specifiers or ‘...’ before ‘__gnuc_va_list’
/usr/include/bits/stdio2.h: In function ‘vprintf’:
/usr/include/bits/stdio2.h:118: error: ‘__ap’ undeclared (first use in this function)
/usr/include/bits/stdio2.h:118: error: too many arguments to function ‘__vfprintf_chk’
/usr/include/bits/stdio2.h: At top level:
/usr/include/bits/stdio2.h:126: error: expected declaration specifiers or ‘...’ before ‘__gnuc_va_list’
/usr/include/bits/stdio2.h: In function ‘vfprintf’:
/usr/include/bits/stdio2.h:128: error: ‘__ap’ undeclared (first use in this function)
/usr/include/bits/stdio2.h:128: error: too many arguments to function ‘__vfprintf_chk’
/usr/include/bits/stdio2.h: At top level:
/usr/include/bits/stdio2.h:220: error: expected declaration specifiers or ‘...’ before ‘size_t’
/usr/include/bits/stdio2.h: In function ‘gets’:
/usr/include/bits/stdio2.h:229: error: too many arguments to function ‘__gets_chk’
/usr/include/bits/stdio2.h: At top level:
/usr/include/bits/stdio2.h:233: error: expected declaration specifiers or ‘...’ before ‘size_t’
/usr/include/bits/stdio2.h:238: error: expected declaration specifiers or ‘...’ before ‘size_t’
/usr/include/bits/stdio2.h: In function ‘fgets’:
/usr/include/bits/stdio2.h:250: error: too many arguments to function ‘__fgets_chk’
/usr/include/bits/stdio2.h:252: error: expected ‘)’ before ‘__n’
/usr/include/bits/stdio2.h:253: error: too many arguments to function ‘__fgets_chk_warn’
/usr/include/bits/stdio2.h: At top level:
/usr/include/bits/stdio2.h:258: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘__fread_chk’
/usr/include/bits/stdio2.h:261: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘__fread_alias’
/usr/include/bits/stdio2.h:265: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘__fread_chk_warn’
/usr/include/bits/stdio2.h:274: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘fread’
/usr/include/bits/stdio2.h:319: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘__fread_unlocked_chk’
/usr/include/bits/stdio2.h:322: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘__fread_unlocked_alias’
/usr/include/bits/stdio2.h:326: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘__fread_unlocked_chk_warn’
/usr/include/bits/stdio2.h:335: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘fread_unlocked’
In file included from scripts/basic/fixdep.c:114:
/usr/include/limits.h:125: error: no include path in which to search for limits.h
In file included from /usr/include/sys/uio.h:29,
                 from /usr/include/sys/socket.h:28,
                 from /usr/include/netinet/in.h:25,
                 from /usr/include/arpa/inet.h:23,
                 from scripts/basic/fixdep.c:116:
/usr/include/bits/uio.h:47: error: expected specifier-qualifier-list before ‘size_t’
In file included from /usr/include/sys/socket.h:40,
                 from /usr/include/netinet/in.h:25,
                 from /usr/include/arpa/inet.h:23,
                 from scripts/basic/fixdep.c:116:
/usr/include/bits/socket.h:253: error: expected specifier-qualifier-list before ‘size_t’
/usr/include/bits/socket.h:276: error: expected specifier-qualifier-list before ‘size_t’
/usr/include/bits/socket.h: In function ‘__cmsg_nxthdr’:
/usr/include/bits/socket.h:313: error: expected ‘)’ before ‘__cmsg’
/usr/include/bits/socket.h:318: error: ‘struct cmsghdr’ has no member named ‘cmsg_len’
/usr/include/bits/socket.h:318: error: expected ‘)’ before ‘~’ token
/usr/include/bits/socket.h:319: error: ‘struct msghdr’ has no member named ‘msg_control’
/usr/include/bits/socket.h:320: error: ‘struct msghdr’ has no member named ‘msg_controllen’
/usr/include/bits/socket.h:321: error: ‘struct cmsghdr’ has no member named ‘cmsg_len’
/usr/include/bits/socket.h:321: error: expected ‘)’ before ‘~’ token
/usr/include/bits/socket.h:322: error: ‘struct msghdr’ has no member named ‘msg_control’
/usr/include/bits/socket.h:322: error: ‘struct msghdr’ has no member named ‘msg_controllen’
In file included from /usr/include/netinet/in.h:25,
                 from /usr/include/arpa/inet.h:23,
                 from scripts/basic/fixdep.c:116:
/usr/include/sys/socket.h: At top level:
/usr/include/sys/socket.h:141: error: expected declaration specifiers or ‘...’ before ‘size_t’
/usr/include/sys/socket.h:148: error: expected declaration specifiers or ‘...’ before ‘size_t’
/usr/include/sys/socket.h:155: error: expected declaration specifiers or ‘...’ before ‘size_t’
/usr/include/sys/socket.h:166: error: expected declaration specifiers or ‘...’ before ‘size_t’
In file included from /usr/include/sys/socket.h:251,
                 from /usr/include/netinet/in.h:25,
                 from /usr/include/arpa/inet.h:23,
                 from scripts/basic/fixdep.c:116:
/usr/include/bits/socket2.h:24: error: expected declaration specifiers or ‘...’ before ‘size_t’
/usr/include/bits/socket2.h:24: error: expected declaration specifiers or ‘...’ before ‘size_t’
/usr/include/bits/socket2.h:26: error: expected declaration specifiers or ‘...’ before ‘size_t’
/usr/include/bits/socket2.h:28: error: expected declaration specifiers or ‘...’ before ‘size_t’
/usr/include/bits/socket2.h:28: error: expected declaration specifiers or ‘...’ before ‘size_t’
/usr/include/bits/socket2.h:35: error: expected declaration specifiers or ‘...’ before ‘size_t’
/usr/include/bits/socket2.h: In function ‘recv’:
/usr/include/bits/socket2.h:39: error: ‘__n’ undeclared (first use in this function)
/usr/include/bits/socket2.h:40: error: too many arguments to function ‘__recv_chk’
/usr/include/bits/socket2.h:43: error: too many arguments to function ‘__recv_chk_warn’
/usr/include/bits/socket2.h:45: error: too many arguments to function ‘__recv_alias’
/usr/include/bits/socket2.h: At top level:
/usr/include/bits/socket2.h:48: error: expected declaration specifiers or ‘...’ before ‘size_t’
/usr/include/bits/socket2.h:49: error: expected declaration specifiers or ‘...’ before ‘size_t’
/usr/include/bits/socket2.h:52: error: expected declaration specifiers or ‘...’ before ‘size_t’
/usr/include/bits/socket2.h:56: error: expected declaration specifiers or ‘...’ before ‘size_t’
/usr/include/bits/socket2.h:56: error: expected declaration specifiers or ‘...’ before ‘size_t’
/usr/include/bits/socket2.h:65: error: expected declaration specifiers or ‘...’ before ‘size_t’
/usr/include/bits/socket2.h: In function ‘recvfrom’:
/usr/include/bits/socket2.h:70: error: ‘__n’ undeclared (first use in this function)
/usr/include/bits/socket2.h:72: error: too many arguments to function ‘__recvfrom_chk’
/usr/include/bits/socket2.h:75: error: too many arguments to function ‘__recvfrom_chk_warn’
/usr/include/bits/socket2.h:77: error: too many arguments to function ‘__recvfrom_alias’
In file included from scripts/basic/fixdep.c:116:
/usr/include/arpa/inet.h: At top level:
/usr/include/arpa/inet.h:78: error: expected declaration specifiers or ‘...’ before ‘size_t’
/usr/include/arpa/inet.h:84: error: expected declaration specifiers or ‘...’ before ‘size_t’
/usr/include/arpa/inet.h:90: error: expected declaration specifiers or ‘...’ before ‘size_t’
scripts/basic/fixdep.c: In function ‘grow_config’:
scripts/basic/fixdep.c:154: error: too many arguments to function ‘realloc’
scripts/basic/fixdep.c: In function ‘is_defined_config’:
scripts/basic/fixdep.c:172: error: too many arguments to function ‘memcmp’
scripts/basic/fixdep.c: In function ‘define_config’:
scripts/basic/fixdep.c:185: error: too many arguments to function ‘memcpy’
scripts/basic/fixdep.c: In function ‘use_config’:
scripts/basic/fixdep.c:212: error: too many arguments to function ‘memcpy’
scripts/basic/fixdep.c: At top level:
scripts/basic/fixdep.c:223: error: expected declaration specifiers or ‘...’ before ‘size_t’
scripts/basic/fixdep.c: In function ‘parse_config_file’:
scripts/basic/fixdep.c:225: error: ‘len’ undeclared (first use in this function)
scripts/basic/fixdep.c:239: error: too many arguments to function ‘memcmp’
scripts/basic/fixdep.c:248: error: too many arguments to function ‘memcmp’
scripts/basic/fixdep.c: In function ‘strrcmp’:
scripts/basic/fixdep.c:259: warning: implicit declaration of function ‘strlen’
scripts/basic/fixdep.c:259: warning: incompatible implicit declaration of built-in function ‘strlen’
scripts/basic/fixdep.c:265: error: too many arguments to function ‘memcmp’
scripts/basic/fixdep.c: In function ‘do_config_file’:
scripts/basic/fixdep.c:285: error: too many arguments to function ‘mmap’
scripts/basic/fixdep.c:292: error: too many arguments to function ‘parse_config_file’
scripts/basic/fixdep.c:294: error: too many arguments to function ‘munmap’
scripts/basic/fixdep.c: At top level:
scripts/basic/fixdep.c:299: error: expected declaration specifiers or ‘...’ before ‘size_t’
scripts/basic/fixdep.c: In function ‘parse_dep_file’:
scripts/basic/fixdep.c:302: error: ‘len’ undeclared (first use in this function)
scripts/basic/fixdep.c:311: error: too many arguments to function ‘memcpy’
scripts/basic/fixdep.c:326: error: too many arguments to function ‘memcpy’
scripts/basic/fixdep.c: In function ‘print_deps’:
scripts/basic/fixdep.c:357: error: too many arguments to function ‘mmap’
scripts/basic/fixdep.c:364: error: too many arguments to function ‘parse_dep_file’
scripts/basic/fixdep.c:366: error: too many arguments to function ‘munmap’
make[1]: *** [scripts/basic/fixdep] Error 1
make: *** [scripts_basic] Error 2


1. What cause my partition when the journal active, it always keep give Filesystem state: not clean? how to fix this?
2. The most important to me, how can I get my system to be able to run make on kernel headers?

sorry for the long log post

---

### Post by azmyth on 2011-09-29
I'd reinstall headers.

/tmp/vbox.0/include/iprt/types.h:96: fatal error: stddef.h: No such file or directory

This means your missing a header file that should be included with the headers so I'd reinstall them

---

