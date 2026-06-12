---
title: "MESA LG and ATI"
date: 2005-03-02
forum: General Help
---

### Post by teumima on 2005-03-02
Hi

I have an ATI Readeon 9200. I can't get rid of the MESA LG, so everything is running 3D but really slowly, can anyone help me please.

Thanx

a.t.

---

### Post by kidrock on 2005-03-03
Hi, did you manage to solve your problem....I am having the same problem...
I tried installing the driver sudo  apt-get install fglrx-driver... installs but cant get rid of mesa....tried the guide here without success.  :confused:

---

### Post by teumima on 2005-03-03
No. Still haven't solved it man. The fact that nobody can help, maybe says that it's a real issue with no solution at the mo.

There must be a solution, at least one better than throwing away my Radeon and buying an NVIDIA card.

---

### Post by teumima on 2005-03-03
sucks

---

### Post by teumima on 2005-03-03
There has to be a way to install over them, anyone? please?

---

### Post by bobmitch on 2005-03-03
[QUOTE=teumima]There has to be a way to install over them, anyone? please?[/QUOTE]

Once you have installed the fglrx driver package, did you change the driver in the xfree config file from "ati" to "fglrx"?

---

### Post by kidrock on 2005-03-03
When I change the from ATI to fglrx in the Xfree config file, XServer wont boot...

Just to make sure I had installed the Fglrx drivers I tried the guide here and this is the error I got with Alien. 
root@ubuntu:/mnt/HDA-6 # sudo alien fglrx.rpm
mkdir: cannot create directory `fglrx_4_3_0-8.10.19': File exists
mkdir: cannot create directory `fglrx_4_3_0-8.10.19/debian': File exists
Package build failed. Here's the log:
dh_testdir
dh_testdir
dh_testroot
dh_clean -k
dh_installdirs
dh_installdocs
dh_installchangelogs
find . -maxdepth 1 -mindepth 1 -not -name debian -print0 | \
xargs -0 -r -i cp -a {} debian/fglrx-4-3-0
dh_compress
dh_makeshlibs
dh_installdeb
dh_shlibdeps
dpkg-shlibdeps: warning: format of libfglrx_gamma.1 not recognized
dh_gencontrol
sh: line 1: gcc: command not found
dpkg-architecture: warning: Couldn't determine gcc system type, falling back to default (native compilation)
sh: line 1: gcc: command not found
dpkg-architecture: warning: Couldn't determine gcc system type, falling back to default (native compilation)
dh_md5sums
dh_builddeb
dpkg-deb: control directory has bad permissions 777 (must be >=0755 and <=0775)
dpkg-deb: building package `fglrx-4-3-0' in `../fglrx-4-3-0_8.10.19-2_i386.deb'.
dh_builddeb: command returned error code 512
make: *** [binary-arch] Error 1
find: fglrx_4_3_0-8.10.19: No such file or directory


Why do things have to be so complicated  :? 
No way I am changing a card for an OS.

Regards....

---

### Post by teumima on 2005-03-04
Ok this is what my config file looks like:

Section "Device"
    Identifier                          "ATI Graphics Adapter"
    Driver                              "fglrx"
# ### generic DRI settings ###
# === disable PnP Monitor  ===
    #Option                              "NoDDC"
# === disable/enable XAA/DRI ===
    Option "no_accel"                   "no"
    Option "no_dri"                     "no"
# === misc DRI settings ===
    Option "mtrr"                       "off" # disable DRI mtrr mapper, driver has its own code for mtrr
# ### FireGL DDX driver module specific settings ###
# === Screen Management ===
    Option "DesktopSetup"               "0x00000000" 
    Option "MonitorLayout"              "AUTO, AUTO"
    Option "IgnoreEDID"                 "off"
    Option "HSync2"                     "unspecified" 
    Option "VRefresh2"                  "unspecified" 
    Option "ScreenOverlap"              "0" 
# === TV-out Management ===
    Option "NoTV"                       "no"     
    Option "TVStandard"                 "NTSC-M"     
    Option "TVHSizeAdj"                 "0"     
    Option "TVVSizeAdj"                 "0"     
    Option "TVHPosAdj"                  "0"     
    Option "TVVPosAdj"                  "0"     
    Option "TVHStartAdj"                "0"     
    Option "TVColorAdj"                 "0"     
    Option "GammaCorrectionI"           "0x00000000"
    Option "GammaCorrectionII"          "0x00000000"
# === OpenGL specific profiles/settings ===
    Option "Capabilities"               "0x00000000"
# === Video Overlay for the Xv extension ===
    Option "VideoOverlay"               "on"
# === OpenGL Overlay ===
# Note: When OpenGL Overlay is enabled, Video Overlay
#       will be disabled automatically
    Option "OpenGLOverlay"              "off"
# === Center Mode (Laptops only) ===
    Option "CenterMode"                 "off"
# === Pseudo Color Visuals (8-bit visuals) ===
    Option "PseudoColorVisuals"         "off"
# === QBS Management ===
    Option "Stereo"                     "off"
    Option "StereoSyncEnable"           "1"
# === FSAA Management ===
    Option "FSAAEnable"                 "no"
    Option "FSAAScale"                  "1"
    Option "FSAADisableGamma"           "no"
    Option "FSAACustomizeMSPos"         "no"
    Option "FSAAMSPosX0"                "0.000000"
    Option "FSAAMSPosY0"                "0.000000"
    Option "FSAAMSPosX1"                "0.000000"
    Option "FSAAMSPosY1"                "0.000000"
    Option "FSAAMSPosX2"                "0.000000"
    Option "FSAAMSPosY2"                "0.000000"
    Option "FSAAMSPosX3"                "0.000000"
    Option "FSAAMSPosY3"                "0.000000"
    Option "FSAAMSPosX4"                "0.000000"
    Option "FSAAMSPosY4"                "0.000000"
    Option "FSAAMSPosX5"                "0.000000"
    Option "FSAAMSPosY5"                "0.000000"
# === Misc Options ===
    Option "UseFastTLS"                 "2"
    Option "BlockSignalsOnLock"         "on"
    Option "UseInternalAGPGART"         "no"
    Option "ForceGenericCPU"            "no"
    Option "KernelModuleParm"           "agplock=0" # AGP locked user pages: disabled
    BusID "PCI:2:0:0"    # vendor=1002, device=5964
    Screen 0
EndSection


I can see that a lot of things seem to be the wrong option? like no 3d Accelaration? Can someone help me sort this out? The only thing that I did change is the "ati" fgl..."

---

### Post by kidrock on 2005-03-04
I cant change the Driver from ATi to Fglrx...When i do that XServer wont start..... \\:D/

---

### Post by bobmitch on 2005-03-04
Looks to me like you guys need to create a brand new config using 'fglrxconfig'.
If you have the latest drivers this will create an xorg.conf file, otherwise it will be a standard xfree86 config file, which you may have to rename if you are running xorg.

---

### Post by kidrock on 2005-03-04
This is the error i encounter when i  use sh make.sh

root@ubuntu:/lib/modules/fglrx/build_mod # sudo sh make.sh
make.sh: line 1: gcc: command not found
make.sh: line 52: [: !=: unary operator expected
ATI module generator V 2.0
==========================
initializing...
cleaning...
patching 'highmem.h'...
assuming new VMA API since we do have kernel 2.6.x...
doing Makefile based build for kernel 2.6.x and higher
/bin/sh: line 1: gcc: command not found
/bin/sh: line 1: gcc: command not found
ln: `./libfglrx_ip.a.GCC': File exists
make: *** [libfglrx_ip.a.GCC] Error 1
build failed with return value 2
root@ubuntu:/lib/modules/fglrx/build_mod #

---

### Post by kidrock on 2005-03-04
this is the error i encounter now 

root@ubuntu:/lib/modules/fglrx # sh make_install.sh
- creating symlink
- recreating module dependency list
- trying a sample load of the kernel module
FATAL: Error inserting fglrx (/lib/modules/2.6.8.1-3-386/kernel/drivers/video/fglrx.ko): Operation not permitted
failed.
root@ubuntu:/lib/modules/fglrx #


and 

root@ubuntu:/lib/modules/fglrx # rmmod fglrx
ERROR: Module fglrx does not exist in /proc/modules
root@ubuntu:/lib/modules/fglrx #

---

### Post by kidrock on 2005-03-04
Okay...I managed to install the prop ATI drivers
but still fglrxinfo shows mesa   :?:  :confused:

---

### Post by Scottles on 2005-03-04
Looking at the error log you have posted, you havent installed GCC! You will need to install that and the kernel headers *before* you try to install the ATi drivers!

The error you get with the "rmmod fglrx" command is normal.. This command is to unload any instance of fglrx currently running.. The error just means you don't already have the driver installed/running.

Hope that helps! :)

---

### Post by kidrock on 2005-03-04
Hi, I installed the driver...but still running under mesa.

If I change "ATI" to fglrx in the config file, XServer wont star.....any reason for that?

---

### Post by teumima on 2005-03-05
hi bobmix

can u guide me with this?

---

### Post by bobmitch on 2005-03-06
[QUOTE=teumima]hi bobmix

can u guide me with this?[/QUOTE]

I can try.

Did you run 'fglrxconfig' to generate a proper X config file?

---

### Post by teumima on 2005-03-07
yes

---

