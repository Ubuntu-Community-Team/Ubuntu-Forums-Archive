---
title: "Thunderbird 3.1"
date: 2010-08-14
forum: General Help
---

### Post by pqwoerituytrueiwoq on 2010-08-14
Using Ubuntu 10.04 (64 bit)
When should I receive an update for Thunderbird 3.1
I am growing impatient
I really want some features that are in it i had in Thunderbird 2
**Solution in post 7**

---

### Post by zerubbabel on 2010-08-15
See [this thread]("http://ubuntuforums.org/showpost.php?p=9509778&postcount=6").

---

### Post by pqwoerituytrueiwoq on 2010-08-18
thanks but after adding the source i was not able to find any update for thunderbird
check software center, package manager, and *sudo apt-get install thunderbird*
here is my *sudo apt-get update output*:
```
Hit http://ppa.launchpad.net lucid Release.gpg
Ign http://ppa.launchpad.net/ubuntu-mozilla-security/ppa/ubuntu/ lucid/main Translation-en_US     
Hit http://ppa.launchpad.net lucid Release.gpg                                                    
Get:1 http://dl.google.com stable Release.gpg [189B]                                               
Ign http://dl.google.com/linux/chrome/deb/ stable/main Translation-en_US                                                     
Hit http://us.archive.ubuntu.com lucid Release.gpg                                                 
Ign http://us.archive.ubuntu.com/ubuntu/ lucid/main Translation-en_US                              
Ign http://us.archive.ubuntu.com/ubuntu/ lucid/restricted Translation-en_US                        
Ign http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu/ lucid/main Translation-en_US                  
Hit http://ppa.launchpad.net lucid Release                                                         
Get:2 http://dl.google.com stable Release [2,544B]                                                                                             
Ign http://us.archive.ubuntu.com/ubuntu/ lucid/universe Translation-en_US                                                  
Ign http://us.archive.ubuntu.com/ubuntu/ lucid/multiverse Translation-en_US                        
Hit http://us.archive.ubuntu.com lucid-updates Release.gpg                                         
Ign http://us.archive.ubuntu.com/ubuntu/ lucid-updates/main Translation-en_US                      
Ign http://us.archive.ubuntu.com/ubuntu/ lucid-updates/restricted Translation-en_US                
Ign http://us.archive.ubuntu.com/ubuntu/ lucid-updates/universe Translation-en_US                                        
Ign http://us.archive.ubuntu.com/ubuntu/ lucid-updates/multiverse Translation-en_US                                      
Hit http://ppa.launchpad.net lucid Release                                                         
Hit http://us.archive.ubuntu.com lucid Release                                                                                                 
Get:3 http://dl.google.com stable/main Packages [1,058B]                                                                                       
Hit http://ppa.launchpad.net lucid/main Packages                                                                                   
Hit http://us.archive.ubuntu.com lucid-updates Release                                             
Hit http://ppa.launchpad.net lucid/main Packages                                                   
Hit http://us.archive.ubuntu.com lucid/main Packages                                               
Hit http://us.archive.ubuntu.com lucid/restricted Packages                   
Hit http://us.archive.ubuntu.com lucid/main Sources    
Hit http://us.archive.ubuntu.com lucid/restricted Sources                    
Hit http://us.archive.ubuntu.com lucid/universe Packages                     
Hit http://us.archive.ubuntu.com lucid/universe Sources
Hit http://us.archive.ubuntu.com lucid/multiverse Packages
Hit http://us.archive.ubuntu.com lucid/multiverse Sources                    
Hit http://us.archive.ubuntu.com lucid-updates/main Packages                 
Hit http://us.archive.ubuntu.com lucid-updates/restricted Packages           
Hit http://us.archive.ubuntu.com lucid-updates/main Sources                  
Hit http://us.archive.ubuntu.com lucid-updates/restricted Sources            
Hit http://us.archive.ubuntu.com lucid-updates/universe Packages             
Hit http://us.archive.ubuntu.com lucid-updates/universe Sources              
Hit http://us.archive.ubuntu.com lucid-updates/multiverse Packages           
Hit http://us.archive.ubuntu.com lucid-updates/multiverse Sources            
Hit http://security.ubuntu.com lucid-security Release.gpg                    
Ign http://security.ubuntu.com/ubuntu/ lucid-security/main Translation-en_US
Ign http://security.ubuntu.com/ubuntu/ lucid-security/restricted Translation-en_US
Ign http://security.ubuntu.com/ubuntu/ lucid-security/universe Translation-en_US
Ign http://security.ubuntu.com/ubuntu/ lucid-security/multiverse Translation-en_US
Hit http://security.ubuntu.com lucid-security Release
Hit http://security.ubuntu.com lucid-security/main Packages
Hit http://security.ubuntu.com lucid-security/restricted Packages
Hit http://security.ubuntu.com lucid-security/main Sources
Hit http://security.ubuntu.com lucid-security/restricted Sources
Hit http://security.ubuntu.com lucid-security/universe Packages
Hit http://security.ubuntu.com lucid-security/universe Sources
Hit http://security.ubuntu.com lucid-security/multiverse Packages
Hit http://security.ubuntu.com lucid-security/multiverse Sources
Fetched 3,791B in 4s (913B/s)
Reading package lists... Done
```

---

### Post by pqwoerituytrueiwoq on 2010-08-26
and compiling it does not work
```
me@linux-laptop:~/Desktop/comm-1.9.2$ ./configure --enable-application=mail --enable-static --enable-calendar --enable-official-branding
loading cache ./config.cache
checking host system type... x86_64-unknown-linux-gnu
checking target system type... x86_64-unknown-linux-gnu
checking build system type... x86_64-unknown-linux-gnu
checking for perl5... (cached) /usr/bin/perl
checking for gawk... (cached) gawk
checking for gcc... (cached) gcc
checking whether the C compiler (gcc  ) works... yes
checking whether the C compiler (gcc  ) is a cross-compiler... no
checking whether we are using GNU C... (cached) yes
checking whether gcc accepts -g... (cached) yes
checking for c++... (cached) c++
checking whether the C++ compiler (c++  ) works... yes
checking whether the C++ compiler (c++  ) is a cross-compiler... no
checking whether we are using GNU C++... (cached) yes
checking whether c++ accepts -g... (cached) yes
checking for ranlib... (cached) ranlib
checking for as... (cached) /usr/bin/as
checking for ar... (cached) ar
checking for ld... (cached) ld
checking for strip... (cached) strip
checking for windres... no
checking whether gcc and cc understand -c and -o together... (cached) yes
checking how to run the C preprocessor... (cached) gcc -E
checking how to run the C++ preprocessor... (cached) c++ -E
checking for a BSD compatible install... (cached) /usr/bin/install -c
checking whether ln -s works... (cached) yes
checking for minimum required perl version >= 5.006... 5.010001
checking for full perl installation... yes
checking for python2.6... (cached) /usr/bin/python2.6
checking for doxygen... (cached) :
checking for whoami... (cached) /usr/bin/whoami
checking for autoconf... (cached) /usr/bin/autoconf
checking for unzip... (cached) /usr/bin/unzip
checking for zip... (cached) /usr/bin/zip
checking for makedepend... no
checking for xargs... (cached) /usr/bin/xargs
checking for X... (cached) libraries , headers 
checking for dnet_ntoa in -ldnet... (cached) no
checking for dnet_ntoa in -ldnet_stub... (cached) no
checking for gethostbyname... (cached) yes
checking for connect... (cached) yes
checking for remove... (cached) yes
checking for shmat... (cached) yes
checking for IceConnectionNumber in -lICE... (cached) yes
checking whether the compiler supports -Wno-invalid-offsetof... yes
checking whether the compiler supports -Wno-variadic-macros... yes
checking whether the compiler supports -Werror=return-type... yes
checking whether ld has archive extraction flags... (cached) yes
checking that static assertion macros used in autoconf tests work... (cached) yes
checking for 64-bit OS... yes
checking for ANSI C header files... (cached) yes
checking for working const... (cached) yes
checking for mode_t... (cached) yes
checking for off_t... (cached) yes
checking for pid_t... (cached) yes
checking for size_t... (cached) yes
checking for st_blksize in struct stat... (cached) yes
checking for siginfo_t... (cached) yes
checking for int16_t... (cached) yes
checking for int32_t... (cached) yes
checking for int64_t... (cached) yes
checking for int64... (cached) no
checking for uint... (cached) yes
checking for uint_t... (cached) no
checking for uint16_t... (cached) no
checking for uname.domainname... (cached) yes
checking for uname.__domainname... (cached) no
checking for usable char16_t (2 bytes, unsigned)... (cached) no
checking for usable wchar_t (2 bytes, unsigned)... (cached) no
checking for compiler -fshort-wchar option... (cached) yes
checking for visibility(hidden) attribute... (cached) yes
checking for visibility(default) attribute... (cached) yes
checking for visibility pragma support... (cached) yes
checking For gcc visibility bug with class-level attributes (GCC bug 26905)... (cached) no
checking For x86_64 gcc visibility bug with builtins (GCC bug 20297)... (cached) no
checking for dirent.h that defines DIR... (cached) yes
checking for opendir in -ldir... (cached) no
checking for sys/byteorder.h... (cached) no
checking for compat.h... (cached) no
checking for getopt.h... (cached) yes
checking for sys/bitypes.h... (cached) yes
checking for memory.h... (cached) yes
checking for unistd.h... (cached) yes
checking for gnu/libc-version.h... (cached) yes
checking for nl_types.h... (cached) yes
checking for malloc.h... (cached) yes
checking for X11/XKBlib.h... (cached) yes
checking for sys/statvfs.h... (cached) yes
checking for sys/statfs.h... (cached) yes
checking for sys/vfs.h... (cached) yes
checking for sys/mount.h... (cached) yes
checking for mmintrin.h... (cached) yes
checking for new... (cached) yes
checking for sys/cdefs.h... (cached) yes
checking for gethostbyname_r in -lc_r... (cached) no
checking for atan in -lm... (cached) yes
checking for dlopen in -ldl... (cached) yes
checking for dlfcn.h... (cached) yes
checking for dladdr... (cached) yes
checking for socket in -lsocket... (cached) no
checking for XDrawLines in -lX11... (cached) yes
checking for XextAddDisplay in -lXext... (cached) yes
checking for XtFree in -lXt... (cached) yes
checking for pthread_create in -lpthreads... no
checking for pthread_create in -lpthread... yes
checking whether gcc accepts -pthread... yes
checking whether mmap() sees write()s... yes
checking whether gcc needs -traditional... (cached) no
checking for 8-bit clean memcmp... (cached) yes
checking for random... (cached) yes
checking for strerror... (cached) yes
checking for lchown... (cached) yes
checking for fchmod... (cached) yes
checking for snprintf... (cached) yes
checking for statvfs... (cached) yes
checking for memmove... (cached) yes
checking for rint... (cached) yes
checking for stat64... (cached) yes
checking for lstat64... (cached) yes
checking for truncate64... (cached) yes
checking for statvfs64... (cached) yes
checking for flockfile... (cached) yes
checking for getpagesize... (cached) yes
checking for localtime_r... (cached) yes
checking for strtok_r... (cached) yes
checking for wcrtomb... (cached) yes
checking for mbrtowc... (cached) yes
checking for res_ninit()... (cached) yes
checking for gnu_get_libc_version()... (cached) yes
checking for iconv in -lc... (cached) yes
checking for iconv()... (cached) yes
checking for iconv() with const input... (cached) no
checking for nl_langinfo and CODESET... (cached) yes
checking for an implementation of va_copy()... (cached) yes
checking for an implementation of __va_copy()... (cached) yes
checking whether va_lists can be copied by value... (cached) no
checking for C++ exceptions flag... (cached) -fno-exceptions
checking for gcc 3.0 ABI... (cached) yes
checking for C++ "explicit" keyword... (cached) yes
checking for C++ "typename" keyword... (cached) yes
checking for modern C++ template specialization syntax support... (cached) yes
checking whether partial template specialization works... (cached) yes
checking whether operators must be re-defined for templates derived from templates... (cached) no
checking whether we need to cast a derived template to pass as its base class... (cached) no
checking whether the compiler can resolve const ambiguities for templates... (cached) yes
checking whether the C++ "using" keyword can change access... (cached) yes
checking whether the C++ "using" keyword resolves ambiguity... (cached) yes
checking for "std::" namespace... (cached) yes
checking whether standard template operator!=() is ambiguous... (cached) unambiguous
checking for C++ reinterpret_cast... (cached) yes
checking for C++ dynamic_cast to void*... (cached) yes
checking whether C++ requires implementation of unused virtual methods... (cached) yes
checking for trouble comparing to zero near std::operator!=()... (cached) no
checking for __thread keyword for TLS variables... (cached) yes
checking for malloc.h... (cached) yes
checking for strndup... (cached) yes
checking for posix_memalign... (cached) yes
checking for memalign... (cached) yes
checking for valloc... (cached) yes
checking for __attribute__((always_inline))... (cached) yes
checking for __attribute__((malloc))... (cached) yes
checking for __attribute__((warn_unused_result))... (cached) yes
checking for __attribute__((noreturn))... (cached) yes
checking for LC_MESSAGES... (cached) yes
checking if app-specific confvars.sh exists... ./mail/confvars.sh
checking for pkg-config... (cached) /usr/bin/pkg-config
checking for gtk+-2.0 >= 2.10.0 gtk+-unix-print-2.0 glib-2.0 gobject-2.0 gdk-x11-2.0... yes
checking MOZ_GTK2_CFLAGS... -pthread -D_REENTRANT -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/gio-unix-2.0/ -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/pixman-1 -I/usr/include/freetype2 -I/usr/include/directfb -I/usr/include/libpng12 -I/usr/include/gtk-unix-print-2.0  
checking MOZ_GTK2_LIBS... -pthread -lgtk-x11-2.0 -latk-1.0 -lgio-2.0 -lpangoft2-1.0 -lfreetype -lfontconfig -lgdk-x11-2.0 -lgdk_pixbuf-2.0 -lm -lpangocairo-1.0 -lpango-1.0 -lcairo -lgobject-2.0 -lgmodule-2.0 -lgthread-2.0 -lrt -lglib-2.0  
checking for pango >= 1.14.0 pangoft2 >= 1.14.0... yes
checking MOZ_PANGO_CFLAGS... -pthread -I/usr/include/pango-1.0 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/freetype2  
checking MOZ_PANGO_LIBS... -pthread -lpangoft2-1.0 -lpango-1.0 -lfreetype -lfontconfig -lgobject-2.0 -lgmodule-2.0 -lgthread-2.0 -lrt -lglib-2.0  
checking for gnome-vfs-2.0 >= 2.0 gnome-vfs-module-2.0 >= 2.0... yes
checking MOZ_GNOMEVFS_CFLAGS... -pthread -DORBIT2=1 -I/usr/include/gnome-vfs-2.0 -I/usr/lib/gnome-vfs-2.0/include -I/usr/include/gconf/2 -I/usr/include/orbit-2.0 -I/usr/include/dbus-1.0 -I/usr/lib/dbus-1.0/include -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/gnome-vfs-module-2.0  
checking MOZ_GNOMEVFS_LIBS... -pthread -lgnomevfs-2 -lgconf-2 -lgmodule-2.0 -lgobject-2.0 -lgthread-2.0 -lrt -lglib-2.0  
checking for gconf-2.0 >= 1.2.1... yes
checking MOZ_GCONF_CFLAGS... -DORBIT2=1 -pthread -I/usr/include/gconf/2 -I/usr/include/orbit-2.0 -I/usr/include/dbus-1.0 -I/usr/lib/dbus-1.0/include -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include  
checking MOZ_GCONF_LIBS... -lgconf-2 -lglib-2.0  
checking for dbus-glib-1 >= 0.60... yes
checking MOZ_DBUS_GLIB_CFLAGS... -pthread -I/usr/include/dbus-1.0 -I/usr/lib/dbus-1.0/include -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include  
checking MOZ_DBUS_GLIB_LIBS... -pthread -L/lib -ldbus-glib-1 -ldbus-1 -lpthread -lgobject-2.0 -lgthread-2.0 -lrt -lglib-2.0  
checking for alsa... yes
checking MOZ_ALSA_CFLAGS... -I/usr/include/alsa  
checking MOZ_ALSA_LIBS... -lasound  
checking for tar archiver... checking for gnutar... (cached) tar
tar
checking for wget... checking for wget... (cached) wget
wget
checking for valid optimization flags... yes
checking size of int *... (cached) 8
checking for __cxa_demangle... (cached) yes
checking for unwind.h... (cached) yes
checking for _Unwind_Backtrace... (cached) yes
checking for gcc -pipe support... yes
checking whether compiler supports -Wno-long-long... yes
checking whether C compiler supports -fprofile-generate... yes
checking whether C++ compiler has -pedantic long long bug... no
checking for correct temporary object destruction order... yes
checking for correct overload resolution with const and templates... no
checking for glib-2.0 >= 1.3.7 gobject-2.0... yes
checking GLIB_CFLAGS... -pthread -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include  
checking GLIB_LIBS... -pthread -lgobject-2.0 -lgthread-2.0 -lrt -lglib-2.0  
checking for stdint.h... (cached) yes
checking for inttypes.h... (cached) yes
checking for sys/int_types.h... (cached) no
creating ./config.status
creating config/autoconf.mk
config/autoconf.mk is unchanged
configuring in mozilla
running /bin/sh ./configure  --enable-application=mail --enable-static --enable-calendar --enable-official-branding --enable-application=../mail --disable-official-branding --with-branding=../other-licenses/branding/thunderbird --cache-file=.././config.cache --srcdir=.
loading cache .././config.cache
checking host system type... x86_64-unknown-linux-gnu
checking target system type... x86_64-unknown-linux-gnu
checking build system type... x86_64-unknown-linux-gnu
checking for gawk... (cached) gawk
checking for perl5... (cached) /usr/bin/perl
checking for gcc... (cached) gcc
checking whether the C compiler (gcc  ) works... yes
checking whether the C compiler (gcc  ) is a cross-compiler... no
checking whether we are using GNU C... (cached) yes
checking whether gcc accepts -g... (cached) yes
checking for c++... (cached) c++
checking whether the C++ compiler (c++  ) works... yes
checking whether the C++ compiler (c++  ) is a cross-compiler... no
checking whether we are using GNU C++... (cached) yes
checking whether c++ accepts -g... (cached) yes
checking for ranlib... (cached) ranlib
checking for as... (cached) /usr/bin/as
checking for ar... (cached) ar
checking for ld... (cached) ld
checking for strip... (cached) strip
checking for windres... no
checking whether gcc and cc understand -c and -o together... (cached) yes
checking how to run the C preprocessor... (cached) gcc -E
checking how to run the C++ preprocessor... (cached) c++ -E
checking for a BSD compatible install... (cached) /usr/bin/install -c
checking whether ln -s works... (cached) yes
checking for minimum required perl version >= 5.006... 5.010001
checking for full perl installation... yes
checking for python2.5... (cached) /usr/bin/python2.6
checking for doxygen... (cached) :
checking for whoami... (cached) /usr/bin/whoami
checking for autoconf... (cached) /usr/bin/autoconf
checking for unzip... (cached) /usr/bin/unzip
checking for zip... (cached) /usr/bin/zip
checking for makedepend... no
checking for xargs... (cached) /usr/bin/xargs
checking for gmake... no
checking for make... /usr/bin/make
checking for X... (cached) libraries , headers 
checking for dnet_ntoa in -ldnet... (cached) no
checking for dnet_ntoa in -ldnet_stub... (cached) no
checking for gethostbyname... (cached) yes
checking for connect... (cached) yes
checking for remove... (cached) yes
checking for shmat... (cached) yes
checking for IceConnectionNumber in -lICE... (cached) yes
checking whether the compiler supports -Wno-invalid-offsetof... yes
checking whether ld has archive extraction flags... (cached) yes
checking that static assertion macros used in autoconf tests work... (cached) yes
checking for 64-bit OS... yes
checking for minimum required Python version >= 2.4... yes
checking for ANSI C header files... (cached) yes
checking for working const... (cached) yes
checking for mode_t... (cached) yes
checking for off_t... (cached) yes
checking for pid_t... (cached) yes
checking for size_t... (cached) yes
checking for st_blksize in struct stat... (cached) yes
checking for siginfo_t... (cached) yes
checking for int16_t... (cached) yes
checking for int32_t... (cached) yes
checking for int64_t... (cached) yes
checking for int64... (cached) no
checking for uint... (cached) yes
checking for uint_t... (cached) no
checking for uint16_t... (cached) no
checking for uname.domainname... (cached) yes
checking for uname.__domainname... (cached) no
checking for usable char16_t (2 bytes, unsigned)... (cached) no
checking for usable wchar_t (2 bytes, unsigned)... (cached) no
checking for compiler -fshort-wchar option... (cached) yes
checking for visibility(hidden) attribute... (cached) yes
checking for visibility(default) attribute... (cached) yes
checking for visibility pragma support... (cached) yes
checking For gcc visibility bug with class-level attributes (GCC bug 26905)... (cached) no
checking For x86_64 gcc visibility bug with builtins (GCC bug 20297)... (cached) no
checking for dirent.h that defines DIR... (cached) yes
checking for opendir in -ldir... (cached) no
checking for sys/byteorder.h... (cached) no
checking for compat.h... (cached) no
checking for getopt.h... (cached) yes
checking for sys/bitypes.h... (cached) yes
checking for memory.h... (cached) yes
checking for unistd.h... (cached) yes
checking for gnu/libc-version.h... (cached) yes
checking for nl_types.h... (cached) yes
checking for malloc.h... (cached) yes
checking for X11/XKBlib.h... (cached) yes
checking for io.h... no
checking for sys/statvfs.h... (cached) yes
checking for sys/statfs.h... (cached) yes
checking for sys/vfs.h... (cached) yes
checking for sys/mount.h... (cached) yes
checking for mmintrin.h... (cached) yes
checking for new... (cached) yes
checking for sys/cdefs.h... (cached) yes
checking for gethostbyname_r in -lc_r... (cached) no
checking for atan in -lm... (cached) yes
checking for dlopen in -ldl... (cached) yes
checking for dlfcn.h... (cached) yes
checking for dladdr... (cached) yes
checking for socket in -lsocket... (cached) no
checking for XDrawLines in -lX11... (cached) yes
checking for XextAddDisplay in -lXext... (cached) yes
checking for XtFree in -lXt... (cached) yes
checking for XShmCreateImage in -lXext... yes
checking for X11/extensions/XShm.h... yes
checking for XieFloGeometry in -lXIE... no
checking for X11/extensions/XIElib.h... no
checking for freetype-config... /usr/bin/freetype-config
checking for FreeType - version >= 6.1.0... yes
checking for FT_Bitmap_Size.y_ppem... yes
checking for FT_GlyphSlot_Embolden... yes
checking for FT_Load_Sfnt_Table... yes
checking for FT_Select_Size... yes
checking for ARM SIMD support in compiler... no
checking for ARM NEON support in compiler... no
checking for pthread_create in -lpthreads... no
checking for pthread_create in -lpthread... yes
checking whether gcc accepts -pthread... yes
checking whether mmap() sees write()s... yes
checking whether gcc needs -traditional... (cached) no
checking for 8-bit clean memcmp... (cached) yes
checking for random... (cached) yes
checking for strerror... (cached) yes
checking for lchown... (cached) yes
checking for fchmod... (cached) yes
checking for snprintf... (cached) yes
checking for statvfs... (cached) yes
checking for memmove... (cached) yes
checking for rint... (cached) yes
checking for stat64... (cached) yes
checking for lstat64... (cached) yes
checking for truncate64... (cached) yes
checking for statvfs64... (cached) yes
checking for setbuf... yes
checking for isatty... yes
checking for flockfile... (cached) yes
checking for getpagesize... (cached) yes
checking for localtime_r... (cached) yes
checking for strtok_r... (cached) yes
checking for wcrtomb... (cached) yes
checking for mbrtowc... (cached) yes
checking for res_ninit()... (cached) yes
checking for gnu_get_libc_version()... (cached) yes
checking for iconv in -lc... (cached) yes
checking for iconv()... (cached) yes
checking for iconv() with const input... (cached) no
checking for nl_langinfo and CODESET... (cached) yes
checking for an implementation of va_copy()... (cached) yes
checking for an implementation of __va_copy()... (cached) yes
checking whether va_lists can be copied by value... (cached) no
checking for C++ exceptions flag... (cached) -fno-exceptions
checking for gcc 3.0 ABI... (cached) yes
checking for C++ "explicit" keyword... (cached) yes
checking for C++ "typename" keyword... (cached) yes
checking for modern C++ template specialization syntax support... (cached) yes
checking whether partial template specialization works... (cached) yes
checking whether operators must be re-defined for templates derived from templates... (cached) no
checking whether we need to cast a derived template to pass as its base class... (cached) no
checking whether the compiler can resolve const ambiguities for templates... (cached) yes
checking whether the C++ "using" keyword can change access... (cached) yes
checking whether the C++ "using" keyword resolves ambiguity... (cached) yes
checking for "std::" namespace... (cached) yes
checking whether standard template operator!=() is ambiguous... (cached) unambiguous
checking for C++ reinterpret_cast... (cached) yes
checking for C++ dynamic_cast to void*... (cached) yes
checking whether C++ requires implementation of unused virtual methods... (cached) yes
checking for trouble comparing to zero near std::operator!=()... (cached) no
checking for __thread keyword for TLS variables... (cached) yes
checking for LC_MESSAGES... (cached) yes
checking if app-specific confvars.sh exists... ./../mail/confvars.sh
checking for pkg-config... (cached) /usr/bin/pkg-config
checking for gtk+-2.0 >= 2.10.0 gtk+-unix-print-2.0 glib-2.0 gobject-2.0 gdk-x11-2.0... yes
checking MOZ_GTK2_CFLAGS... -pthread -D_REENTRANT -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/gio-unix-2.0/ -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/pixman-1 -I/usr/include/freetype2 -I/usr/include/directfb -I/usr/include/libpng12 -I/usr/include/gtk-unix-print-2.0  
checking MOZ_GTK2_LIBS... -pthread -lgtk-x11-2.0 -latk-1.0 -lgio-2.0 -lpangoft2-1.0 -lfreetype -lfontconfig -lgdk-x11-2.0 -lgdk_pixbuf-2.0 -lm -lpangocairo-1.0 -lpango-1.0 -lcairo -lgobject-2.0 -lgmodule-2.0 -lgthread-2.0 -lrt -lglib-2.0  
checking for pango >= 1.14.0... yes
checking _PANGOCHK_CFLAGS... -pthread -I/usr/include/pango-1.0 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include  
checking _PANGOCHK_LIBS... -pthread -lpango-1.0 -lgobject-2.0 -lgmodule-2.0 -lgthread-2.0 -lrt -lglib-2.0  
checking for pango >= 1.14.0 pangoft2 >= 1.14.0... yes
checking MOZ_PANGO_CFLAGS... -pthread -I/usr/include/pango-1.0 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/freetype2  
checking MOZ_PANGO_LIBS... -pthread -lpangoft2-1.0 -lpango-1.0 -lfreetype -lfontconfig -lgobject-2.0 -lgmodule-2.0 -lgthread-2.0 -lrt -lglib-2.0  
checking for gnome-vfs-2.0 >= 2.0 gnome-vfs-module-2.0 >= 2.0... yes
checking MOZ_GNOMEVFS_CFLAGS... -pthread -DORBIT2=1 -I/usr/include/gnome-vfs-2.0 -I/usr/lib/gnome-vfs-2.0/include -I/usr/include/gconf/2 -I/usr/include/orbit-2.0 -I/usr/include/dbus-1.0 -I/usr/lib/dbus-1.0/include -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/gnome-vfs-module-2.0  
checking MOZ_GNOMEVFS_LIBS... -pthread -lgnomevfs-2 -lgconf-2 -lgmodule-2.0 -lgobject-2.0 -lgthread-2.0 -lrt -lglib-2.0  
checking for gconf-2.0 >= 1.2.1... yes
checking MOZ_GCONF_CFLAGS... -DORBIT2=1 -pthread -I/usr/include/gconf/2 -I/usr/include/orbit-2.0 -I/usr/include/dbus-1.0 -I/usr/lib/dbus-1.0/include -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include  
checking MOZ_GCONF_LIBS... -lgconf-2 -lglib-2.0  
checking for libgnomeui-2.0 >= 2.2.0... yes
checking MOZ_GNOMEUI_CFLAGS... -DORBIT2=1 -pthread -D_REENTRANT -I/usr/include/libgnomeui-2.0 -I/usr/include/libart-2.0 -I/usr/include/gconf/2 -I/usr/include/gnome-keyring-1 -I/usr/include/libgnome-2.0 -I/usr/include/libbonoboui-2.0 -I/usr/include/libgnomecanvas-2.0 -I/usr/include/gtk-2.0 -I/usr/include/gnome-vfs-2.0 -I/usr/lib/gnome-vfs-2.0/include -I/usr/include/orbit-2.0 -I/usr/include/dbus-1.0 -I/usr/lib/dbus-1.0/include -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/libbonobo-2.0 -I/usr/include/bonobo-activation-2.0 -I/usr/include/libxml2 -I/usr/include/pango-1.0 -I/usr/include/gail-1.0 -I/usr/include/freetype2 -I/usr/include/atk-1.0 -I/usr/lib/gtk-2.0/include -I/usr/include/cairo -I/usr/include/gio-unix-2.0/ -I/usr/include/pixman-1 -I/usr/include/directfb -I/usr/include/libpng12  
checking MOZ_GNOMEUI_LIBS... -pthread -lgnomeui-2 -lSM -lICE -lbonoboui-2 -lgnomevfs-2 -lgnomecanvas-2 -lgnome-2 -lpopt -lbonobo-2 -lbonobo-activation -lORBit-2 -lart_lgpl_2 -lgtk-x11-2.0 -lgdk-x11-2.0 -latk-1.0 -lgio-2.0 -lpangoft2-1.0 -lgdk_pixbuf-2.0 -lm -lpangocairo-1.0 -lcairo -lpango-1.0 -lfreetype -lfontconfig -lgconf-2 -lgmodule-2.0 -lgobject-2.0 -lgthread-2.0 -lrt -lglib-2.0  
checking for dbus-glib-1 >= 0.60... yes
checking MOZ_DBUS_GLIB_CFLAGS... -pthread -I/usr/include/dbus-1.0 -I/usr/lib/dbus-1.0/include -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include  
checking MOZ_DBUS_GLIB_LIBS... -pthread -L/lib -ldbus-glib-1 -ldbus-1 -lpthread -lgobject-2.0 -lgthread-2.0 -lrt -lglib-2.0  
checking for libnotify >= 0.4... Package libnotify was not found in the pkg-config search path. Perhaps you should add the directory containing `libnotify.pc' to the PKG_CONFIG_PATH environment variable No package 'libnotify' found
configure: error: Library requirements (libnotify >= 0.4) not met; consider adjusting the PKG_CONFIG_PATH environment variable if your libraries are in a nonstandard prefix so pkg-config can find them.
configure: error: ./configure failed for mozilla

```

---

### Post by scouser73 on 2010-08-26
> **pqwoerituytrueiwoq said:**
> Using Ubuntu 10.04 (64 bit)
When should I receive an update for Thunderbird 3.1
I am growing impatient
I really want some features that are in it i had in Thunderbird 2

Download the **.tar.bz2** file from

[[COLOR="Red"]**Mozilla Thunderbird 3.1.2**[/COLOR]]("http://www.mozillamessaging.com/en-GB/thunderbird/")


**1** - Extract the **.tar.bz2** file

**2** - Enter **gksudo nautilus** in terminal

**3** - Go to the folder **/opt**

**4** - Copy & paste the Thunderbird file that you extracted to **/opt**

**5 -** Enter these commands into **Terminal** > **sudo -i**

*Enter your password if asked.*

> **cd /opt**
> **chown -R username filename**

[COLOR="Red"]**Obviously the username refers to you, and the filename to the file**[/COLOR]

**6** - Go to **System > Preferences > Main Menu**

**7** - In Main Menu, click on **New Item**

**8** - In the **Name** field enter **Mozilla Thunderbird Mail/News**

**9** - In the **Command** field enter **/opt/thunderbird/thunderbird**

**10** - In the **Comment** field enter **Mozilla Thunderbird Mail/News**

[[IMG]http://img121.imageshack.us/img121/7329/screenshot2c.png[/IMG]](http://img121.imageshack.us/img121/7329/screenshot2c.png/)

---

### Post by pqwoerituytrueiwoq on 2010-08-26
That is the 32bit version need the **64bit** version

---

### Post by pqwoerituytrueiwoq on 2010-08-27
Found a place to get it :)
```
sudo add-apt-repository ppa:ricotz/ppa && sudo apt-get update
```
then you can get it from the update manager
source:
[http://www.webupd8.org/2010/07/thunderbird-31-ubuntu-ppa-repository.html](http://www.webupd8.org/2010/07/thunderbird-31-ubuntu-ppa-repository.html)

---

