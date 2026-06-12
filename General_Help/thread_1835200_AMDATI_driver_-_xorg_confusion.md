---
title: "AMD/ATI driver - xorg confusion"
date: 2011-08-28
forum: General Help
---

### Post by eresrch on 2011-08-28
Under Ubuntu 10.04 I have tried loading an AMD/ATI driver for an 880 chip set (which includes an HD4250 graphics card equivalent).  The driver AMD recommends is: ati-driver-installer-11-8-x86.x86_64.run.  After I run that I do
sudo aticonfig --initial
and then do a reboot.  I then try to run Catalyst and I get the error:

p, li { white-space: pre-wrap; } "There was a problem initializing Catalyst Control Center Linux edition.  It could be caused by the following.
 
 

No AMD graphics driver is installed, or the AMD driver is not functioning properly.
 Please install the AMD driver appropriate for you AMD hardware, or configure using aticonfig."


If I look under System->Admin->Hardware Drivers it shows ATI/AMD proprietary FGLRX graphics driver is activated.


The file xorg.conf has the following data:
==================================================================================

Section "ServerLayout"
    Identifier     "aticonfig Layout"
    Screen      0  "aticonfig-Screen[0]-0" 0 0
EndSection

Section "Files"
EndSection

Section "Module"
    Load  "glx"
EndSection

Section "Monitor"
    Identifier   "aticonfig-Monitor[0]-0"
    Option        "Horizsync" "30kHz - 70kHz"
    Option        "Vertrefresh" "50Hz - 60Hz"
    Option        "VendorName" "ATI Proprietary Driver"
    Option        "ModelName" "Generic Autodetecting Monitor"
    Option        "DPMS" "true"
EndSection

Section "Device"
    Identifier  "aticonfig-Device[0]-0"
    Driver      "fglrx"
    BusID       "PCI:1:5:0"
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
================================================================================


The Xorg.log file shows the RADEON load was successful, but it shows up with
(EE) GLX error: Can not get required symbols.
in the middle of it all.  So the "glxgears" does not work either giving the error:

X Error of failed request:  BadRequest (invalid request code or no such operation)
  Major opcode of failed request:  135 (GLX)
  Minor opcode of failed request:  19 (X_GLXQueryServerString)
  Serial number of failed request:  12
  Current serial number in output stream:  12

I also have an nvidia driver installed so I can program CUDA on card in a PCIE slot, but that should not be connected since it is not seen at boot by Xorg.

I don't understand why Catalyst doesn't run nor why fglrx doesn't run glxgears or glxinfo when the driver is reported as active.  My net searches must not be using the right keywords because everything I've found doesn't seem to change the problem.  If anyone has any clues on how to fix this I'd really appreciate it!

Thanks,
Mike

---

