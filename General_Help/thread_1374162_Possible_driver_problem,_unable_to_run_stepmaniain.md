---
title: "Possible driver problem, unable to run stepmania/install drivers"
date: 2010-01-06
forum: General Help
---

### Post by Drojoke on 2010-01-06
I installed Xubuntu a couple of days ago on my pc (Which means im really new to linux), i got xubuntu and windows XP on 1 desktop now. After the install and all updates were done i downloaded the binary version of Stepmania (Stepmania is a DDR like game available for mac, windows and linux).  Link to the download: [http://www.stepmania.com/wiki/Downloads](http://www.stepmania.com/wiki/Downloads) 
After i extracted the game i tried to run it, which failed. Nothing happened. The file was set as an executable but it still did not start. After a while it did start, no idea what i did though. 
When i start stepmania now, you see the stepmania logo in the middle of the screen (which is normal) and then i get a black screen and after like 3 seconds the game brings me back to linux again. Only thing i get is a logfile with this information:
```
00:00.005: StepMania 3.9
00:00.014: Log starting 2010-01-06 18:10:55
00:00.016:  
00:00.016: Reading 'Data/Defaults.ini' failed: No such file or directory
00:00.016: Reading 'Data/StepMania.ini' failed: No such file or directory
00:00.016: Reading 'Data/Static.ini' failed: No such file or directory
00:00.064: Couldn't load driver gtk: Couldn't initialize gtk (cannot open display)
00:00.066: 
00:00.066: //////////////////////////////////////////////////////
00:00.066: Exception: Couldn't initialize SDL: No available video device
00:00.066: //////////////////////////////////////////////////////
00:00.066: 
00:00.066: Couldn't load driver sdl: Couldn't initialize SDL: No available video device
00:00.068: 
00:00.068: //////////////////////////////////////////////////////
00:00.068: Exception: Couldn't open any loading windows.
00:00.068: //////////////////////////////////////////////////////
00:00.068: 
```So i am currently not able to run stepmania (uses 3d stuff) and the standard chess game on ubuntu in 3d mode, so i thought it might be something with my drivers? When i go to applications - system - hardware drivers, it says there are no drivers installed (except for a broadcom wireless driver, which i don't need because im not on wireless internet) 
So i tried to download the video card driver from intel. My graphics card is:
-Intel 82915G/GV/910GL Integrated Graphics Controller (128 mb)

So i downloaded the driver, extracted it and tried to run the install.sh. I was able to start the installation with the linux console screen, but after it started to install the driver i got an error:
```
DIRECT RENDERING OPEN SOURCE PROJECT  -  DRIVER INSTALLATION SCRIPT

[ http://dri.sourceforge.net ]

==========================================================================

The script will now compile the agpgart module and DRM kernel modules
for your machine.

Press ENTER to continue or CTRL-C to exit.


Compiling new agpgart module...

ERROR: AGPGART module did not compile

Compiling DRM module...

ERROR: Kernel modules did not compile

The DRI drivers can not be installed without the latest kernel modules.
Installation will be aborted. See the dri.log file for information on
what went wrong.

joep@Xubuntu:~/Downloads/dripkg$ 

```The dri.log file says:

```
make -C /lib/modules/2.6.31-16-generic/build SUBDIRS=/home/joep/Downloads/dripkg/agpgart-2.0 modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.31-16-generic'
  CC [M]  /home/joep/Downloads/dripkg/agpgart-2.0/intel-agp.o
/home/joep/Downloads/dripkg/agpgart-2.0/intel-agp.c: In function &#8216;i8xx_alloc_pages&#8217;:
/home/joep/Downloads/dripkg/agpgart-2.0/intel-agp.c:165: error: implicit declaration of function &#8216;change_page_attr&#8217;
/home/joep/Downloads/dripkg/agpgart-2.0/intel-agp.c:171: error: implicit declaration of function &#8216;SetPageLocked&#8217;
/home/joep/Downloads/dripkg/agpgart-2.0/intel-agp.c: In function &#8216;intel_i810_insert_entries&#8217;:
/home/joep/Downloads/dripkg/agpgart-2.0/intel-agp.c:232: error: &#8216;struct agp_memory&#8217; has no member named &#8216;memory&#8217;
/home/joep/Downloads/dripkg/agpgart-2.0/intel-agp.c: In function &#8216;alloc_agpphysmem_i8xx&#8217;:
/home/joep/Downloads/dripkg/agpgart-2.0/intel-agp.c:285: error: &#8216;struct agp_memory&#8217; has no member named &#8216;memory&#8217;
/home/joep/Downloads/dripkg/agpgart-2.0/intel-agp.c:288: error: &#8216;struct agp_memory&#8217; has no member named &#8216;memory&#8217;
/home/joep/Downloads/dripkg/agpgart-2.0/intel-agp.c:288: error: &#8216;struct agp_memory&#8217; has no member named &#8216;memory&#8217;
/home/joep/Downloads/dripkg/agpgart-2.0/intel-agp.c:289: error: &#8216;struct agp_memory&#8217; has no member named &#8216;memory&#8217;
/home/joep/Downloads/dripkg/agpgart-2.0/intel-agp.c:289: error: &#8216;struct agp_memory&#8217; has no member named &#8216;memory&#8217;
/home/joep/Downloads/dripkg/agpgart-2.0/intel-agp.c:290: error: &#8216;struct agp_memory&#8217; has no member named &#8216;memory&#8217;
/home/joep/Downloads/dripkg/agpgart-2.0/intel-agp.c:290: error: &#8216;struct agp_memory&#8217; has no member named &#8216;memory&#8217;
/home/joep/Downloads/dripkg/agpgart-2.0/intel-agp.c:295: error: &#8216;struct agp_memory&#8217; has no member named &#8216;memory&#8217;
/home/joep/Downloads/dripkg/agpgart-2.0/intel-agp.c: In function &#8216;intel_i810_alloc_by_type&#8217;:
/home/joep/Downloads/dripkg/agpgart-2.0/intel-agp.c:314: error: &#8216;struct agp_memory&#8217; has no member named &#8216;memory&#8217;
/home/joep/Downloads/dripkg/agpgart-2.0/intel-agp.c: In function &#8216;intel_i810_free_by_type&#8217;:
/home/joep/Downloads/dripkg/agpgart-2.0/intel-agp.c:328: error: &#8216;struct agp_memory&#8217; has no member named &#8216;memory&#8217;
/home/joep/Downloads/dripkg/agpgart-2.0/intel-agp.c:331: error: &#8216;struct agp_memory&#8217; has no member named &#8216;memory&#8217;
/home/joep/Downloads/dripkg/agpgart-2.0/intel-agp.c:332: error: &#8216;struct agp_memory&#8217; has no member named &#8216;memory&#8217;
/home/joep/Downloads/dripkg/agpgart-2.0/intel-agp.c: In function &#8216;intel_i830_insert_entries&#8217;:
/home/joep/Downloads/dripkg/agpgart-2.0/intel-agp.c:580: error: &#8216;struct agp_memory&#8217; has no member named &#8216;memory&#8217;
/home/joep/Downloads/dripkg/agpgart-2.0/intel-agp.c: In function &#8216;intel_i915_insert_entries&#8217;:
/home/joep/Downloads/dripkg/agpgart-2.0/intel-agp.c:686: error: &#8216;struct agp_memory&#8217; has no member named &#8216;memory&#8217;
/home/joep/Downloads/dripkg/agpgart-2.0/intel-agp.c: At top level:
/home/joep/Downloads/dripkg/agpgart-2.0/intel-agp.c:1239: error: &#8216;TRUE&#8217; undeclared here (not in a function)
/home/joep/Downloads/dripkg/agpgart-2.0/intel-agp.c: In function &#8216;agp_intel_suspend&#8217;:
/home/joep/Downloads/dripkg/agpgart-2.0/intel-agp.c:1726: error: too many arguments to function &#8216;pci_save_state&#8217;
/home/joep/Downloads/dripkg/agpgart-2.0/intel-agp.c:1731: error: too many arguments to function &#8216;pci_save_state&#8217;
/home/joep/Downloads/dripkg/agpgart-2.0/intel-agp.c:1736: error: too many arguments to function &#8216;pci_save_state&#8217;
/home/joep/Downloads/dripkg/agpgart-2.0/intel-agp.c: In function &#8216;agp_intel_resume&#8217;:
/home/joep/Downloads/dripkg/agpgart-2.0/intel-agp.c:1749: error: too many arguments to function &#8216;pci_restore_state&#8217;
/home/joep/Downloads/dripkg/agpgart-2.0/intel-agp.c:1754: error: too many arguments to function &#8216;pci_restore_state&#8217;
/home/joep/Downloads/dripkg/agpgart-2.0/intel-agp.c:1759: error: too many arguments to function &#8216;pci_restore_state&#8217;
/home/joep/Downloads/dripkg/agpgart-2.0/intel-agp.c: At top level:
/home/joep/Downloads/dripkg/agpgart-2.0/intel-agp.c:1792: warning: initialization from incompatible pointer type
/home/joep/Downloads/dripkg/agpgart-2.0/intel-agp.c: In function &#8216;agp_intel_init&#8217;:
/home/joep/Downloads/dripkg/agpgart-2.0/intel-agp.c:1806: error: implicit declaration of function &#8216;pci_module_init&#8217;
make[2]: *** [/home/joep/Downloads/dripkg/agpgart-2.0/intel-agp.o] Error 1
make[1]: *** [_module_/home/joep/Downloads/dripkg/agpgart-2.0] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.31-16-generic'
make: *** [default] Error 2
make -f Makefile.linux DRM_MODULES=gdg.ko modules
make[1]: Entering directory `/home/joep/Downloads/dripkg/drm'
make -C /lib/modules/2.6.31-16-generic/build  SUBDIRS=`pwd` DRMSRCDIR=`pwd` modules
make[2]: Entering directory `/usr/src/linux-headers-2.6.31-16-generic'
rm: cannot remove `/home/joep/Downloads/dripkg/drm/.tmp_versions/CVS': Is a directory
make[2]: *** [crmodverdir] Error 1
make[2]: Leaving directory `/usr/src/linux-headers-2.6.31-16-generic'
make[1]: *** [modules] Error 2
make[1]: Leaving directory `/home/joep/Downloads/dripkg/drm'
make: *** [gdg.ko] Error 2
```Well, those problems listed above are my problems now. Things i would like to know are: Do i need to install intel's drivers? And if so, how do i get them to install correctly.

Sorry for any bad grammar above.

Thanks for your time :)

---

### Post by Drojoke on 2010-01-06
Bump, anyone can help please?

---

### Post by Drojoke on 2010-01-08
Could anyone at least help me with this error?
```

DIRECT RENDERING OPEN SOURCE PROJECT  -  DRIVER INSTALLATION SCRIPT

[ http://dri.sourceforge.net ]

==========================================================================

The script will now compile the agpgart module and DRM kernel modules
for your machine.

Press ENTER to continue or CTRL-C to exit.


Compiling new agpgart module...

ERROR: AGPGART module did not compile

Compiling DRM module...

ERROR: Kernel modules did not compile

The DRI drivers can not be installed without the latest kernel modules.
Installation will be aborted. See the dri.log file for information on
what went wrong.
```

joep@Xubuntu:~/Downloads/dripkg$

---

