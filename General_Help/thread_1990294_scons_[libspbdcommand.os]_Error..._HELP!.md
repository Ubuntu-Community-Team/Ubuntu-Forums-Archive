---
title: "scons [libs/pbd/command.os] Error... HELP!"
date: 2012-05-29
forum: General Help
---

### Post by poodoopealeoap on 2012-05-29
I'm trying to compile Ardour from source so I can have VST support. I just went through the trouble of reinstalling Ubuntu so I could have the x32 infrastructure so this would be possible. I followed the steps for everything at this page --> [http://noisyheron.wordpress.com/2009/04/05/running-vst-plugins-on-ubuntu-linux-by-building-ardour-with-vst-support/](http://noisyheron.wordpress.com/2009/04/05/running-vst-plugins-on-ubuntu-linux-by-building-ardour-with-vst-support/) , but whenever I try to compile with scons, I get that command.os error 1. I've looked all over and I can't find anything else out there that can help me out... for the record too, on that page that I just gave the link for, I got everything to install except for liblo0ldbl. I can't seem to find it anywhere. I'm not sure if that would be the problem or anything like that. Also, I made sure to sudo apt-get update/upgrade to make sure I had the most up to date libraries and everything.

Here's the code that it spits out when I try to compile with scons... 
```
pwnage@pwnage:~/Downloads/ardour-2.8.12$ sudo scons VST=1
scons: Reading SConscript files ...
Checking for pkg-config version >= 0.8.0... (cached) yes
Checking for lrdf... (cached) yes
Checking for libgnomecanvas-2.0... (cached) yes
Checking for gtk+-2.0... (cached) yes
Checking for jack... (cached) yes
Checking for aubio... (cached) yes
Checking for sndfile... (cached) yes
Checking for samplerate... (cached) yes
Checking for gthread-2.0... (cached) yes
Checking for libxml-2.0... (cached) yes
Checking for glib-2.0... (cached) yes
Checking for fftw3f...(cached) yes
Checking for fftw3...(cached) yes
Checking for aubio...(cached) yes
Checking for raptor2...(cached) no
Checking for raptor...(cached) yes
Checking for glib-2.0... (cached) yes
Checking for C header file fftw3.h... (cached) yes
Checking for C header file curl/curl.h... (cached) yes
LV2 support is not enabled.  Build with 'scons LV2=1' to enable.
WIIMOTE not enabled. Build with 'scons WIIMOTE=1' to enable support.
Congratulations, you have a functioning C++ compiler.
system triple: i686-pc-linux-gnu
Checking for C header file fftw3.h... (cached) yes
Checking for usb_interrupt_write() in C library usb... (cached) no
Checking for C header file linux/input.h... (cached) yes
Checking for C++ header file boost/shared_ptr.hpp... (cached) yes
Checking for lo_server_new() in C library lo... (cached) yes
Checking for dmalloc_shutdown() in C library dmallocth... (cached) no
Checking for C header file alsa/asoundlib.h... (cached) yes
Disabled building Tranzport code because libusb could not be found
Checking for internationalization support ...
Found xgettext
Found msgmerge
Checking for C header file libintl.h... (cached) yes
International version will be built.
Checking for C header file /System/Library/Frameworks/CoreAudio.framework/Versions/A/Headers/CoreAudio.h... (cached) no
Checking for C function posix_memalign()... (cached) yes
Checking for C function gtk_widget_set_tooltip_text()... (cached) yes

scons: warning: Ignoring missing SConscript 'manual/SConscript'
File "/home/pwnage/Downloads/ardour-2.8.12/SConstruct", line 1442, in <module>
Checking for C function getmntent()... (cached) yes
Checking for C header file execinfo.h... (cached) yes
Checking for jack_client_open()...(cached) yes
Checking for jack_port_type_get_buffer_size()...(cached) yes
Checking for jack_on_info_shutdown()...(cached) yes
Checking for jack_recompute_total_latencies()...(cached) yes
Checking for JackVideoFrameOffset in jack_position_bits_t enum...(cached) yes
Checking for jack_port_ensure_monitor_input()...(cached) yes
Checking for C header file wordexp.h... (cached) yes
Checking for C header file sys/vfs.h... (cached) yes
Checking for C header file /System/Library/Frameworks/CoreMIDI.framework/Headers/CoreMIDI.h... (cached) no
Checking for C header file /System/Library/Frameworks/AudioToolbox.framework/Headers/ExtendedAudioFile.h... (cached) no
Checking for C header file /System/Library/Frameworks/CoreAudio.framework/Headers/CoreAudio.h... (cached) no
Checking for C header file /System/Library/Frameworks/AudioUnit.framework/Headers/AudioUnit.h... (cached) no
FPU OPTIMIZATION WITH TARGET 
i686
Checking for jack_set_thread_creator()...(cached) yes

scons: warning: Ignoring missing SConscript 'tools/sanity_check/SConscript'
File "/home/pwnage/Downloads/ardour-2.8.12/SConstruct", line 1446, in <module>
scons: done reading SConscript files.
scons: Building targets ...
scons: `ardour_system.rc' is up to date.
scons: `libs/sigc++2/sigc++config.h' is up to date.
scons: `libs/sigc++2/libsigc++2.so' is up to date.
scons: `libs/glibmm2/glibmmconfig.h' is up to date.
g++ -o libs/pbd/command.os -c -Woverloaded-virtual -DGTK_NEW_TOOLTIP_API -DPACKAGE=\"libpbd\" -D_REENTRANT -D_LARGEFILE_SOURCE -D_LARGEFILE64_SOURCE -DLIBSIGC_DISABLE_DEPRECATED -DHAVE_EXECINFO -O3 -fomit-frame-pointer -ffast-math -fstrength-reduce -pipe -DARCH_X86 -mmmx -march=i686 -msse -mfpmath=sse -DUSE_XMMINTRIN -m32 -DBUILD_SSE_OPTIMIZATIONS -Wall -DHAVE_LIBLO -DPROGRAM_NAME=\"Ardour\" -D_REENTRANT -D_LARGEFILE_SOURCE -D_LARGEFILE64_SOURCE -D_FILE_OFFSET_BITS=64 -D__STDC_FORMAT_MACROS -Ilibs -DENABLE_NLS -DHAVE_GETMNTENT -pthread -DWINE_THREAD_SUPPORT -fPIC -I/usr/include/glib-2.0 -Ilibs/sigc++2 -Ilibs/glibmm2 -Ilibs/pbd -I/usr/include/libxml2 -I/usr/lib/i386-linux-gnu/glib-2.0/include -Ilibs/fst libs/pbd/command.cc
In file included from libs/pbd/pbd/id.h:26:0,
                 from libs/pbd/pbd/stateful.h:24,
                 from libs/pbd/pbd/statefuldestructible.h:23,
                 from libs/pbd/pbd/command.h:23,
                 from libs/pbd/command.cc:20:
libs/glibmm2/glibmm/thread.h:149:25: error: variable or field ‘thread_init’ declared void
libs/glibmm2/glibmm/thread.h:149:25: error: ‘GThreadFunctions’ was not declared in this scope
libs/glibmm2/glibmm/thread.h:149:43: error: ‘vtable’ was not declared in this scope
libs/glibmm2/glibmm/thread.h:310:11: error: field ‘gobject_’ has incomplete type
libs/glibmm2/glibmm/thread.h: In member function ‘GThread* Glib::Thread::gobj()’:
libs/glibmm2/glibmm/thread.h:306:41: error: ‘gobject_’ was not declared in this scope
libs/glibmm2/glibmm/thread.h: In member function ‘const GThread* Glib::Thread::gobj() const’:
libs/glibmm2/glibmm/thread.h:307:41: error: ‘gobject_’ was not declared in this scope
libs/glibmm2/glibmm/thread.h: At global scope:
libs/glibmm2/glibmm/thread.h:354:3: error: ‘GStaticMutex’ does not name a type
libs/glibmm2/glibmm/thread.h:358:3: error: ‘GStaticMutex’ does not name a type
libs/glibmm2/glibmm/thread.h:470:3: error: ‘GStaticRecMutex’ does not name a type
libs/glibmm2/glibmm/thread.h:474:3: error: ‘GStaticRecMutex’ does not name a type
libs/glibmm2/glibmm/thread.h:539:3: error: ‘GStaticRWLock’ does not name a type
libs/glibmm2/glibmm/thread.h:543:3: error: ‘GStaticRWLock’ does not name a type
libs/glibmm2/glibmm/thread.h:722:3: error: ‘GStaticPrivate’ does not name a type
libs/glibmm2/glibmm/thread.h:726:3: error: ‘GStaticPrivate’ does not name a type
libs/glibmm2/glibmm/thread.h:773:18: error: variable or field ‘thread_init’ declared void
libs/glibmm2/glibmm/thread.h:773:18: error: ‘GThreadFunctions’ was not declared in this scope
libs/glibmm2/glibmm/thread.h:773:36: error: ‘vtable’ was not declared in this scope
libs/glibmm2/glibmm/thread.h: In function ‘bool Glib::thread_supported()’:
libs/glibmm2/glibmm/thread.h:783:30: error: ‘g_thread_supported’ was not declared in this scope
libs/glibmm2/glibmm/thread.h: In member function ‘T* Glib::StaticPrivate<T>::get()’:
libs/glibmm2/glibmm/thread.h:1039:48: error: ‘gobject_’ was not declared in this scope
libs/glibmm2/glibmm/thread.h:1039:56: error: there are no arguments to ‘g_static_private_get’ that depend on a template parameter, so a declaration of ‘g_static_private_get’ must be available [-fpermissive]
libs/glibmm2/glibmm/thread.h:1039:56: note: (if you use ‘-fpermissive’, G++ will accept your code, but allowing the use of an undeclared name is deprecated)
libs/glibmm2/glibmm/thread.h: In member function ‘void Glib::StaticPrivate<T>::set(T*, Glib::StaticPrivate<T>::DestroyNotifyFunc)’:
libs/glibmm2/glibmm/thread.h:1045:25: error: ‘gobject_’ was not declared in this scope
libs/glibmm2/glibmm/thread.h: In constructor ‘Glib::Private<T>::Private(Glib::Private<T>::DestructorFunc)’:
libs/glibmm2/glibmm/thread.h:1061:42: error: there are no arguments to ‘g_private_new’ that depend on a template parameter, so a declaration of ‘g_private_new’ must be available [-fpermissive]
scons: *** [libs/pbd/command.os] Error 1
scons: building terminated because of errors.

```

---

### Post by gunterkoenigsmann on 2013-02-25
The same applies to inkscape and seems to be also happening on developer's versions of debian and arch linux. I wonder if we have found a transitional problem with gnome's header files on the way to the next version.

---

