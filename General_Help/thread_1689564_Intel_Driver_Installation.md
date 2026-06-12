---
title: "Intel Driver Installation"
date: 2011-02-17
forum: General Help
---

### Post by GTMoraes on 2011-02-17
Hello. I'm using Ubuntu Maverick with Intel 4500MHD

So, I want to update my drivers, but I don't know how. there's _[this site]("http://intellinuxgraphics.org/index.html")_ (more precisely _[here.]("http://intellinuxgraphics.org/2010Q4.html")_) for Intel Drivers (apparently maintained by intel), but I don't get it.
Actually I don't even know which drivers am I using right now. I didn't change anything video related since the install.

Video works fine, so does animations. I just want to see if updating my drivers will fix some jitter I get when I move a window around the screen (fuzzy, loose style windows. Max effects) and improve my FPS in few games.

Thanks.

P.S.:
Tried on my own. I get this:
```

gtmoraes@GTM-Aspire1410:~/Drivers/xf86-video-intel-2.11.0$ sudo make install
Making install in uxa
make[1]: Entrando no diretório `/home/gtmoraes/Drivers/xf86-video-intel-2.11.0/uxa'
make[2]: Entrando no diretório `/home/gtmoraes/Drivers/xf86-video-intel-2.11.0/uxa'
make[2]: Nada a ser feito para `install-exec-am'.
make[2]: Nada a ser feito para `install-data-am'.
make[2]: Saindo do diretório `/home/gtmoraes/Drivers/xf86-video-intel-2.11.0/uxa'
make[1]: Saindo do diretório `/home/gtmoraes/Drivers/xf86-video-intel-2.11.0/uxa'
Making install in src
make[1]: Entrando no diretório `/home/gtmoraes/Drivers/xf86-video-intel-2.11.0/src'
Making install in xvmc
make[2]: Entrando no diretório `/home/gtmoraes/Drivers/xf86-video-intel-2.11.0/src/xvmc'
Making install in shader
make[3]: Entrando no diretório `/home/gtmoraes/Drivers/xf86-video-intel-2.11.0/src/xvmc/shader'
Making install in mc
make[4]: Entrando no diretório `/home/gtmoraes/Drivers/xf86-video-intel-2.11.0/src/xvmc/shader/mc'
make  install-am
make[5]: Entrando no diretório `/home/gtmoraes/Drivers/xf86-video-intel-2.11.0/src/xvmc/shader/mc'
make[6]: Entrando no diretório `/home/gtmoraes/Drivers/xf86-video-intel-2.11.0/src/xvmc/shader/mc'
make[6]: Nada a ser feito para `install-exec-am'.
make[6]: Nada a ser feito para `install-data-am'.
make[6]: Saindo do diretório `/home/gtmoraes/Drivers/xf86-video-intel-2.11.0/src/xvmc/shader/mc'
make[5]: Saindo do diretório `/home/gtmoraes/Drivers/xf86-video-intel-2.11.0/src/xvmc/shader/mc'
make[4]: Saindo do diretório `/home/gtmoraes/Drivers/xf86-video-intel-2.11.0/src/xvmc/shader/mc'
Making install in vld
make[4]: Entrando no diretório `/home/gtmoraes/Drivers/xf86-video-intel-2.11.0/src/xvmc/shader/vld'
make  install-am
make[5]: Entrando no diretório `/home/gtmoraes/Drivers/xf86-video-intel-2.11.0/src/xvmc/shader/vld'
make[6]: Entrando no diretório `/home/gtmoraes/Drivers/xf86-video-intel-2.11.0/src/xvmc/shader/vld'
make[6]: Nada a ser feito para `install-exec-am'.
make[6]: Nada a ser feito para `install-data-am'.
make[6]: Saindo do diretório `/home/gtmoraes/Drivers/xf86-video-intel-2.11.0/src/xvmc/shader/vld'
make[5]: Saindo do diretório `/home/gtmoraes/Drivers/xf86-video-intel-2.11.0/src/xvmc/shader/vld'
make[4]: Saindo do diretório `/home/gtmoraes/Drivers/xf86-video-intel-2.11.0/src/xvmc/shader/vld'
make[4]: Entrando no diretório `/home/gtmoraes/Drivers/xf86-video-intel-2.11.0/src/xvmc/shader'
make[5]: Entrando no diretório `/home/gtmoraes/Drivers/xf86-video-intel-2.11.0/src/xvmc/shader'
make[5]: Nada a ser feito para `install-exec-am'.
make[5]: Nada a ser feito para `install-data-am'.
make[5]: Saindo do diretório `/home/gtmoraes/Drivers/xf86-video-intel-2.11.0/src/xvmc/shader'
make[4]: Saindo do diretório `/home/gtmoraes/Drivers/xf86-video-intel-2.11.0/src/xvmc/shader'
make[3]: Saindo do diretório `/home/gtmoraes/Drivers/xf86-video-intel-2.11.0/src/xvmc/shader'
make[3]: Entrando no diretório `/home/gtmoraes/Drivers/xf86-video-intel-2.11.0/src/xvmc'
make[4]: Entrando no diretório `/home/gtmoraes/Drivers/xf86-video-intel-2.11.0/src/xvmc'
test -z "/usr/local/lib" || /bin/mkdir -p "/usr/local/lib"
make[4]: Nada a ser feito para `install-data-am'.
make[4]: Saindo do diretório `/home/gtmoraes/Drivers/xf86-video-intel-2.11.0/src/xvmc'
make[3]: Saindo do diretório `/home/gtmoraes/Drivers/xf86-video-intel-2.11.0/src/xvmc'
make[2]: Saindo do diretório `/home/gtmoraes/Drivers/xf86-video-intel-2.11.0/src/xvmc'
Making install in render_program
make[2]: Entrando no diretório `/home/gtmoraes/Drivers/xf86-video-intel-2.11.0/src/render_program'
make  install-am
make[3]: Entrando no diretório `/home/gtmoraes/Drivers/xf86-video-intel-2.11.0/src/render_program'
make[4]: Entrando no diretório `/home/gtmoraes/Drivers/xf86-video-intel-2.11.0/src/render_program'
make[4]: Nada a ser feito para `install-exec-am'.
make[4]: Nada a ser feito para `install-data-am'.
make[4]: Saindo do diretório `/home/gtmoraes/Drivers/xf86-video-intel-2.11.0/src/render_program'
make[3]: Saindo do diretório `/home/gtmoraes/Drivers/xf86-video-intel-2.11.0/src/render_program'
make[2]: Saindo do diretório `/home/gtmoraes/Drivers/xf86-video-intel-2.11.0/src/render_program'
make[2]: Entrando no diretório `/home/gtmoraes/Drivers/xf86-video-intel-2.11.0/src'
  CC     i810_driver.lo
In file included from i810_driver.c:73:
i830.h:81: error: redefinition of &#8216;struct list&#8217;
i830.h:86: error: conflicting types for &#8216;list_init&#8217;
/usr/include/xorg/list.h:35: note: previous definition of &#8216;list_init&#8217; was here
i830.h:92: error: conflicting types for &#8216;__list_add&#8217;
/usr/include/xorg/list.h:41: note: previous definition of &#8216;__list_add&#8217; was here
i830.h:103: error: conflicting types for &#8216;list_add&#8217;
/usr/include/xorg/list.h:52: note: previous definition of &#8216;list_add&#8217; was here
i830.h:109: error: conflicting types for &#8216;__list_del&#8217;
/usr/include/xorg/list.h:58: note: previous definition of &#8216;__list_del&#8217; was here
i830.h:116: error: conflicting types for &#8216;list_del&#8217;
/usr/include/xorg/list.h:65: note: previous definition of &#8216;list_del&#8217; was here
i830.h:123: error: conflicting types for &#8216;list_is_empty&#8217;
/usr/include/xorg/list.h:72: note: previous definition of &#8216;list_is_empty&#8217; was here
i810_driver.c: In function &#8216;I810FreeRec&#8217;:
i810_driver.c:369: warning: &#8216;Xfree&#8217; is deprecated (declared at /usr/include/xorg/os.h:234)
i810_driver.c: In function &#8216;I810PreInit&#8217;:
i810_driver.c:620: warning: &#8216;Xalloc&#8217; is deprecated (declared at /usr/include/xorg/os.h:221)
i810_driver.c: In function &#8216;I810ScreenInit&#8217;:
i810_driver.c:1900: warning: &#8216;Xcalloc&#8217; is deprecated (declared at /usr/include/xorg/os.h:225)
i810_driver.c: In function &#8216;I810CloseScreen&#8217;:
i810_driver.c:2309: warning: &#8216;Xfree&#8217; is deprecated (declared at /usr/include/xorg/os.h:234)
i810_driver.c:2315: warning: &#8216;Xfree&#8217; is deprecated (declared at /usr/include/xorg/os.h:234)
i810_driver.c:2336: warning: &#8216;Xfree&#8217; is deprecated (declared at /usr/include/xorg/os.h:234)
make[2]: ** [i810_driver.lo] Erro 1
make[2]: Saindo do diretório `/home/gtmoraes/Drivers/xf86-video-intel-2.11.0/src'
make[1]: ** [install-recursive] Erro 1
make[1]: Saindo do diretório `/home/gtmoraes/Drivers/xf86-video-intel-2.11.0/src'
make: ** [install-recursive] Erro 1

```
There's some parts in portuguese, but I believe they're not important for the fix of this problem (mostly, they're "Entering folder ..." and "Leaving folder.."). I've had ran the command "./configure" and "make" before running "make install", as the install instructions says to do.
do I need to shut off the X server?

--------------------
On another thread, someone with a similar issue has been asked to post the "./configure" output.
It might be necessary, so I'll agilize the process:
```


gtmoraes@GTM-Aspire1410:~/Drivers/xf86-video-intel-2.11.0$ ./configure
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for a thread-safe mkdir -p... /bin/mkdir -p
checking for gawk... no
checking for mawk... mawk
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
checking for gcc option to accept ISO C99... -std=gnu99
checking for pkg-config... /usr/bin/pkg-config
checking pkg-config is at least version 0.9.0... yes
checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
Package xorg-macros was not found in the pkg-config search path.
Perhaps you should add the directory containing `xorg-macros.pc'
to the PKG_CONFIG_PATH environment variable
No package 'xorg-macros' found
checking for a sed that does not truncate output... /bin/sed
checking for fgrep... /bin/grep -F
checking for ld used by gcc -std=gnu99... /usr/bin/ld
checking if the linker (/usr/bin/ld) is GNU ld... yes
checking for BSD- or MS-compatible name lister (nm)... /usr/bin/nm -B
checking the name lister (/usr/bin/nm -B) interface... BSD nm
checking whether ln -s works... yes
checking the maximum length of command line arguments... 1572864
checking whether the shell understands some XSI constructs... yes
checking whether the shell understands "+="... yes
checking for /usr/bin/ld option to reload object files... -r
checking for objdump... objdump
checking how to recognize dependent libraries... pass_all
checking for ar... ar
checking for strip... strip
checking for ranlib... ranlib
checking command to parse /usr/bin/nm -B output from gcc -std=gnu99 object... ok
checking for dlfcn.h... yes
checking for objdir... .libs
checking if gcc -std=gnu99 supports -fno-rtti -fno-exceptions... no
checking for gcc -std=gnu99 option to produce PIC... -fPIC -DPIC
checking if gcc -std=gnu99 PIC flag -fPIC -DPIC works... yes
checking if gcc -std=gnu99 static flag -static works... yes
checking if gcc -std=gnu99 supports -c -o file.o... yes
checking if gcc -std=gnu99 supports -c -o file.o... (cached) yes
checking whether the gcc -std=gnu99 linker (/usr/bin/ld) supports shared libraries... yes
checking whether -lc should be explicitly linked in... no
checking dynamic linker characteristics... GNU/Linux ld.so
checking how to hardcode library paths into programs... immediate
checking whether stripping libraries is possible... yes
checking if libtool supports shared libraries... yes
checking whether to build shared libraries... yes
checking whether to build static libraries... no
checking for gcc... (cached) gcc
checking whether we are using the GNU C compiler... (cached) yes
checking whether gcc accepts -g... (cached) yes
checking for gcc option to accept ISO C89... (cached) none needed
checking dependency style of gcc... (cached) gcc3
checking whether gcc and cc understand -c and -o together... yes
checking for GEN4ASM... no
checking for ANSI C header files... (cached) yes
checking sys/mman.h usability... yes
checking sys/mman.h presence... yes
checking for sys/mman.h... yes
checking for mprotect... yes
checking if RANDR is defined... yes
checking if RENDER is defined... yes
checking if XF86DRI is defined... yes
checking if DPMSExtension is defined... yes
checking for XORG... yes
checking for DRM... yes
checking for PCIACCESS... yes
checking for XEXT... yes
checking whether to include DRI support... checking for /usr/include/xorg/dri.h... yes
checking for /usr/include/xorg/sarea.h... yes
checking for /usr/include/xorg/dristruct.h... yes
checking whether to include DRI support... yes
checking for DRI... yes
checking for XVMCLIB... no
checking whether to include XvMC support... no
configure: creating ./config.status
config.status: creating Makefile
config.status: creating uxa/Makefile
config.status: creating src/Makefile
config.status: creating src/xvmc/Makefile
config.status: creating src/xvmc/shader/Makefile
config.status: creating src/xvmc/shader/mc/Makefile
config.status: creating src/xvmc/shader/vld/Makefile
config.status: creating man/Makefile
config.status: creating src/render_program/Makefile
config.status: creating config.h
config.status: config.h is unchanged
config.status: executing depfiles commands
config.status: executing libtool commands
gtmoraes@GTM-Aspire1410:~/Drivers/xf86-video-intel-2.11.0$ 

```
---
I've seen somewhere else tellin' someone to install the GCC and G++ from the Synaptic. I did it, but the output is still the same.

---

### Post by GTMoraes on 2011-02-18
I'm sure somebody here knows how to fix it...

---

### Post by GTMoraes on 2011-02-20
Nobody?

---

### Post by jerenept on 2011-02-20
Did you use "sudo make" and "sudo make install"? Also you might try installing "build-essential" which would pull in all the packages you need to compile stuff.

---

### Post by jerenept on 2011-02-20
P.S. Yeah, you might want to stop the X Server: run "sudo stop gdm" (after closing all programs and saving your data) and then press <ctrl><alt><F1>. Enter your login credentials.
You may want to try a reboot afterwards as well.

---

### Post by GTMoraes on 2011-02-20
Hey, thanks for the reply!

No deal, gives me the same error message.
I see a lot of "*software* is deprecated" messages. What does this mean? Is that relevant to something? Also, I've noticed the error messages begin after the line "  CC     i810_driver.lo". 

I don't know what to do and I rely on you guys help
I'll be waiting for an answer. 
Thank you everybody :)

----------------------
Hey, newsflash. I've found a command over the net and ran it. Installation procedure went further, but still stops at "i810_driver.lo". Check it out:
```


gtmoraes@GTM-Aspire1410:~/Drivers/xf86-video-intel-2.11.0$ ./configure
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for a thread-safe mkdir -p... /bin/mkdir -p
checking for gawk... no
checking for mawk... mawk
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
checking for gcc option to accept ISO C99... -std=gnu99
checking for pkg-config... /usr/bin/pkg-config
checking pkg-config is at least version 0.9.0... yes
checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
checking for a sed that does not truncate output... /bin/sed
checking for fgrep... /bin/grep -F
checking for ld used by gcc -std=gnu99... /usr/bin/ld
checking if the linker (/usr/bin/ld) is GNU ld... yes
checking for BSD- or MS-compatible name lister (nm)... /usr/bin/nm -B
checking the name lister (/usr/bin/nm -B) interface... BSD nm
checking whether ln -s works... yes
checking the maximum length of command line arguments... 1572864
checking whether the shell understands some XSI constructs... yes
checking whether the shell understands "+="... yes
checking for /usr/bin/ld option to reload object files... -r
checking for objdump... objdump
checking how to recognize dependent libraries... pass_all
checking for ar... ar
checking for strip... strip
checking for ranlib... ranlib
checking command to parse /usr/bin/nm -B output from gcc -std=gnu99 object... ok
checking for dlfcn.h... yes
checking for objdir... .libs
checking if gcc -std=gnu99 supports -fno-rtti -fno-exceptions... no
checking for gcc -std=gnu99 option to produce PIC... -fPIC -DPIC
checking if gcc -std=gnu99 PIC flag -fPIC -DPIC works... yes
checking if gcc -std=gnu99 static flag -static works... yes
checking if gcc -std=gnu99 supports -c -o file.o... yes
checking if gcc -std=gnu99 supports -c -o file.o... (cached) yes
checking whether the gcc -std=gnu99 linker (/usr/bin/ld) supports shared libraries... yes
checking whether -lc should be explicitly linked in... no
checking dynamic linker characteristics... GNU/Linux ld.so
checking how to hardcode library paths into programs... immediate
checking whether stripping libraries is possible... yes
checking if libtool supports shared libraries... yes
checking whether to build shared libraries... yes
checking whether to build static libraries... no
checking for gcc... (cached) gcc
checking whether we are using the GNU C compiler... (cached) yes
checking whether gcc accepts -g... (cached) yes
checking for gcc option to accept ISO C89... (cached) none needed
checking dependency style of gcc... (cached) gcc3
checking whether gcc and cc understand -c and -o together... yes
checking for GEN4ASM... no
checking for ANSI C header files... (cached) yes
checking sys/mman.h usability... yes
checking sys/mman.h presence... yes
checking for sys/mman.h... yes
checking for mprotect... yes
checking if RANDR is defined... yes
checking if RENDER is defined... yes
checking if XF86DRI is defined... yes
checking if DPMSExtension is defined... yes
checking for XORG... yes
checking for DRM... yes
checking for PCIACCESS... yes
checking for XEXT... yes
checking whether to include DRI support... checking for /usr/include/xorg/dri.h... yes
checking for /usr/include/xorg/sarea.h... yes
checking for /usr/include/xorg/dristruct.h... yes
checking whether to include DRI support... yes
checking for DRI... yes
checking for XVMCLIB... yes
checking whether to include XvMC support... yes
configure: creating ./config.status
config.status: creating Makefile
config.status: creating uxa/Makefile
config.status: creating src/Makefile
config.status: creating src/xvmc/Makefile
config.status: creating src/xvmc/shader/Makefile
config.status: creating src/xvmc/shader/mc/Makefile
config.status: creating src/xvmc/shader/vld/Makefile
config.status: creating man/Makefile
config.status: creating src/render_program/Makefile
config.status: creating config.h
config.status: executing depfiles commands
config.status: executing libtool commands
gtmoraes@GTM-Aspire1410:~/Drivers/xf86-video-intel-2.11.0$ sudo make
make  all-recursive
make[1]: Entrando no diretório `/home/gtmoraes/Drivers/xf86-video-intel-2.11.0'
Making all in uxa
make[2]: Entrando no diretório `/home/gtmoraes/Drivers/xf86-video-intel-2.11.0/uxa'
  CC     uxa.lo
In file included from uxa.c:37:
uxa-priv.h: In function &#8216;uxa_get_screen&#8217;:
uxa-priv.h:194: warning: passing argument 2 of &#8216;dixLookupPrivate&#8217; from incompatible pointer type
/usr/include/xorg/privates.h:162: note: expected &#8216;DevPrivateKey&#8217; but argument is of type &#8216;int *&#8217;
uxa.c: In function &#8216;uxa_close_screen&#8217;:
uxa.c:398: warning: &#8216;Xfree&#8217; is deprecated (declared at /usr/include/xorg/os.h:234)
uxa.c: In function &#8216;uxa_driver_alloc&#8217;:
uxa.c:415: warning: &#8216;Xcalloc&#8217; is deprecated (declared at /usr/include/xorg/os.h:225)
uxa.c: In function &#8216;uxa_driver_init&#8217;:
uxa.c:467: warning: &#8216;Xcalloc&#8217; is deprecated (declared at /usr/include/xorg/os.h:225)
uxa.c:478: warning: passing argument 2 of &#8216;dixSetPrivate&#8217; from incompatible pointer type
/usr/include/xorg/privates.h:145: note: expected &#8216;DevPrivateKey&#8217; but argument is of type &#8216;int *&#8217;
  CC     uxa-accel.lo
In file included from uxa-accel.c:33:
uxa-priv.h: In function &#8216;uxa_get_screen&#8217;:
uxa-priv.h:194: warning: passing argument 2 of &#8216;dixLookupPrivate&#8217; from incompatible pointer type
/usr/include/xorg/privates.h:162: note: expected &#8216;DevPrivateKey&#8217; but argument is of type &#8216;int *&#8217;
uxa-accel.c: In function &#8216;uxa_poly_point&#8217;:
uxa-accel.c:526: warning: &#8216;Xalloc&#8217; is deprecated (declared at /usr/include/xorg/os.h:221)
uxa-accel.c:540: warning: &#8216;Xfree&#8217; is deprecated (declared at /usr/include/xorg/os.h:234)
uxa-accel.c: In function &#8216;uxa_poly_lines&#8217;:
uxa-accel.c:563: warning: &#8216;Xalloc&#8217; is deprecated (declared at /usr/include/xorg/os.h:221)
uxa-accel.c:579: warning: &#8216;Xfree&#8217; is deprecated (declared at /usr/include/xorg/os.h:234)
uxa-accel.c:603: warning: &#8216;Xfree&#8217; is deprecated (declared at /usr/include/xorg/os.h:234)
uxa-accel.c: In function &#8216;uxa_poly_segment&#8217;:
uxa-accel.c:632: warning: &#8216;Xalloc&#8217; is deprecated (declared at /usr/include/xorg/os.h:221)
uxa-accel.c:660: warning: &#8216;Xfree&#8217; is deprecated (declared at /usr/include/xorg/os.h:234)
  CC     uxa-glyphs.lo
In file included from uxa-glyphs.c:49:
uxa-priv.h: In function &#8216;uxa_get_screen&#8217;:
uxa-priv.h:194: warning: passing argument 2 of &#8216;dixLookupPrivate&#8217; from incompatible pointer type
/usr/include/xorg/privates.h:162: note: expected &#8216;DevPrivateKey&#8217; but argument is of type &#8216;int *&#8217;
uxa-glyphs.c: In function &#8216;uxa_unrealize_glyph_caches&#8217;:
uxa-glyphs.c:134: warning: &#8216;Xfree&#8217; is deprecated (declared at /usr/include/xorg/os.h:234)
uxa-glyphs.c:139: warning: &#8216;Xfree&#8217; is deprecated (declared at /usr/include/xorg/os.h:234)
uxa-glyphs.c: In function &#8216;uxa_realize_glyph_caches&#8217;:
uxa-glyphs.c:219: warning: &#8216;Xalloc&#8217; is deprecated (declared at /usr/include/xorg/os.h:221)
uxa-glyphs.c:221: warning: &#8216;Xalloc&#8217; is deprecated (declared at /usr/include/xorg/os.h:221)
  CC     uxa-render.lo
In file included from uxa-render.c:31:
uxa-priv.h: In function &#8216;uxa_get_screen&#8217;:
uxa-priv.h:194: warning: passing argument 2 of &#8216;dixLookupPrivate&#8217; from incompatible pointer type
/usr/include/xorg/privates.h:162: note: expected &#8216;DevPrivateKey&#8217; but argument is of type &#8216;int *&#8217;
  CC     uxa-unaccel.lo
In file included from uxa-unaccel.c:24:
uxa-priv.h: In function &#8216;uxa_get_screen&#8217;:
uxa-priv.h:194: warning: passing argument 2 of &#8216;dixLookupPrivate&#8217; from incompatible pointer type
/usr/include/xorg/privates.h:162: note: expected &#8216;DevPrivateKey&#8217; but argument is of type &#8216;int *&#8217;
  CCLD   libuxa.la
make[2]: Saindo do diretório `/home/gtmoraes/Drivers/xf86-video-intel-2.11.0/uxa'
Making all in src
make[2]: Entrando no diretório `/home/gtmoraes/Drivers/xf86-video-intel-2.11.0/src'
Making all in xvmc
make[3]: Entrando no diretório `/home/gtmoraes/Drivers/xf86-video-intel-2.11.0/src/xvmc'
Making all in shader
make[4]: Entrando no diretório `/home/gtmoraes/Drivers/xf86-video-intel-2.11.0/src/xvmc/shader'
Making all in mc
make[5]: Entrando no diretório `/home/gtmoraes/Drivers/xf86-video-intel-2.11.0/src/xvmc/shader/mc'
make  all-am
make[6]: Entrando no diretório `/home/gtmoraes/Drivers/xf86-video-intel-2.11.0/src/xvmc/shader/mc'
make[6]: Nada a ser feito para `all-am'.
make[6]: Saindo do diretório `/home/gtmoraes/Drivers/xf86-video-intel-2.11.0/src/xvmc/shader/mc'
make[5]: Saindo do diretório `/home/gtmoraes/Drivers/xf86-video-intel-2.11.0/src/xvmc/shader/mc'
Making all in vld
make[5]: Entrando no diretório `/home/gtmoraes/Drivers/xf86-video-intel-2.11.0/src/xvmc/shader/vld'
make  all-am
make[6]: Entrando no diretório `/home/gtmoraes/Drivers/xf86-video-intel-2.11.0/src/xvmc/shader/vld'
make[6]: Nada a ser feito para `all-am'.
make[6]: Saindo do diretório `/home/gtmoraes/Drivers/xf86-video-intel-2.11.0/src/xvmc/shader/vld'
make[5]: Saindo do diretório `/home/gtmoraes/Drivers/xf86-video-intel-2.11.0/src/xvmc/shader/vld'
make[5]: Entrando no diretório `/home/gtmoraes/Drivers/xf86-video-intel-2.11.0/src/xvmc/shader'
make[5]: Nada a ser feito para `all-am'.
make[5]: Saindo do diretório `/home/gtmoraes/Drivers/xf86-video-intel-2.11.0/src/xvmc/shader'
make[4]: Saindo do diretório `/home/gtmoraes/Drivers/xf86-video-intel-2.11.0/src/xvmc/shader'
make[4]: Entrando no diretório `/home/gtmoraes/Drivers/xf86-video-intel-2.11.0/src/xvmc'
  CC     libI810XvMC_la-I810XvMC.lo
  CCLD   libI810XvMC.la
  CC     libIntelXvMC_la-intel_xvmc.lo
  CC     libIntelXvMC_la-intel_xvmc_dump.lo
  CC     libIntelXvMC_la-i915_xvmc.lo
  CC     libIntelXvMC_la-i965_xvmc.lo
  CC     libIntelXvMC_la-xvmc_vld.lo
  CC     libIntelXvMC_la-intel_batchbuffer.lo
  CCLD   libIntelXvMC.la
make[4]: Saindo do diretório `/home/gtmoraes/Drivers/xf86-video-intel-2.11.0/src/xvmc'
make[3]: Saindo do diretório `/home/gtmoraes/Drivers/xf86-video-intel-2.11.0/src/xvmc'
Making all in render_program
make[3]: Entrando no diretório `/home/gtmoraes/Drivers/xf86-video-intel-2.11.0/src/render_program'
make  all-am
make[4]: Entrando no diretório `/home/gtmoraes/Drivers/xf86-video-intel-2.11.0/src/render_program'
make[4]: Nada a ser feito para `all-am'.
make[4]: Saindo do diretório `/home/gtmoraes/Drivers/xf86-video-intel-2.11.0/src/render_program'
make[3]: Saindo do diretório `/home/gtmoraes/Drivers/xf86-video-intel-2.11.0/src/render_program'
make[3]: Entrando no diretório `/home/gtmoraes/Drivers/xf86-video-intel-2.11.0/src'
  CC     i810_accel.lo
  CC     i810_cursor.lo
  CC     i810_dga.lo
i810_dga.c: In function &#8216;I810DGAInit&#8217;:
i810_dga.c:87: warning: &#8216;Xrealloc&#8217; is deprecated (declared at /usr/include/xorg/os.h:229)
i810_dga.c:90: warning: &#8216;Xfree&#8217; is deprecated (declared at /usr/include/xorg/os.h:234)
  CC     i810_driver.lo
In file included from i810_driver.c:73:
i830.h:81: error: redefinition of &#8216;struct list&#8217;
i830.h:86: error: conflicting types for &#8216;list_init&#8217;
/usr/include/xorg/list.h:35: note: previous definition of &#8216;list_init&#8217; was here
i830.h:92: error: conflicting types for &#8216;__list_add&#8217;
/usr/include/xorg/list.h:41: note: previous definition of &#8216;__list_add&#8217; was here
i830.h:103: error: conflicting types for &#8216;list_add&#8217;
/usr/include/xorg/list.h:52: note: previous definition of &#8216;list_add&#8217; was here
i830.h:109: error: conflicting types for &#8216;__list_del&#8217;
/usr/include/xorg/list.h:58: note: previous definition of &#8216;__list_del&#8217; was here
i830.h:116: error: conflicting types for &#8216;list_del&#8217;
/usr/include/xorg/list.h:65: note: previous definition of &#8216;list_del&#8217; was here
i830.h:123: error: conflicting types for &#8216;list_is_empty&#8217;
/usr/include/xorg/list.h:72: note: previous definition of &#8216;list_is_empty&#8217; was here
i810_driver.c: In function &#8216;I810FreeRec&#8217;:
i810_driver.c:369: warning: &#8216;Xfree&#8217; is deprecated (declared at /usr/include/xorg/os.h:234)
i810_driver.c: In function &#8216;I810PreInit&#8217;:
i810_driver.c:620: warning: &#8216;Xalloc&#8217; is deprecated (declared at /usr/include/xorg/os.h:221)
i810_driver.c: In function &#8216;I810ScreenInit&#8217;:
i810_driver.c:1900: warning: &#8216;Xcalloc&#8217; is deprecated (declared at /usr/include/xorg/os.h:225)
i810_driver.c: In function &#8216;I810CloseScreen&#8217;:
i810_driver.c:2309: warning: &#8216;Xfree&#8217; is deprecated (declared at /usr/include/xorg/os.h:234)
i810_driver.c:2315: warning: &#8216;Xfree&#8217; is deprecated (declared at /usr/include/xorg/os.h:234)
i810_driver.c:2336: warning: &#8216;Xfree&#8217; is deprecated (declared at /usr/include/xorg/os.h:234)
make[3]: ** [i810_driver.lo] Erro 1
make[3]: Saindo do diretório `/home/gtmoraes/Drivers/xf86-video-intel-2.11.0/src'
make[2]: ** [all-recursive] Erro 1
make[2]: Saindo do diretório `/home/gtmoraes/Drivers/xf86-video-intel-2.11.0/src'
make[1]: ** [all-recursive] Erro 1
make[1]: Saindo do diretório `/home/gtmoraes/Drivers/xf86-video-intel-2.11.0'
make: ** [all] Erro 2
gtmoraes@GTM-Aspire1410:~/Drivers/xf86-video-intel-2.11.0$ sudo make install
Making install in uxa
make[1]: Entrando no diretório `/home/gtmoraes/Drivers/xf86-video-intel-2.11.0/uxa'
make[2]: Entrando no diretório `/home/gtmoraes/Drivers/xf86-video-intel-2.11.0/uxa'
make[2]: Nada a ser feito para `install-exec-am'.
make[2]: Nada a ser feito para `install-data-am'.
make[2]: Saindo do diretório `/home/gtmoraes/Drivers/xf86-video-intel-2.11.0/uxa'
make[1]: Saindo do diretório `/home/gtmoraes/Drivers/xf86-video-intel-2.11.0/uxa'
Making install in src
make[1]: Entrando no diretório `/home/gtmoraes/Drivers/xf86-video-intel-2.11.0/src'
Making install in xvmc
make[2]: Entrando no diretório `/home/gtmoraes/Drivers/xf86-video-intel-2.11.0/src/xvmc'
Making install in shader
make[3]: Entrando no diretório `/home/gtmoraes/Drivers/xf86-video-intel-2.11.0/src/xvmc/shader'
Making install in mc
make[4]: Entrando no diretório `/home/gtmoraes/Drivers/xf86-video-intel-2.11.0/src/xvmc/shader/mc'
make  install-am
make[5]: Entrando no diretório `/home/gtmoraes/Drivers/xf86-video-intel-2.11.0/src/xvmc/shader/mc'
make[6]: Entrando no diretório `/home/gtmoraes/Drivers/xf86-video-intel-2.11.0/src/xvmc/shader/mc'
make[6]: Nada a ser feito para `install-exec-am'.
make[6]: Nada a ser feito para `install-data-am'.
make[6]: Saindo do diretório `/home/gtmoraes/Drivers/xf86-video-intel-2.11.0/src/xvmc/shader/mc'
make[5]: Saindo do diretório `/home/gtmoraes/Drivers/xf86-video-intel-2.11.0/src/xvmc/shader/mc'
make[4]: Saindo do diretório `/home/gtmoraes/Drivers/xf86-video-intel-2.11.0/src/xvmc/shader/mc'
Making install in vld
make[4]: Entrando no diretório `/home/gtmoraes/Drivers/xf86-video-intel-2.11.0/src/xvmc/shader/vld'
make  install-am
make[5]: Entrando no diretório `/home/gtmoraes/Drivers/xf86-video-intel-2.11.0/src/xvmc/shader/vld'
make[6]: Entrando no diretório `/home/gtmoraes/Drivers/xf86-video-intel-2.11.0/src/xvmc/shader/vld'
make[6]: Nada a ser feito para `install-exec-am'.
make[6]: Nada a ser feito para `install-data-am'.
make[6]: Saindo do diretório `/home/gtmoraes/Drivers/xf86-video-intel-2.11.0/src/xvmc/shader/vld'
make[5]: Saindo do diretório `/home/gtmoraes/Drivers/xf86-video-intel-2.11.0/src/xvmc/shader/vld'
make[4]: Saindo do diretório `/home/gtmoraes/Drivers/xf86-video-intel-2.11.0/src/xvmc/shader/vld'
make[4]: Entrando no diretório `/home/gtmoraes/Drivers/xf86-video-intel-2.11.0/src/xvmc/shader'
make[5]: Entrando no diretório `/home/gtmoraes/Drivers/xf86-video-intel-2.11.0/src/xvmc/shader'
make[5]: Nada a ser feito para `install-exec-am'.
make[5]: Nada a ser feito para `install-data-am'.
make[5]: Saindo do diretório `/home/gtmoraes/Drivers/xf86-video-intel-2.11.0/src/xvmc/shader'
make[4]: Saindo do diretório `/home/gtmoraes/Drivers/xf86-video-intel-2.11.0/src/xvmc/shader'
make[3]: Saindo do diretório `/home/gtmoraes/Drivers/xf86-video-intel-2.11.0/src/xvmc/shader'
make[3]: Entrando no diretório `/home/gtmoraes/Drivers/xf86-video-intel-2.11.0/src/xvmc'
make[4]: Entrando no diretório `/home/gtmoraes/Drivers/xf86-video-intel-2.11.0/src/xvmc'
test -z "/usr/local/lib" || /bin/mkdir -p "/usr/local/lib"
 /bin/bash ../../libtool   --mode=install /usr/bin/install -c   libI810XvMC.la libIntelXvMC.la '/usr/local/lib'
libtool: install: /usr/bin/install -c .libs/libI810XvMC.so.1.0.0 /usr/local/lib/libI810XvMC.so.1.0.0
libtool: install: (cd /usr/local/lib && { ln -s -f libI810XvMC.so.1.0.0 libI810XvMC.so.1 || { rm -f libI810XvMC.so.1 && ln -s libI810XvMC.so.1.0.0 libI810XvMC.so.1; }; })
libtool: install: (cd /usr/local/lib && { ln -s -f libI810XvMC.so.1.0.0 libI810XvMC.so || { rm -f libI810XvMC.so && ln -s libI810XvMC.so.1.0.0 libI810XvMC.so; }; })
libtool: install: /usr/bin/install -c .libs/libI810XvMC.lai /usr/local/lib/libI810XvMC.la
libtool: install: /usr/bin/install -c .libs/libIntelXvMC.so.1.0.0 /usr/local/lib/libIntelXvMC.so.1.0.0
libtool: install: (cd /usr/local/lib && { ln -s -f libIntelXvMC.so.1.0.0 libIntelXvMC.so.1 || { rm -f libIntelXvMC.so.1 && ln -s libIntelXvMC.so.1.0.0 libIntelXvMC.so.1; }; })
libtool: install: (cd /usr/local/lib && { ln -s -f libIntelXvMC.so.1.0.0 libIntelXvMC.so || { rm -f libIntelXvMC.so && ln -s libIntelXvMC.so.1.0.0 libIntelXvMC.so; }; })
libtool: install: /usr/bin/install -c .libs/libIntelXvMC.lai /usr/local/lib/libIntelXvMC.la
libtool: finish: PATH="/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/X11R6/bin:/sbin" ldconfig -n /usr/local/lib
----------------------------------------------------------------------
Libraries have been installed in:
   /usr/local/lib

If you ever happen to want to link against installed libraries
in a given directory, LIBDIR, you must either use libtool, and
specify the full pathname of the library, or use the `-LLIBDIR'
flag during linking and do at least one of the following:
   - add LIBDIR to the `LD_LIBRARY_PATH' environment variable
     during execution
   - add LIBDIR to the `LD_RUN_PATH' environment variable
     during linking
   - use the `-Wl,-rpath -Wl,LIBDIR' linker flag
   - have your system administrator add LIBDIR to `/etc/ld.so.conf'

See any operating system documentation about shared libraries for
more information, such as the ld(1) and ld.so(8) manual pages.
----------------------------------------------------------------------
make[4]: Nada a ser feito para `install-data-am'.
make[4]: Saindo do diretório `/home/gtmoraes/Drivers/xf86-video-intel-2.11.0/src/xvmc'
make[3]: Saindo do diretório `/home/gtmoraes/Drivers/xf86-video-intel-2.11.0/src/xvmc'
make[2]: Saindo do diretório `/home/gtmoraes/Drivers/xf86-video-intel-2.11.0/src/xvmc'
Making install in render_program
make[2]: Entrando no diretório `/home/gtmoraes/Drivers/xf86-video-intel-2.11.0/src/render_program'
make  install-am
make[3]: Entrando no diretório `/home/gtmoraes/Drivers/xf86-video-intel-2.11.0/src/render_program'
make[4]: Entrando no diretório `/home/gtmoraes/Drivers/xf86-video-intel-2.11.0/src/render_program'
make[4]: Nada a ser feito para `install-exec-am'.
make[4]: Nada a ser feito para `install-data-am'.
make[4]: Saindo do diretório `/home/gtmoraes/Drivers/xf86-video-intel-2.11.0/src/render_program'
make[3]: Saindo do diretório `/home/gtmoraes/Drivers/xf86-video-intel-2.11.0/src/render_program'
make[2]: Saindo do diretório `/home/gtmoraes/Drivers/xf86-video-intel-2.11.0/src/render_program'
make[2]: Entrando no diretório `/home/gtmoraes/Drivers/xf86-video-intel-2.11.0/src'
  CC     i810_driver.lo
In file included from i810_driver.c:73:
i830.h:81: error: redefinition of &#8216;struct list&#8217;
i830.h:86: error: conflicting types for &#8216;list_init&#8217;
/usr/include/xorg/list.h:35: note: previous definition of &#8216;list_init&#8217; was here
i830.h:92: error: conflicting types for &#8216;__list_add&#8217;
/usr/include/xorg/list.h:41: note: previous definition of &#8216;__list_add&#8217; was here
i830.h:103: error: conflicting types for &#8216;list_add&#8217;
/usr/include/xorg/list.h:52: note: previous definition of &#8216;list_add&#8217; was here
i830.h:109: error: conflicting types for &#8216;__list_del&#8217;
/usr/include/xorg/list.h:58: note: previous definition of &#8216;__list_del&#8217; was here
i830.h:116: error: conflicting types for &#8216;list_del&#8217;
/usr/include/xorg/list.h:65: note: previous definition of &#8216;list_del&#8217; was here
i830.h:123: error: conflicting types for &#8216;list_is_empty&#8217;
/usr/include/xorg/list.h:72: note: previous definition of &#8216;list_is_empty&#8217; was here
i810_driver.c: In function &#8216;I810FreeRec&#8217;:
i810_driver.c:369: warning: &#8216;Xfree&#8217; is deprecated (declared at /usr/include/xorg/os.h:234)
i810_driver.c: In function &#8216;I810PreInit&#8217;:
i810_driver.c:620: warning: &#8216;Xalloc&#8217; is deprecated (declared at /usr/include/xorg/os.h:221)
i810_driver.c: In function &#8216;I810ScreenInit&#8217;:
i810_driver.c:1900: warning: &#8216;Xcalloc&#8217; is deprecated (declared at /usr/include/xorg/os.h:225)
i810_driver.c: In function &#8216;I810CloseScreen&#8217;:
i810_driver.c:2309: warning: &#8216;Xfree&#8217; is deprecated (declared at /usr/include/xorg/os.h:234)
i810_driver.c:2315: warning: &#8216;Xfree&#8217; is deprecated (declared at /usr/include/xorg/os.h:234)
i810_driver.c:2336: warning: &#8216;Xfree&#8217; is deprecated (declared at /usr/include/xorg/os.h:234)
make[2]: ** [i810_driver.lo] Erro 1
make[2]: Saindo do diretório `/home/gtmoraes/Drivers/xf86-video-intel-2.11.0/src'
make[1]: ** [install-recursive] Erro 1
make[1]: Saindo do diretório `/home/gtmoraes/Drivers/xf86-video-intel-2.11.0/src'
make: ** [install-recursive] Erro 1

```
It's huge, sorry. I still have faith I'll install those drivers before the release of 11.04 :)

---

