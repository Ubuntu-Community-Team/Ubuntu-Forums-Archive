---
title: "Trying to Compile LinuxWacom on Breezy, need Xorg SDK"
date: 2006-03-18
forum: General Help
---

### Post by WDot on 2006-03-18
Exactly what the title says.  Without it, I get this during ./configure:

```
  BUILD ENVIRONMENT:
       architecture - i686
       linux kernel - yes 2.6.11
  module versioning - yes -DCONFIG_MODVERSIONS -DMODVERSIONS -include /usr/src/linux/include/linux/modversions.h
      kernel source - yes /usr/src/linux
           Xorg SDK - no /home/miguel/Desktop/linuxwacom-0.7.2
          XSERVER64 - no
           dlloader - no
               XLib - yes /usr/X11R6/lib
                TCL - yes /usr/include/tcl8.4/
                 TK - yes /usr/include/tcl8.4/
            ncurses - yes

  BUILD OPTIONS:
            wacom.o - no
            wacdump - yes
             xidump - yes
        libwacomcfg - yes
         libwacomxi - yes
          xsetwacom - yes
              hid.o - no
         usbmouse.o - no
            evdev.o - no
         mousedev.o - no
            input.o - no
        tabletdev.o - no
       wacom_drv.so - no
        wacom_drv.o - no

```

And subsequently get problems during make.  I can't find a Xorg SDK on Synaptic, even with Universe/Multiverse enabled.  I've downloaded and installed pretty much every X11 development library I could find, but none of them has the "Xorg SDK" I seek.  Some tutorials on the Ubuntu website for making Wacom tablets work involve simply configuring and making LinuxWacom, but it's not as simple for me.

I'm using an Intuos3 tablet if it helps.

---

