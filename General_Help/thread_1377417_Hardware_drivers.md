---
title: "Hardware drivers"
date: 2010-01-10
forum: General Help
---

### Post by Drojoke on 2010-01-10
So i reinstalled xubuntu 9.10 on my PC (This time the i386 one isntead of the AMD64.) And i have some problems with my hardware drivers.
When i look at my hardware drivers it only says i can install some kind of wireless driver from broadcom. 
A game i try to run tells me it couldn't find a sound driver. Error of the game:
edit:**This error is gone now, somehow. I didn't do anything but i am able to run the game now. Im figuring out now if it works properly.**
```
00:00.006: StepMania 3.9
00:00.007: Log starting 2010-01-10 15:07:56
00:00.007:  
00:00.007: Reading 'Data/Defaults.ini' failed: No such file or directory
00:00.007: Reading 'Data/StepMania.ini' failed: No such file or directory
00:00.007: Reading 'Data/Static.ini' failed: No such file or directory
00:00.184: Loading window: gtk
00:00.184: OS: Linux ver 020631
00:00.184: Crash backtrace component: x86 custom backtrace
00:00.185: Crash lookup component: dladdr
00:00.185: Crash demangle component: cxa_demangle
00:00.185: Runtime library: glibc 2.10.1
00:00.185: Threads library: NPTL 2.10.1
00:00.185: TLS is available
00:00.185: AnnouncerManager::AnnouncerManager()
00:00.185: Reading 'Data/GamePrefs.ini' failed: No such file or directory
00:00.185: Reading 'Data/Static.ini' failed: No such file or directory
00:00.186: ThemeManager::SwitchThemeAndLanguage: "default", ""
00:00.229: Initializing driver: ALSA
00:00.237: ALSA: Advanced Linux Sound Architecture Driver Version 1.0.20.
00:00.237: ALSA Driver: 0: HDA Intel [Intel], device 0: STAC92xx Analog [STAC92xx Analog], 0/1 subdevices avail
00:00.238: ALSA error: pcm_hw.c:1327 snd_pcm_hw_open: open /dev/snd/pcmC0D0p failed (Device or resource busy)
00:00.239: Couldn't load driver ALSA: dsnd_pcm_open(hw:0): Device or resource busy
00:00.239: Initializing driver: ALSA-sw
00:00.239: OS: Linux ver 020631
00:00.239: ALSA error: pcm_hw.c:1327 snd_pcm_hw_open: open /dev/snd/pcmC0D0p failed (Device or resource busy)
00:00.239: Mixing 0.000000 ahead in 0 Mix() calls
00:00.240: Couldn't load driver ALSA-sw: dsnd_pcm_open(hw:0): Device or resource busy
00:00.240: Initializing driver: OSS
00:00.240: Mixing 0.000000 ahead in 0 Mix() calls
00:00.240: Couldn't load driver OSS: RageSound_OSS: Couldn't open /dev/dsp: Device or resource busy
00:00.240: 
00:00.240: //////////////////////////////////////////////////////
00:00.240: Exception: Couldn't find a sound driver that works
00:00.240: //////////////////////////////////////////////////////
00:00.240: 
00:00.240: Language: english
00:00.240: Theme: default

```I also tried to install a graphics card driver for my PC (Intel 82915G chipset). But i got this error:
```
make -C /lib/modules/2.6.31-17-generic/build SUBDIRS=/home/joep/Downloads/dripkg/agpgart-2.0 modules
make[1]: Map '/usr/src/linux-headers-2.6.31-17-generic' wordt binnengegaan
  CC [M]  /home/joep/Downloads/dripkg/agpgart-2.0/backend.o
/home/joep/Downloads/dripkg/agpgart-2.0/backend.c:68: error: conflicting types for &#8216;agp_backend_acquire&#8217;
include/linux/agp_backend.h:105: note: previous declaration of &#8216;agp_backend_acquire&#8217; was here
/home/joep/Downloads/dripkg/agpgart-2.0/backend.c:77: error: conflicting types for &#8216;agp_backend_acquire&#8217;
include/linux/agp_backend.h:105: note: previous declaration of &#8216;agp_backend_acquire&#8217; was here
/home/joep/Downloads/dripkg/agpgart-2.0/backend.c:88: error: conflicting types for &#8216;agp_backend_release&#8217;
include/linux/agp_backend.h:106: note: previous declaration of &#8216;agp_backend_release&#8217; was here
/home/joep/Downloads/dripkg/agpgart-2.0/backend.c:93: error: conflicting types for &#8216;agp_backend_release&#8217;
include/linux/agp_backend.h:106: note: previous declaration of &#8216;agp_backend_release&#8217; was here
/home/joep/Downloads/dripkg/agpgart-2.0/backend.c:220: error: expected &#8216;=&#8217;, &#8216;,&#8217;, &#8216;;&#8217;, &#8216;asm&#8217; or &#8216;__attribute__&#8217; before &#8216;drm_agp&#8217;
/home/joep/Downloads/dripkg/agpgart-2.0/backend.c: In function &#8216;agp_add_bridge&#8217;:
/home/joep/Downloads/dripkg/agpgart-2.0/backend.c:281: error: implicit declaration of function &#8216;inter_module_register&#8217;
/home/joep/Downloads/dripkg/agpgart-2.0/backend.c:281: error: &#8216;drm_agp&#8217; undeclared (first use in this function)
/home/joep/Downloads/dripkg/agpgart-2.0/backend.c:281: error: (Each undeclared identifier is reported only once
/home/joep/Downloads/dripkg/agpgart-2.0/backend.c:281: error: for each function it appears in.)
/home/joep/Downloads/dripkg/agpgart-2.0/backend.c: In function &#8216;agp_remove_bridge&#8217;:
/home/joep/Downloads/dripkg/agpgart-2.0/backend.c:301: error: implicit declaration of function &#8216;inter_module_unregister&#8217;
make[2]: *** [/home/joep/Downloads/dripkg/agpgart-2.0/backend.o] Fout 1
make[1]: *** [_module_/home/joep/Downloads/dripkg/agpgart-2.0] Fout 2
make[1]: Map '/usr/src/linux-headers-2.6.31-17-generic' wordt verlaten
make: *** [default] Fout 2
make -f Makefile.linux DRM_MODULES=gdg.ko modules
make[1]: Map '/home/joep/Downloads/dripkg/drm' wordt binnengegaan
+ ln -s Makefile.linux Makefile
make -C /lib/modules/2.6.31-17-generic/build  SUBDIRS=`pwd` DRMSRCDIR=`pwd` modules
make[2]: Map '/usr/src/linux-headers-2.6.31-17-generic' wordt binnengegaan
rm: kan `/home/joep/Downloads/dripkg/drm/.tmp_versions/CVS&#8217; niet verwijderen: Is een map
make[2]: *** [crmodverdir] Fout 1
make[2]: Map '/usr/src/linux-headers-2.6.31-17-generic' wordt verlaten
make[1]: *** [modules] Fout 2
make[1]: Map '/home/joep/Downloads/dripkg/drm' wordt verlaten
make: *** [gdg.ko] Fout 2

```Above error is in dutch though. I will translate if needed.

Anyone knows how to fix this?
Other information:
-I have dualboot with windows XP home edition
-Using Xubuntu 9.10 i386
-1GB ram
-Intel 82915G chipset
-Soundcard should be included in the chipset, at least my dad said that.
-Game i try to run is called: Stepmania. Uses 3D, but requires very low system requirements. I can play it smoothly on windows XP.

---

