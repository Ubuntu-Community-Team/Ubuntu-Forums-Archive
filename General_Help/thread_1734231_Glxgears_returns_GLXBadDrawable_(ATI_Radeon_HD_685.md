---
title: "Glxgears returns GLXBadDrawable (ATI Radeon HD 6850)"
date: 2011-04-20
forum: General Help
---

### Post by Flipflops4life on 2011-04-20
Hello folks!

After a lot of work and a little luck I finally got my Radeon 6850 running again but I can't get any 3d rendering (I'm guessing that's the issue?) Basically if I try to run any type of game from quadrapassel to Civ IV the application window will appear and then instantly close. Compiz & desktop effects work fine.

I followed the cchtml wiki for the installation of the catalyst drivers and here's where I think my problem lies

When I enter the command: $ glxgears I get this:

:~$ glxgears
X Error of failed request:  GLXBadDrawable
  Major opcode of failed request:  161 (GLX)
  Minor opcode of failed request:  11 (X_GLXSwapBuffers)
  Serial number of failed request:  78
  Current serial number in output stream:  111

Any ideas where to go from here? I've tried installing the xorg edgers ppa (I think that was the name). But still no effect. I have also tried disabling fastTLS.

Here is a copy of my xorg.conf file if that will help. 

Section "ServerLayout"
    Identifier     "aticonfig Layout"
    Screen      0  "aticonfig-Screen[0]-0" 0 0
EndSection

Section "Module"
    Load  "GLcore"
    Load  "glx"
    Load  "dri"
EndSection

Section "Monitor"
    Identifier   "aticonfig-Monitor[0]-0"
    Option        "VendorName" "ATI Proprietary Driver"
    Option        "ModelName" "Generic Autodetecting Monitor"
    Option        "DPMS" "true"
EndSection

Section "Device"
    Identifier  "aticonfig-Device[0]-0"
    Driver      "fglrx"
    Option        "UseFastTLS" "0"
    BusID       "PCI:2:0:0"
Option "AddARGBVisuals" "True"
Option "AddARGBGLXVisuals" "True"
EndSection

Section "Screen"
    Identifier "aticonfig-Screen[0]-0"
    Device     "aticonfig-Device[0]-0"
    Monitor    "aticonfig-Monitor[0]-0"
    DefaultDepth     24
    SubSection "Display"
        Viewport   0 0
        Depth     24
    EndSubSection
EndSection

Any direction you guys could give me would be great, no rush tho - finals are coming up so I don't need to be getting all I can get out of my GPU right now anyway :P Mahalo!

---

