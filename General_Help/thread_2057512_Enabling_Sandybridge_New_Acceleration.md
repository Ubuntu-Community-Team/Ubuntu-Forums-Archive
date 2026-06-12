---
title: "Enabling Sandybridge New Acceleration"
date: 2012-09-13
forum: General Help
---

### Post by Stonecold1995 on 2012-09-13
I read [here]("https://help.ubuntu.com/community/How%20to%20make%20Kubuntu%20(KDE)%20blazing%20fast%20and%20optimise%20it%20for%20performance%20%7C%20kio_http") that enabling "Sandybridge New Acceleration" can speed up KDE, but the [link]("https://launchpad.net/~sarvatt/+archive/intel-sna") it provided is marked as private and I can't go to it.  I read [here]("http://www.phoronix.com/scan.php?page=news_item&px=MTEzOTE") that the current Intel video driver supports SNA, but it is off by default.  And [this]("https://bbs.archlinux.org/viewtopic.php?id=144500") page that I have to compile the xf86-intel-video package with --enable-sna, but when I tried that I got this:
```
**alex@kubuntu:~$** sudo apt-get source xserver-xorg-video-intel
Reading package lists... Done
Building dependency tree       
Reading state information... Done
NOTICE: 'xserver-xorg-video-intel' packaging is maintained in the 'Git' version control system at:
git://git.debian.org/git/pkg-xorg/driver/xserver-xorg-video-intel
Need to get 2,122 kB of source archives.
Get:1 http://ppa.launchpad.net/ubuntu-x-swat/x-updates/ubuntu/ precise/main xserver-xorg-video-intel 2:2.19.0-0ubuntu1~xup1 (tar) [1,972 kB]
Get:2 http://ppa.launchpad.net/ubuntu-x-swat/x-updates/ubuntu/ precise/main xserver-xorg-video-intel 2:2.19.0-0ubuntu1~xup1 (diff) [148 kB]                                                                                                                                   
Get:3 http://ppa.launchpad.net/ubuntu-x-swat/x-updates/ubuntu/ precise/main xserver-xorg-video-intel 2:2.19.0-0ubuntu1~xup1 (dsc) [2,182 B]                                                                                                                                   
Fetched 2,122 kB in 16s (129 kB/s)                                                                                                                                                                                                                                            
gpgv: Signature made Wed 02 May 2012 08:32:00 AM PDT using DSA key ID CB98E2AF
gpgv: Can't check signature: public key not found
dpkg-source: warning: failed to verify signature on ./xserver-xorg-video-intel_2.19.0-0ubuntu1~xup1.dsc
dpkg-source: info: extracting xserver-xorg-video-intel in xserver-xorg-video-intel-2.19.0
dpkg-source: info: unpacking xserver-xorg-video-intel_2.19.0.orig.tar.gz
dpkg-source: info: applying xserver-xorg-video-intel_2.19.0-0ubuntu1~xup1.diff.gz
dpkg-source: info: upstream files that have been modified: 
 xserver-xorg-video-intel-2.19.0/ChangeLog
 xserver-xorg-video-intel-2.19.0/RELEASING
 xserver-xorg-video-intel-2.19.0/autogen.sh
 xserver-xorg-video-intel-2.19.0/src/scripts/clock-graph.5c
 xserver-xorg-video-intel-2.19.0/src/scripts/clock.5c
 xserver-xorg-video-intel-2.19.0/src/scripts/fix.5c
 xserver-xorg-video-intel-2.19.0/src/scripts/tv.5c

**alex@kubuntu:~$** cd xserver-xorg-video-intel-2.19.0/

**alex@kubuntu:~/xserver-xorg-video-intel-2.19.0$** sudo ./configure --enable-sna
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for a thread-safe mkdir -p... /bin/mkdir -p
checking for gawk... gawk
checking whether make sets $(MAKE)... yes
checking whether to enable maintainer-specific portions of Makefiles... no
checking for style of include used by make... GNU
checking for gcc... gcc
checking whether the C compiler works... yes
checking for C compiler default output file name... a.out
checking for suffix of executables... 
checking whether we are cross compiling... no
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ISO C89... none needed
checking dependency style of gcc... gcc3
checking for gcc option to accept ISO C99... -std=gnu99
checking how to run the C preprocessor... gcc -std=gnu99 -E
checking for grep that handles long lines and -e... /bin/grep
checking for egrep... /bin/grep -E
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
checking whether __clang__ is declared... no
checking whether __INTEL_COMPILER is declared... no
checking whether __SUNPRO_C is declared... no
checking for pkg-config... /usr/bin/pkg-config
checking pkg-config is at least version 0.9.0... yes
checking build system type... x86_64-unknown-linux-gnu
checking host system type... x86_64-unknown-linux-gnu
checking for a sed that does not truncate output... /bin/sed
checking if gcc -std=gnu99 supports -Werror=unknown-warning-option... no
checking if gcc -std=gnu99 supports -Werror=unused-command-line-argument... no
checking if gcc -std=gnu99 supports-Wall... yes
checking if gcc -std=gnu99 supports-Wpointer-arith... yes
checking if gcc -std=gnu99 supports-Wmissing-declarations... yes
checking if gcc -std=gnu99 supports-Wformat=2... yes
checking if gcc -std=gnu99 supports-Wstrict-prototypes... yes
checking if gcc -std=gnu99 supports-Wmissing-prototypes... yes
checking if gcc -std=gnu99 supports-Wnested-externs... yes
checking if gcc -std=gnu99 supports-Wbad-function-cast... yes
checking if gcc -std=gnu99 supports-Wold-style-definition... yes
checking if gcc -std=gnu99 supports-Wdeclaration-after-statement... yes
checking if gcc -std=gnu99 supports-Wunused... yes
checking if gcc -std=gnu99 supports-Wuninitialized... yes
checking if gcc -std=gnu99 supports-Wshadow... yes
checking if gcc -std=gnu99 supports-Wcast-qual... yes
checking if gcc -std=gnu99 supports-Wmissing-noreturn... yes
checking if gcc -std=gnu99 supports-Wmissing-format-attribute... yes
checking if gcc -std=gnu99 supports-Wredundant-decls... yes
checking if gcc -std=gnu99 supports-Werror=implicit... yes
checking if gcc -std=gnu99 supports-Werror=nonnull... yes
checking if gcc -std=gnu99 supports-Werror=init-self... yes
checking if gcc -std=gnu99 supports-Werror=main... yes
checking if gcc -std=gnu99 supports-Werror=missing-braces... yes
checking if gcc -std=gnu99 supports-Werror=sequence-point... yes
checking if gcc -std=gnu99 supports-Werror=return-type... yes
checking if gcc -std=gnu99 supports-Werror=trigraphs... yes
checking if gcc -std=gnu99 supports-Werror=array-bounds... yes
checking if gcc -std=gnu99 supports-Werror=write-strings... yes
checking if gcc -std=gnu99 supports-Werror=address... yes
checking if gcc -std=gnu99 supports-Werror=int-to-pointer-cast... yes
checking if gcc -std=gnu99 supports-Werror=pointer-to-int-cast... yes
checking if gcc -std=gnu99 supports-pedantic... yes
checking if gcc -std=gnu99 supports-Werror... yes
checking if gcc -std=gnu99 supports-Werror=attributes... yes
checking whether make supports nested variables... yes
checking how to print strings... printf
checking for a sed that does not truncate output... (cached) /bin/sed
checking for fgrep... /bin/grep -F
checking for ld used by gcc -std=gnu99... /usr/bin/ld
checking if the linker (/usr/bin/ld) is GNU ld... yes
checking for BSD- or MS-compatible name lister (nm)... /usr/bin/nm -B
checking the name lister (/usr/bin/nm -B) interface... BSD nm
checking whether ln -s works... yes
checking the maximum length of command line arguments... 1572864
checking whether the shell understands some XSI constructs... yes
checking whether the shell understands "+="... yes
checking how to convert x86_64-unknown-linux-gnu file names to x86_64-unknown-linux-gnu format... func_convert_file_noop
checking how to convert x86_64-unknown-linux-gnu file names to toolchain format... func_convert_file_noop
checking for /usr/bin/ld option to reload object files... -r
checking for objdump... objdump
checking how to recognize dependent libraries... pass_all
checking for dlltool... no
checking how to associate runtime and link libraries... printf %s\n
checking for ar... ar
checking for archiver @FILE support... @
checking for strip... strip
checking for ranlib... ranlib
checking command to parse /usr/bin/nm -B output from gcc -std=gnu99 object... ok
checking for sysroot... no
checking for mt... mt
checking if mt is a manifest tool... no
checking for dlfcn.h... yes
checking for objdir... .libs
checking if gcc -std=gnu99 supports -fno-rtti -fno-exceptions... no
checking for gcc -std=gnu99 option to produce PIC... -fPIC -DPIC
checking if gcc -std=gnu99 PIC flag -fPIC -DPIC works... yes
checking if gcc -std=gnu99 static flag -static works... yes
checking if gcc -std=gnu99 supports -c -o file.o... yes
checking if gcc -std=gnu99 supports -c -o file.o... (cached) yes
checking whether the gcc -std=gnu99 linker (/usr/bin/ld -m elf_x86_64) supports shared libraries... yes
checking whether -lc should be explicitly linked in... no
checking dynamic linker characteristics... GNU/Linux ld.so
checking how to hardcode library paths into programs... immediate
checking whether stripping libraries is possible... yes
checking if libtool supports shared libraries... yes
checking whether to build shared libraries... yes
checking whether to build static libraries... no
checking for special C compiler options needed for large files... no
checking for _FILE_OFFSET_BITS value needed for large files... no
checking for GEN4ASM... no
checking for UDEV... no
checking for X11... yes
checking whether to include SNA support... checking sys/sysinfo.h usability... yes
checking sys/sysinfo.h presence... yes
checking for sys/sysinfo.h... yes
yes
checking whether to include UXA support... yes
checking for DRMINTEL... yes
checking whether to include GLAMOR support... no
checking if RANDR is defined... no
checking if RENDER is defined... no
checking if XF86DRI is defined... no
checking if DPMSExtension is defined... no
checking for XORG... no
configure: error: Package requirements (xorg-server >= 1.10 xproto fontsproto pixman-1 >= 0.24 ) were not met:

No package 'xorg-server' found
No package 'fontsproto' found

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables XORG_CFLAGS
and XORG_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.
```

What confuses me is this part during "sudo ./configure --enable-sna":
```
checking for XORG... no
configure: error: Package requirements (xorg-server >= 1.10 xproto fontsproto pixman-1 >= 0.24 ) were not met:

No package 'xorg-server' found
No package 'fontsproto' found
```

How do I get this to compile?  I keep hearing that SNA speeds the Intel GPU up a lot, so I really want to be able to try it out.

---

### Post by Stonecold1995 on 2012-10-04
Never-mind, I found out how to do this.  I asked on the KDE IRC channel, and after a bit of troubleshooting, I found that I had to put a text file called "20-intel.conf" in "/usr/share/X11/xorg.conf.d" with these contents:

```
Section "Device"
   Identifier  "Intel Graphics"
   Driver      "intel"
   Option      "AccelMethod"  "sna"
   Option      "SwapbuffersWait"  "false"
EndSection
```

And after rebooting (or restarting the X server), SNA is enabled and vsync is disabled..  The performance improvement was amazing (all my Touhou Project games now run at a smooth 60 fps, before some of them could barely hit 30 fps), and I experienced none of the instability occasionally reported with SNA.

The performance improvement brought about because of this change was really good.  Before enabling SNA, I got under 30 fps, but after I'm getting over 140, and that's even with Folding@home taking up 100% of the CPU!

---

