---
title: "pkg-config problem"
date: 2010-02-21
forum: General Help
---

### Post by guriinii on 2010-02-21
I am trying to install xcompmgr-dana but I seem to be having a problem with pkg-config when I use "./configure"

```

guriinii@singularity:~/Desktop/xcompmgr-dana$ ./configure
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for a thread-safe mkdir -p... /bin/mkdir -p
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking whether to enable maintainer-specific portions of Makefiles... no
checking for gcc... gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables... 
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ISO C89... none needed
checking for style of include used by make... GNU
checking dependency style of gcc... gcc3
checking how to run the C preprocessor... gcc -E
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
checking for stdlib.h... (cached) yes
checking sys/time.h usability... yes
checking sys/time.h presence... yes
checking for sys/time.h... yes
checking for unistd.h... (cached) yes
checking whether time.h and sys/time.h may both be included... yes
checking whether struct tm is in sys/time.h or time.h... time.h
checking for stdlib.h... (cached) yes
checking for GNU libc compatible malloc... yes
checking for gettimeofday... yes
checking for localtime_r... yes
checking for pkg-config... /usr/bin/pkg-config
checking pkg-config is at least version 0.9.0... yes
checking for XCOMPMGR... configure: error: Package requirements (xcomposite xfixes xdamage xrender) were not met:

No package 'xcomposite' found
No package 'xfixes' found
No package 'xdamage' found
No package 'xrender' found

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables XCOMPMGR_CFLAGS
and XCOMPMGR_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.


```

I've researched into it but this is new to me and I'm lost.

Can anyone help?

---

### Post by gmargo on 2010-02-21
Install these packages and try again: 

[LIST]
[*]libxcomposite-dev
[*]libxfixes-dev
[*]libxdamage-dev
[*]libxrender-dev
[/LIST]

---

### Post by guriinii on 2010-02-21
Thanks worked perfectly.

---

