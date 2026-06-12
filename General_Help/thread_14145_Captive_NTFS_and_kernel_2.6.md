---
title: "Captive NTFS and kernel 2.6?"
date: 2005-02-05
forum: General Help
---

### Post by EnderWiggin on 2005-02-05
Hi all

I'm a relative newbie here. This question seems not to have been covered here though...

After installing and Captive NTFS, configuring it with ntfs.sys and ntoskrnl.exe, it still wouldn't mount a drive, giving this error message:

mount -t captive-ntfs /dev/hda1 /mnt/captive-hegemon/
Captive NTFS v1.1.5.  Check a new version at: [http://www.jankratochvil.net/](http://www.jankratochvil.net/)
Preparing LUFS kernel module... Run /usr/share/lufs/prepmod if problems occur.
lufs module not loaded: Try running /usr/share/lufs/prepmod to see more. at /usr/bin/captive-lufsd line 180

Running /usr/share/lufs/prepmod, I get the following error message:

/usr/share/lufs/prepmod
+ /sbin/modprobe lufs 2>/dev/null
Preparing LUFS kernel module... Run /usr/share/lufs/prepmod if problems occur.
Running kernel version: 2.6.8.1-4-386 (base version 2.6.8.1)
Destination module directory: /lib/modules/2.6.8.1-4-386/kernel/fs/lufs
Failed to find kernel headers for 2.6.8.1-4-386
Failed to prepare lufs.ko module for your Linux kernel 2.6.8.1-4-386.
No Linux kernel sources for your running kernel were found.
Please install kernel-source-x.y.z.i386.rpm or kernel-headers_x.y.z_i386.deb.
The following directory paths were search (first existing directory used):
                /lib/modules/2.6.8.1-4-386/build
                /usr/src/kernel-headers-2.6.8.1-4-386
                /usr/src/linux-2.6.8.1-4-386
                /usr/src/linux-2.6.8.1
                /usr/src/linux
                /usr/src/kernel-source-2.6.8.1-4-386

Now, my question is: why on Earth are there no kernel-header packages available for my kernel version? the Synaptic Package Manager reports that there is only one version of this package available: 2.5.999-test7-bk-16 (warty).

Can anyone shed some light?

---

### Post by llamakc on 2005-02-05
Have you installed lufs-source and lufs-utils yet? Is that the default kernel from the install? Try getting a kernel-image for your arch or building one from source. I love using the Linux Userland Filesystem but haven't tried it either since coming to Ubuntu from Gentoo & Debian.

---

### Post by EnderWiggin on 2005-02-05
after pottering around with this [in work time ;-)], i got it to the following error message:

root@framling:/home/arno/temp/lufs-0.9.7 # ./configure
checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
checking target system type... i686-pc-linux-gnu
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking OS... Linux
checking kernel... 2.6.8.1-4-386
checking kernel support... supported in kernel/Linux/2.6
checking kernel headers... found in /lib/modules/2.6.8.1-4-386/build/include
checking kernel configuration... found, using modversions
checking modversions.h... /lib/modules/2.6.8.1-4-386/build/include/config/modversions.h
checking for gcc... gcc
checking for C compiler default output... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables...
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ANSI C... none needed
checking for style of include used by make... GNU
checking dependency style of gcc... gcc3
checking how to run the C preprocessor... gcc -E
checking for g++... no
checking for c++... no
checking for gpp... no
checking for aCC... no
checking for CC... no
checking for cxx... no
checking for cc++... no
checking for cl... no
checking for FCC... no
checking for KCC... no
checking for RCC... no
checking for xlC_r... no
checking for xlC... no
checking whether we are using the GNU C++ compiler... no
checking whether g++ accepts -g... no
checking dependency style of g++... none
checking for a BSD-compatible install... /usr/bin/install -c
checking whether ln -s works... yes
checking for a sed that does not truncate output... /bin/sed
checking for egrep... grep -E
checking for ld used by gcc... /usr/bin/ld
checking if the linker (/usr/bin/ld) is GNU ld... yes
checking for /usr/bin/ld option to reload object files... -r
checking for BSD-compatible nm... /usr/bin/nm -B
checking how to recognise dependent libraries... pass_all
checking for ANSI C header files... yes
checking for sys/types.h... yes
checking for sys/stat.h... yes
checking for stdlib.h... yes
checking for string.h... yes
checking for memory.h... yes
checking for strings.h... yes
checking for inttypes.h... yes
checking for stdint.h... yes
checking for unistd.h... yes
checking dlfcn.h usability... yes
checking dlfcn.h presence... yes
checking for dlfcn.h... yes
checking how to run the C++ preprocessor... /lib/cpp
configure: error: C++ preprocessor "/lib/cpp" fails sanity check
See `config.log' for more details.

I got the kernel-headers to install from the console with apt-get, so that's sorted... it was the default before, this is a virgin Ubuntu install, done just this morning.

How do I fix the /lib/cpp problem?

---

### Post by llamakc on 2005-02-05
I'd install the build-essential package and cpp, doesn't look to be installed yet. I just forgot some build tools too while compiling MPlayer from source.

---

### Post by EnderWiggin on 2005-02-05
Did that, looks like lufs compiled successfully, now when i try to mount the ntfs partition with 

root@framling:/home/arno/temp/lufs-0.9.7 # mount -t captive-ntfs /dev/hda1 /mnt/captive-hegemon/

I get:

Captive NTFS v1.1.5.  Check a new version at: [http://www.jankratochvil.net/](http://www.jankratochvil.net/)
/usr/bin/captive-lufsd-bin: /usr/bin/captive-lufsd-bin: cannot execute binary file

What am I doing wrong?

---

