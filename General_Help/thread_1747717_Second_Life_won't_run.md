---
title: "Second Life won't run"
date: 2011-05-02
forum: General Help
---

### Post by feathre on 2011-05-02
Hi, I was trying to install Second Life on my Ubuntu 11.04 x64 bit.
It won't allow me to run it, here is the message it gives:

```
dustin@lestat:/usr/local/games/SecondLife-i686-2.6.3.227447$ ./secondlife
64-bit Linux detected.
Running from /usr/local/games/SecondLife-i686-2.6.3.227447
 - Installing menu entries in /home/dustin/.local/share/applications
2011-05-03T03:05:45Z INFO: (anonymous namespace)::LogControlFile::loadFile: logging reconfigured from /usr/local/games/SecondLife-i686-2.6.3.227447/app_settings/logcontrol.xml
2011-05-03T03:05:45Z INFO: loadSettingsFromDirectory: Attempting to load settings for the group Global - from location Default
2011-05-03T03:05:45Z INFO: loadSettingsFromDirectory: Loaded settings file /usr/local/games/SecondLife-i686-2.6.3.227447/app_settings/settings.xml
2011-05-03T03:05:45Z INFO: loadSettingsFromDirectory: Attempting to load settings for the group PerAccount - from location Default
2011-05-03T03:05:45Z INFO: loadSettingsFromDirectory: Loaded settings file /usr/local/games/SecondLife-i686-2.6.3.227447/app_settings/settings_per_account.xml
2011-05-03T03:05:45Z INFO: loadSettingsFromDirectory: Attempting to load settings for the group CrashSettings - from location Default
2011-05-03T03:05:45Z INFO: loadSettingsFromDirectory: Loaded settings file /usr/local/games/SecondLife-i686-2.6.3.227447/app_settings/settings_crash_behavior.xml
2011-05-03T03:05:45Z INFO: loadSettingsFromDirectory: Attempting to load settings for the group Warnings - from location Default
2011-05-03T03:05:45Z INFO: loadSettingsFromDirectory: Loaded settings file /usr/local/games/SecondLife-i686-2.6.3.227447/app_settings/ignorable_dialogs.xml
2011-05-03T03:05:45Z INFO: initParseCommandLine: Language en
2011-05-03T03:05:45Z INFO: initParseCommandLine: Location US
2011-05-03T03:05:45Z INFO: initParseCommandLine: Variant UTF-8
2011-05-03T03:05:45Z INFO: loadSettingsFromDirectory: Attempting to load settings for the group Global - from location User
2011-05-03T03:05:45Z WARNING: loadFromFile: Cannot find file /home/dustin/.secondlife/user_settings//home/dustin/.secondlife/user_settings/settings.xml to load.
2011-05-03T03:05:45Z INFO: loadSettingsFromDirectory: Cannot load /home/dustin/.secondlife/user_settings//home/dustin/.secondlife/user_settings/settings.xml - No settings found.
2011-05-03T03:05:45Z INFO: loadSettingsFromDirectory: Attempting to load settings for the group CrashSettings - from location User
2011-05-03T03:05:45Z WARNING: loadFromFile: Cannot find file /home/dustin/.secondlife/user_settings/settings_crash_behavior to load.
2011-05-03T03:05:45Z INFO: loadSettingsFromDirectory: Cannot load /home/dustin/.secondlife/user_settings/settings_crash_behavior - No settings found.
2011-05-03T03:05:45Z INFO: loadSettingsFromDirectory: Attempting to load settings for the group Warnings - from location User
2011-05-03T03:05:45Z WARNING: loadFromFile: Cannot find file /home/dustin/.secondlife/user_settings/ignorable_dialogs.xml to load.
2011-05-03T03:05:45Z INFO: loadSettingsFromDirectory: Cannot load /home/dustin/.secondlife/user_settings/ignorable_dialogs.xml - No settings found.
2011-05-03T03:05:45Z INFO: loadSettingsFromDirectory: Attempting to load settings for the group Global - from location Session
2011-05-03T03:05:45Z INFO: loadSettingsFromDirectory: Loaded settings file /usr/local/games/SecondLife-i686-2.6.3.227447/app_settings/settings_minimal.xml
2011-05-03T03:05:45Z INFO: loadSettingsFromDirectory: Attempting to load settings for the group Global - from location UserSession
2011-05-03T03:05:45Z INFO: parse: LLSDXMLParser::Impl::parse: XML_STATUS_ERROR parsing:
2011-05-03T03:05:45Z WARNING: loadFromFile: Unable to open LLSD control file /home/dustin/.secondlife/user_settings. Trying Legacy Method.
2011-05-03T03:05:45Z WARNING: parseFile: Error while reading file  /home/dustin/.secondlife/user_settings
2011-05-03T03:05:45Z WARNING: parseFile: LLXmlTree parse failed.  Line 1: Error while reading file  /home/dustin/.secondlife/user_settings
2011-05-03T03:05:45Z WARNING: loadFromFileLegacy: Unable to open control file /home/dustin/.secondlife/user_settings
2011-05-03T03:05:45Z INFO: loadSettingsFromDirectory: Cannot load /home/dustin/.secondlife/user_settings - No settings found.
2011-05-03T03:05:45Z INFO: initMarkerFile: Exec marker found: program froze on previous execution
2011-05-03T03:05:45Z INFO: checkForCrash: Last execution froze, requesting to send crash report.
2011-05-03T03:05:45Z INFO: ll_try_gtk_init: Starting GTK Initialization.
2011-05-03T03:05:45Z INFO: ll_try_gtk_init: GTK Initialized.
2011-05-03T03:05:45Z INFO: ll_try_gtk_init: - Compiled against GTK version 2.4.14
2011-05-03T03:05:45Z INFO: ll_try_gtk_init: - Running against GTK version 2.24.4
2011-05-03T03:05:45Z INFO: ll_try_gtk_init: - GTK version is good.
2011-05-03T03:05:45Z INFO: OSMessageBoxSDL: Creating a dialog because we're in windowed mode and GTK is happy.
/usr/lib/gio/modules/libgiobamf.so: wrong ELF class: ELFCLASS64
Failed to load module: /usr/lib/gio/modules/libgiobamf.so
/usr/lib/gio/modules/libgvfsdbus.so: wrong ELF class: ELFCLASS64
Failed to load module: /usr/lib/gio/modules/libgvfsdbus.so

(<unknown>:26855): Gtk-WARNING **: Error loading theme icon 'dialog-question' for stock: Unable to load image-loading module: /usr/lib/gdk-pixbuf-2.0/2.10.0/loaders/libpixbufloader-svg.so: /usr/lib/gdk-pixbuf-2.0/2.10.0/loaders/libpixbufloader-svg.so: wrong ELF class: ELFCLASS64

(<unknown>:26855): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

** (<unknown>:26855): CRITICAL **: murrine_style_draw_render_icon: assertion `base_pixbuf != NULL' failed

(<unknown>:26855): Gtk-CRITICAL **: IA__gtk_style_render_icon: assertion `pixbuf != NULL' failed

(<unknown>:26855): GLib-GObject-CRITICAL **: g_object_ref: assertion `G_IS_OBJECT (object)' failed

(<unknown>:26855): Gtk-WARNING **: Error loading theme icon 'dialog-question' for stock: Unable to load image-loading module: /usr/lib/gdk-pixbuf-2.0/2.10.0/loaders/libpixbufloader-svg.so: /usr/lib/gdk-pixbuf-2.0/2.10.0/loaders/libpixbufloader-svg.so: wrong ELF class: ELFCLASS64

(<unknown>:26855): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

** (<unknown>:26855): CRITICAL **: murrine_style_draw_render_icon: assertion `base_pixbuf != NULL' failed

(<unknown>:26855): Gtk-CRITICAL **: IA__gtk_style_render_icon: assertion `pixbuf != NULL' failed

(<unknown>:26855): GLib-GObject-CRITICAL **: g_object_ref: assertion `G_IS_OBJECT (object)' failed
2011-05-03T03:05:47Z INFO: checkForCrash: Not sending crash report.
2011-05-03T03:05:47Z WARNING: LLUIColorTable::loadFromFilename: Unable to parse color file /home/dustin/.secondlife/skins/minimal/colors.xml
2011-05-03T03:05:47Z WARNING: LLUIColorTable::loadFromFilename: Unable to parse color file /home/dustin/.secondlife/user_settings/colors.xml
2011-05-03T03:05:47Z INFO: initialize: is array
2011-05-03T03:05:47Z INFO: writeSystemInfo: Second Life version 2.6.3
2011-05-03T03:05:47Z INFO: writeSystemInfo: Local time: 2011-05-02T21:05:47 MDT
2011-05-03T03:05:47Z INFO: writeSystemInfo: CPU info:
processor	: 0 
vendor_id	: GenuineIntel 
cpu family	: 6 
model		: 23 
model name	: Intel(R) Core(TM)2 Duo CPU     T6600  @ 2.20GHz 
stepping	: 10 
cpu MHz		: 1200.000 
cache size	: 2048 KB 
physical id	: 0 
siblings	: 2 
core id		: 0 
cpu cores	: 2 
apicid		: 0 
initial apicid	: 0 
fpu		: yes 
fpu_exception	: yes 
cpuid level	: 13 
wp		: yes 
flags		: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx lm constant_tsc arch_perfmon pebs bts rep_good nopl aperfmperf pni dtes64 monitor ds_cpl est tm2 ssse3 cx16 xtpr  
dcm sse4_1 xsave lahf_lm dts 
bogomips	: 4389.78 
clflush size	: 64 
cache_alignment	: 64 
address sizes	: 36 bits physical, 48 bits virtual 
power management: 
 
processor	: 1 
vendor_id	: GenuineIntel 
cpu family	: 6 
model		: 23 
model name	: Intel(R) Core(TM)2 Duo CPU     T6600  @ 2.20GHz 
stepping	: 10 
cpu MHz		: 2200.000 
cache size	: 2048 KB 
physical id	: 0 
siblings	: 2 
core id		: 1 
cpu cores	: 2 
apicid		: 1 
initial apicid	: 1 
fpu		: yes 
fpu_exception	: yes 
cpuid level	: 13 
wp		: yes 
flags		: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx lm constant_tsc arch_perfmon pebs bts rep_good nopl aperfmperf pni dtes64 monitor ds_cpl est tm2 ssse3 cx16 xtpr  
dcm sse4_1 xsave lahf_lm dts 
bogomips	: 4388.98 
clflush size	: 64 
cache_alignment	: 64 
address sizes	: 36 bits physical, 48 bits virtual 
power management: 
 

->mHasSSE:     1
->mHasSSE2:    1
->mHasAltivec: 0
->mCPUMHz:     2200
->mCPUString:  Intel(R) Core(TM)2 Duo CPU     T6600  @ 2.20GHz (2200 MHz)

2011-05-03T03:05:47Z INFO: writeSystemInfo: Memory info:
MemTotal:        4025772 kB MemFree:           35656 kB Buffers:           92620 kB Cached:          2601096 kB SwapCached:          108 kB Active:          1860964 kB Inactive:        1833556 kB Active(anon):     562528 kB Inactive(anon):   465180 kB Active(file):    1298436 kB Inactive(file):  1368376 kB Unevictable:          68 kB Mlocked:              68 kB SwapTotal:       9936892 kB SwapFree:        9935300 kB Dirty:              2376 kB Writeback:             0 kB AnonPages:       1000864 kB Mapped:           177640 kB Shmem:             26904 kB Slab:             118184 kB SReclaimable:      88292 kB SUnreclaim:        29892 kB KernelStack:        3064 kB PageTables:        34164 kB NFS_Unstable:          0 kB Bounce:                0 kB WritebackTmp:          0 kB CommitLimit:    11949776 kB Committed_AS:    2968852 kB VmallocTotal:   34359738367 kB VmallocUsed:      343792 kB VmallocChunk:   34359386620 kB HardwareCorrupted:     0 kB HugePages_Total:       0 HugePages_Free:        0 HugePages_Rsvd:        0 HugePages_Surp:        0 Hugepagesize:       2048 kB DirectMap4k:      233472 kB DirectMap2M:     3928064 kB 
2011-05-03T03:05:47Z INFO: writeSystemInfo: OS: Linux 2.6
2011-05-03T03:05:47Z INFO: writeSystemInfo: OS info: Linux 2.6.38-8-generic #42-Ubuntu SMP Mon Apr 11 03:31:24 UTC 2011 x86_64
2011-05-03T03:05:47Z INFO: writeDebugInfo: Opening debug file /home/dustin/.secondlife/logs/debug_info.log
2011-05-03T03:05:47Z INFO: LLUpdaterServiceImpl::setState: setting state to 1
2011-05-03T03:05:47Z INFO: LLUpdaterServiceImpl::restartTimer: will check for update again in 0 seconds
2011-05-03T03:05:47Z INFO: init: J2C Engine is: KDU v6.4.1
2011-05-03T03:05:47Z INFO: init: libcurl version is: libcurl/7.21.1 OpenSSL/0.9.8q zlib/1.2.5 c-ares/1.7.1
2011-05-03T03:05:47Z WARNING: loadFromFile: Cannot find file /home/dustin/.secondlife/user_settings/settings_crash_behavior.xml to load.
2011-05-03T03:05:48Z INFO: updateVectorize: Vectorization         : DISABLED
2011-05-03T03:05:48Z INFO: updateVectorize: Vector Processor      : COMPILER DEFAULT
2011-05-03T03:05:48Z INFO: updateVectorize: Vectorized Skinning   : ENABLED
2011-05-03T03:05:48Z INFO: updateVectorize: Vectorization         : DISABLED
2011-05-03T03:05:48Z INFO: updateVectorize: Vector Processor      : COMPILER DEFAULT
2011-05-03T03:05:48Z INFO: updateVectorize: Vectorized Skinning   : ENABLED
2011-05-03T03:05:48Z INFO: updateVectorize: Vectorization         : DISABLED
2011-05-03T03:05:48Z INFO: updateVectorize: Vector Processor      : COMPILER DEFAULT
2011-05-03T03:05:48Z INFO: updateVectorize: Vectorized Skinning   : DISABLED
2011-05-03T03:05:48Z INFO: grab_dbus_syms: Found DSO: libdbus-glib-1.so.2
2011-05-03T03:05:48Z INFO: initCache: Headers: 143165 Textures size: 327 MB
2011-05-03T03:05:48Z INFO: purgeAllTextures: Deleting files in directory: /home/dustin/.secondlife/cache/texturecache/0
2011-05-03T03:05:48Z INFO: purgeAllTextures: Deleting files in directory: /home/dustin/.secondlife/cache/texturecache/1
2011-05-03T03:05:48Z INFO: purgeAllTextures: Deleting files in directory: /home/dustin/.secondlife/cache/texturecache/2
2011-05-03T03:05:48Z INFO: purgeAllTextures: Deleting files in directory: /home/dustin/.secondlife/cache/texturecache/3
2011-05-03T03:05:48Z INFO: purgeAllTextures: Deleting files in directory: /home/dustin/.secondlife/cache/texturecache/4
2011-05-03T03:05:48Z INFO: purgeAllTextures: Deleting files in directory: /home/dustin/.secondlife/cache/texturecache/5
2011-05-03T03:05:48Z INFO: purgeAllTextures: Deleting files in directory: /home/dustin/.secondlife/cache/texturecache/6
2011-05-03T03:05:48Z INFO: purgeAllTextures: Deleting files in directory: /home/dustin/.secondlife/cache/texturecache/7
2011-05-03T03:05:48Z INFO: purgeAllTextures: Deleting files in directory: /home/dustin/.secondlife/cache/texturecache/8
2011-05-03T03:05:48Z INFO: purgeAllTextures: Deleting files in directory: /home/dustin/.secondlife/cache/texturecache/9
2011-05-03T03:05:48Z INFO: purgeAllTextures: Deleting files in directory: /home/dustin/.secondlife/cache/texturecache/a
2011-05-03T03:05:48Z INFO: purgeAllTextures: Deleting files in directory: /home/dustin/.secondlife/cache/texturecache/b
2011-05-03T03:05:48Z INFO: purgeAllTextures: Deleting files in directory: /home/dustin/.secondlife/cache/texturecache/c
2011-05-03T03:05:48Z INFO: purgeAllTextures: Deleting files in directory: /home/dustin/.secondlife/cache/texturecache/d
2011-05-03T03:05:48Z INFO: purgeAllTextures: Deleting files in directory: /home/dustin/.secondlife/cache/texturecache/e
2011-05-03T03:05:48Z INFO: purgeAllTextures: Deleting files in directory: /home/dustin/.secondlife/cache/texturecache/f
2011-05-03T03:05:48Z WARNING: ll_apr_warn_status: APR: No such file or directory
2011-05-03T03:05:48Z WARNING: open:  Attempting to open filename: /home/dustin/.secondlife/cache/texturecache/texture.entries
2011-05-03T03:05:48Z INFO: purgeAllTextures: The entire texture cache is cleared.
2011-05-03T03:05:48Z INFO: purgeTextures: TEXTURE CACHE: Purging.
2011-05-03T03:05:48Z INFO: initCache: VFS CACHE SIZE: 102 MB
2011-05-03T03:05:48Z INFO: LLVFS: Attempting to open VFS index file /home/dustin/.secondlife/cache/index.db2.x.153216411
2011-05-03T03:05:48Z INFO: LLVFS: Attempting to open VFS data file /home/dustin/.secondlife/cache/data.db2.x.153216411
2011-05-03T03:05:48Z INFO: presizeDataFile: Pre-sized VFS data file to 106954752 bytes
2011-05-03T03:05:48Z INFO: LLVFS: Using VFS index file /home/dustin/.secondlife/cache/index.db2.x.153216411
2011-05-03T03:05:48Z INFO: LLVFS: Using VFS data file /home/dustin/.secondlife/cache/data.db2.x.153216411
2011-05-03T03:05:48Z INFO: LLVFS: Attempting to open VFS index file /usr/local/games/SecondLife-i686-2.6.3.227447/app_settings/static_index.db2
2011-05-03T03:05:48Z INFO: LLVFS: Attempting to open VFS data file /usr/local/games/SecondLife-i686-2.6.3.227447/app_settings/static_data.db2
2011-05-03T03:05:48Z INFO: LLVFS: Using VFS index file /usr/local/games/SecondLife-i686-2.6.3.227447/app_settings/static_index.db2
2011-05-03T03:05:48Z INFO: LLVFS: Using VFS data file /usr/local/games/SecondLife-i686-2.6.3.227447/app_settings/static_data.db2
2011-05-03T03:05:48Z INFO: initWindow: Initializing window...
2011-05-03T03:05:48Z INFO: LLViewerWindow: NOTE: ALL NOTIFICATIONS THAT OCCUR WILL GET ADDED TO IGNORE LIST FOR LATER RUNS.
2011-05-03T03:05:48Z INFO: createContext: createContext, fullscreen=0 size=1024x738
2011-05-03T03:05:48Z INFO: createContext: Compiled against SDL 1.2.14
2011-05-03T03:05:48Z INFO: createContext:  Running against SDL 1.2.14
2011-05-03T03:05:48Z INFO: createContext: Original aspect ratio was 1366:768=1.77865
2011-05-03T03:05:48Z INFO: createContext: createContext: creating window 1024x738x32
The program '<unknown>' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadWindow (invalid Window parameter)'.
  (Details: serial 33 error_code 3 request_code 138 minor_code 4)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)
*** Bad shutdown. ***

You are running the Second Life Viewer on a x86_64 platform.  The
most common problems when launching the Viewer (particularly
'bin/do-not-directly-run-secondlife-bin: not found' and 'error while
loading shared libraries') may be solved by installing your Linux
distribution's 32-bit compatibility packages.
For example, on Ubuntu and other Debian-based Linuxes you might run:
$ sudo apt-get install ia32-libs ia32-libs-gtk ia32-libs-kde ia32-libs-sdl

*******************************************************
This is a BETA release of the Second Life linux client.
Thank you for testing!
Please see README-linux.txt before reporting problems.

```

---

### Post by 3rdalbum on 2011-05-03
Never tried Second Life, but I notice at the bottom of the error message there's two possibilities:

Have you installed the 32-bit compatibility packages? (sudo apt-get install ia32-libs ia32-libs-gtk ia32-libs-kde ia32-libs-sdl)

There's also a reference to a file called "bin/do-not-directly-run-secondlife-bin" - have you tried actually running this file? It might set environment variables and stuff.

---

### Post by feathre on 2011-05-03
I tried doing that command and got this:
```
dustin@lestat:~$ sudo apt-get install ia32-libs ia32-libs-gtk ia32-libs-kde ia32-libs-sdl
[sudo] password for dustin: 
E: Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
```

---

### Post by mthome on 2011-05-03
The problem you are seeing is due to an ABI incompatibility between x.org and GLX introduced in natty. A number of opengl apps show this problem, including Second Life viewers and Unity3D. Check this thread out: [http://ubuntuforums.org/showthread.php?t=1745841](http://ubuntuforums.org/showthread.php?t=1745841)

---

### Post by alina.bolero on 2011-05-15
Same problem here.  Natty x64 trying to run SecondLife-i686-2.6.3.227447
gives:

```
2011-05-15T21:47:34Z INFO: ll_try_gtk_init: Starting GTK Initialization.
2011-05-15T21:47:34Z INFO: ll_try_gtk_init: GTK Initialized.
2011-05-15T21:47:34Z INFO: ll_try_gtk_init: - Compiled against GTK version 2.4.14
2011-05-15T21:47:34Z INFO: ll_try_gtk_init: - Running against GTK version 2.24.4
2011-05-15T21:47:34Z INFO: ll_try_gtk_init: - GTK version is good.
2011-05-15T21:47:34Z INFO: OSMessageBoxSDL: Creating a dialog because we're in windowed mode and GTK is happy.
/usr/lib/gio/modules/libgiobamf.so: wrong ELF class: ELFCLASS64
Failed to load module: /usr/lib/gio/modules/libgiobamf.so
/usr/lib/gio/modules/libgvfsdbus.so: wrong ELF class: ELFCLASS64
Failed to load module: /usr/lib/gio/modules/libgvfsdbus.so

(<unknown>:1753): Gtk-WARNING **: Error loading theme icon 'dialog-question' for stock: Unable to load image-loading module: /usr/lib/gdk-pixbuf-2.0/2.10.0/loaders/libpixbufloader-svg.so: /usr/lib/gdk-pixbuf-2.0/2.10.0/loaders/libpixbufloader-svg.so: wrong ELF class: ELFCLASS64

(<unknown>:1753): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

** (<unknown>:1753): CRITICAL **: murrine_style_draw_render_icon: assertion `base_pixbuf != NULL' failed

(<unknown>:1753): Gtk-CRITICAL **: IA__gtk_style_render_icon: assertion `pixbuf != NULL' failed

(<unknown>:1753): GLib-GObject-CRITICAL **: g_object_ref: assertion `G_IS_OBJECT (object)' failed

(<unknown>:1753): Gtk-WARNING **: Error loading theme icon 'dialog-question' for stock: Unable to load image-loading module: /usr/lib/gdk-pixbuf-2.0/2.10.0/loaders/libpixbufloader-svg.so: /usr/lib/gdk-pixbuf-2.0/2.10.0/loaders/libpixbufloader-svg.so: wrong ELF class: ELFCLASS64

(<unknown>:1753): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

** (<unknown>:1753): CRITICAL **: murrine_style_draw_render_icon: assertion `base_pixbuf != NULL' failed

(<unknown>:1753): Gtk-CRITICAL **: IA__gtk_style_render_icon: assertion `pixbuf != NULL' failed

(<unknown>:1753): GLib-GObject-CRITICAL **: g_object_ref: assertion `G_IS_OBJECT (object)' failed
```

All of ia32-libs ia32-libs-gtk ia32-libs-kde ia32-libs-sdl are already installed.

The "ABI incompatibility between x.org and GLX introduced in natty" sounds like a good lead for a solution, but the link provided really didn't provide much insight.

Any other leads on this "ABI" issue plaguing X.org, GLX, and apparently GTK when running x32 on x64?

I'm stumped!  :(

---

