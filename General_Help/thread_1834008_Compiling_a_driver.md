---
title: "Compiling a driver"
date: 2011-08-26
forum: General Help
---

### Post by searchfgold6789 on 2011-08-26
Hello ubuntuforums!
I have just downloaded and compiled some source code for my old graphics card, the tutorial I followed is here: [http://ubuntuforums.org/showthread.php?p=29080&mode=linear#post29080](http://ubuntuforums.org/showthread.php?p=29080&mode=linear#post29080)

Anyway, there's an auto-magic-installer-script-run-in-the-terminal-and-all-sorts-of-wizardry-happens-install.sh script. At the climax, it compiles source code. But all I get is a "compiling failed" error, with a message indicating that I should see a "dri.log" file. Which is here: (I highlighted the important-looking part)

```
make DRM_MODULES=mach64.o modules
make[1]: Entering directory `/home/richie/Desktop/Projects/dri/m/mach64-20060325-linux.i386/drm/linux-core'
make -C /lib/modules/2.6.32-21-generic/build  SUBDIRS=`pwd` DRMSRCDIR=`pwd` modules
make[2]: Entering directory `/usr/src/linux-headers-2.6.32-21-generic'
  CC [M]  /home/richie/Desktop/Projects/dri/m/mach64-20060325-linux.i386/drm/linux-core/drm_auth.o
In file included from /home/richie/Desktop/Projects/dri/m/mach64-20060325-linux.i386/drm/linux-core/drm_auth.c:36:
/home/richie/Desktop/Projects/dri/m/mach64-20060325-linux.i386/drm/linux-core/drmP.h:44:26: error: linux/config.h: No such file or directory
In file included from /home/richie/Desktop/Projects/dri/m/mach64-20060325-linux.i386/drm/linux-core/drmP.h:88,
                 from /home/richie/Desktop/Projects/dri/m/mach64-20060325-linux.i386/drm/linux-core/drm_auth.c:36:
/home/richie/Desktop/Projects/dri/m/mach64-20060325-linux.i386/drm/linux-core/drm_os_linux.h:62: error: conflicting types for &#8216;irqreturn_t&#8217;
include/linux/irqreturn.h:16: note: previous declaration of &#8216;irqreturn_t&#8217; was here
In file included from /home/richie/Desktop/Projects/dri/m/mach64-20060325-linux.i386/drm/linux-core/drmP.h:814,
                 from /home/richie/Desktop/Projects/dri/m/mach64-20060325-linux.i386/drm/linux-core/drm_auth.c:36:
[B]/home/richie/Desktop/Projects/dri/m/mach64-20060325-linux.i386/drm/linux-core/drm_memory.h: In function &#8216;agp_remap&#8217;:
/home/richie/Desktop/Projects/dri/m/mach64-20060325-linux.i386/drm/linux-core/drm_memory.h:129: error: &#8216;struct agp_memory&#8217; has no member named &#8216;memory&#8217;[/B]
make[3]: *** [/home/richie/Desktop/Projects/dri/m/mach64-20060325-linux.i386/drm/linux-core/drm_auth.o] Error 1
make[2]: *** [_module_/home/richie/Desktop/Projects/dri/m/mach64-20060325-linux.i386/drm/linux-core] Error 2
make[2]: Leaving directory `/usr/src/linux-headers-2.6.32-21-generic'
make[1]: *** [modules] Error 2
make[1]: Leaving directory `/home/richie/Desktop/Projects/dri/m/mach64-20060325-linux.i386/drm/linux-core'
make: *** [mach64.o] Error 2

```What does it mean? some sort of agp_memory thing?
Any help in understanding this make code would be much appreciated!!
 - search

---

### Post by searchfgold6789 on 2011-08-26
help??? Trying an upgrade now...

---

### Post by kerry_s on 2011-08-26
dude, thats from 2006, xorg has changed since then.

---

### Post by searchfgold6789 on 2011-08-26
Yeah, I'm not doing both at the same time jack'.

kerry', what do you mean? is there any evidence to prove that this would not work?

---

### Post by kerry_s on 2011-08-27
> kerry', what do you mean? is there any evidence to prove that this would not work?

what i'm saying is "why do you need to build it when it's already standard?".

if you need the latest, add the xorg-edgers ppa:
[https://launchpad.net/~xorg-edgers/+archive/ppa/+index?field.series_filter=natty](https://launchpad.net/~xorg-edgers/+archive/ppa/+index?field.series_filter=natty)

---

### Post by searchfgold6789 on 2011-08-27
Do you mean to say that the drivers are already installed for me?
EDIT: OK! THANK YOU!

---

### Post by Mark Phelps on 2011-08-27
The drivers that are installed are the default open-source drivers.  They should give you acceptable performance for 2D graphics but they don't include hardware acceleration.

The drivers you are trying to compile will NOT work with recent versions of the X-server. So, your'e wasting your time with them.

---

