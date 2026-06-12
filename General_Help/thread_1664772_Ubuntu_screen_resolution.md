---
title: "Ubuntu screen resolution"
date: 2011-01-11
forum: General Help
---

### Post by jimmys_ on 2011-01-11
I tried both 10.10 64 and 32 bit and after updating everything I still can't get a higher resolution than 1024x768 for my monitor which supports up to 1680x1050. I have an Intel DQ965GF motherboard and I'm using the onboard graphics card Intel GMA3000 which can give resolutions up to 2048x1536. What is the problem?

---

### Post by mtdave on 2011-01-11
Hey, I'm having the same problem. I upgraded from 10.04 LT to 10.10 and now my highest resolution choice is 1024x768. I had it set to higher resolution in previous versions of Ubuntu. What happened to my choices? How do I get them back?

Thanks

---

### Post by mtdave on 2011-01-11
My graphics card is an on-board "Intel 82915G Express Chipset Family". I guess Ubuntu must have dropped that driver from the 10.04LT distribution to the 10.10 distribution. I went on the Intel site and searched and found a Linux download of the "i915 Graphics" driver. Inside the tar.gz is a folder drpkg that contains an install.sh file and lots of other stuff. Can I install this? Will it change my resolution options?

How do I install it?

---

### Post by marbour on 2011-01-11
@mtdave
> How do I install it?     Personnally, I would not have any problems installing it. It comes from a big renouned company.

To install it... Unzip everything somewhere... right click on the install.sh, go to permissions tabs and render it executable. Close the dialog and double-click the install.sh.

It may be possible that nautilus doesn't let you do some/all of the above, then you have to open a system console screen to do it...


[LIST]
[*]alt-f2
[*]type gnome-terminal and press enter
[*]cd /dir/where/you/unzipped/your/stuff and press enter
[*]sudo chmod +x install.sh (you'll be asked for your root password...)
[*]then simply type ./install.sh and press enter... If it doesn't let you install on account that you are not root... then type sudo ./install.sh
[*]the install script will probably ask you some stuff, confirm some choices... From there on, you are "on your own" for I don't know what will be asked.
[*]it's possible you may have to restart your X server (ctrl-alt-backspace that may be turned off by default for a while in ubuntu now... Then you should simply reboot)
[/LIST]
That ought to do it.

Regards.

Marc

---

### Post by mtdave on 2011-01-11
So I did the following and got an error:

```

pucuz3@pucuz3-desktop:~/graphics_driver/dripkg$ sudo chmod +x install.sh
[sudo] password for pucuz3: 
pucuz3@pucuz3-desktop:~/graphics_driver/dripkg$ sudo ./install.sh


DIRECT RENDERING OPEN SOURCE PROJECT  -  DRIVER INSTALLATION SCRIPT

[ http://dri.sourceforge.net ]

==========================================================================

Welcome to the DRI Driver Installation Script

The package you downloaded is for the following driver: 

Driver Name    : gdg
Description    : Intel 830M/845G/852GM/855GM/865G/915G Driver
Architecture   : I386
Build Date     : 20040604
Kernel Module  : gdg

Optional Information

Driver Version      :  
Special Description :  

Press ENTER to continue or CTRL-C to exit.



DIRECT RENDERING OPEN SOURCE PROJECT  -  DRIVER INSTALLATION SCRIPT

[ http://dri.sourceforge.net ]

==========================================================================

Select from the following options:

  1. Install driver (default)
  2. Uninstall driver

Enter reponse [1-2], or CTRL-C to exit
1
get_osname()










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

pucuz3@pucuz3-desktop:~/graphics_driver/dripkg$

```Here are the contents of my dri.log. Any ideas?

```

make -C /lib/modules/2.6.35-24-generic/build SUBDIRS=/home/pucuz3/graphics_driver/dripkg/agpgart-2.0 modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.35-24-generic'
  CC [M]  /home/pucuz3/graphics_driver/dripkg/agpgart-2.0/backend.o
/home/pucuz3/graphics_driver/dripkg/agpgart-2.0/backend.c:68: error: conflicting types for ‘agp_backend_acquire’
include/linux/agp_backend.h:107: note: previous declaration of ‘agp_backend_acquire’ was here
/home/pucuz3/graphics_driver/dripkg/agpgart-2.0/backend.c:77: error: conflicting types for ‘agp_backend_acquire’
include/linux/agp_backend.h:107: note: previous declaration of ‘agp_backend_acquire’ was here
/home/pucuz3/graphics_driver/dripkg/agpgart-2.0/backend.c:88: error: conflicting types for ‘agp_backend_release’
include/linux/agp_backend.h:108: note: previous declaration of ‘agp_backend_release’ was here
/home/pucuz3/graphics_driver/dripkg/agpgart-2.0/backend.c:93: error: conflicting types for ‘agp_backend_release’
include/linux/agp_backend.h:108: note: previous declaration of ‘agp_backend_release’ was here
/home/pucuz3/graphics_driver/dripkg/agpgart-2.0/backend.c:220: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘drm_agp’
/home/pucuz3/graphics_driver/dripkg/agpgart-2.0/backend.c: In function ‘agp_add_bridge’:
/home/pucuz3/graphics_driver/dripkg/agpgart-2.0/backend.c:281: error: implicit declaration of function ‘inter_module_register’
/home/pucuz3/graphics_driver/dripkg/agpgart-2.0/backend.c:281: error: ‘drm_agp’ undeclared (first use in this function)
/home/pucuz3/graphics_driver/dripkg/agpgart-2.0/backend.c:281: error: (Each undeclared identifier is reported only once
/home/pucuz3/graphics_driver/dripkg/agpgart-2.0/backend.c:281: error: for each function it appears in.)
/home/pucuz3/graphics_driver/dripkg/agpgart-2.0/backend.c: In function ‘agp_remove_bridge’:
/home/pucuz3/graphics_driver/dripkg/agpgart-2.0/backend.c:301: error: implicit declaration of function ‘inter_module_unregister’
make[2]: *** [/home/pucuz3/graphics_driver/dripkg/agpgart-2.0/backend.o] Error 1
make[1]: *** [_module_/home/pucuz3/graphics_driver/dripkg/agpgart-2.0] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.35-24-generic'
make: *** [default] Error 2
make -f Makefile.linux DRM_MODULES=gdg.ko modules
make[1]: Entering directory `/home/pucuz3/graphics_driver/dripkg/drm'
+ ln -s Makefile.linux Makefile
make -C /lib/modules/2.6.35-24-generic/build  SUBDIRS=`pwd` DRMSRCDIR=`pwd` modules
make[2]: Entering directory `/usr/src/linux-headers-2.6.35-24-generic'
rm: cannot remove `/home/pucuz3/graphics_driver/dripkg/drm/.tmp_versions/CVS': Is a directory
make[2]: *** [crmodverdir] Error 1
make[2]: Leaving directory `/usr/src/linux-headers-2.6.35-24-generic'
make[1]: *** [modules] Error 2
make[1]: Leaving directory `/home/pucuz3/graphics_driver/dripkg/drm'
make: *** [gdg.ko] Error 2

```Thanks

---

### Post by marbour on 2011-01-11
> The DRI drivers can not be installed without the latest kernel modules

It seems you could use synaptic package manager to install kernel modules.

Not being too proficient, I may suggest someone else bump into this discussion to tell you what they are and how they are called in synaptic.

You logs also indicate you are using a much newer kernel then mine and my ubuntu is fully updated. Maybe you are under 10.10 and I would not want to help you break something else.

Sorry I couldn't be of more help to you.

Marc

---

### Post by mtdave on 2011-01-11
Marc, thanks. Hopefully we'll get someone else involved who has an idea how to fix this. This happened after I upgraded to 10.10.

Dave

---

### Post by jimmys_ on 2011-01-12
I don't know if this happens only to me but 10.10 seems to be full of problems!! I've been trying Ubuntu since 7.04 and never encountered so many problems. New versions are supposed to fix problems not create new. I'll probably switch back to an earlier version.

---

### Post by realzippy on 2011-01-12
915resolution is an old package,which meanwhile should be integrated in 
actual kernels;note that it does not exist anymore in newer Ubuntu versions.
Suggest to create a basic xorg.conf file.
Press Alt+Ctrl+F1
log in with your username+password
type:

```
sudo service gdm stop
sudo Xorg -configure
sudo reboot

```
Now you have a file  "xorg.conf.new" in your home directory.
Post the file here so we can modify
it for a quick test.

---

### Post by mtdave on 2011-01-12
Realzippy, here are the contents of my xorg.conf.new:

```

Section "ServerLayout"
    Identifier     "X.org Configured"
    Screen      0  "Screen0" 0 0
    InputDevice    "Mouse0" "CorePointer"
    InputDevice    "Keyboard0" "CoreKeyboard"
EndSection

Section "Files"
    ModulePath   "/usr/lib/xorg/modules"
    FontPath     "/usr/share/fonts/X11/misc"
    FontPath     "/usr/share/fonts/X11/cyrillic"
    FontPath     "/usr/share/fonts/X11/100dpi/:unscaled"
    FontPath     "/usr/share/fonts/X11/75dpi/:unscaled"
    FontPath     "/usr/share/fonts/X11/Type1"
    FontPath     "/usr/share/fonts/X11/100dpi"
    FontPath     "/usr/share/fonts/X11/75dpi"
    FontPath     "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
    FontPath     "built-ins"
EndSection

Section "Module"
    Load  "record"
    Load  "dbe"
    Load  "dri2"
    Load  "dri"
    Load  "extmod"
    Load  "glx"
EndSection

Section "InputDevice"
    Identifier  "Keyboard0"
    Driver      "kbd"
EndSection

Section "InputDevice"
    Identifier  "Mouse0"
    Driver      "mouse"
    Option        "Protocol" "auto"
    Option        "Device" "/dev/input/mice"
    Option        "ZAxisMapping" "4 5 6 7"
EndSection

Section "Monitor"
    Identifier   "Monitor0"
    VendorName   "Monitor Vendor"
    ModelName    "Monitor Model"
EndSection

Section "Device"
        ### Available Driver options are:-
        ### Values: <i>: integer, <f>: float, <bool>: "True"/"False",
        ### <string>: "String", <freq>: "<f> Hz/kHz/MHz",
        ### <percent>: "<f>%"
        ### [arg]: arg optional
        #Option     "NoAccel"                # [<bool>]
        #Option     "SWcursor"               # [<bool>]
        #Option     "ColorKey"               # <i>
        #Option     "CacheLines"             # <i>
        #Option     "Dac6Bit"                # [<bool>]
        #Option     "DRI"                    # [<bool>]
        #Option     "NoDDC"                  # [<bool>]
        #Option     "ShowCache"              # [<bool>]
        #Option     "XvMCSurfaces"           # <i>
        #Option     "PageFlip"               # [<bool>]
    Identifier  "Card0"
    Driver      "intel"
    BusID       "PCI:0:2:0"
EndSection

Section "Screen"
    Identifier "Screen0"
    Device     "Card0"
    Monitor    "Monitor0"
    SubSection "Display"
        Viewport   0 0
        Depth     1
    EndSubSection
    SubSection "Display"
        Viewport   0 0
        Depth     4
    EndSubSection
    SubSection "Display"
        Viewport   0 0
        Depth     8
    EndSubSection
    SubSection "Display"
        Viewport   0 0
        Depth     15
    EndSubSection
    SubSection "Display"
        Viewport   0 0
        Depth     16
    EndSubSection
    SubSection "Display"
        Viewport   0 0
        Depth     24
    EndSubSection
EndSection


```I had all my screen resolutions at 10.04 LT but they are gone at 10.10. You can see above that I have onboard Intel video. My monitor is a 19" NEC MultiSync 90. Both computer and monitor are about 6 years old but still work good, especially with Linux. Hopefully I can get my resolutions back.

Thanks

---

### Post by realzippy on 2011-01-12
Not sure about the module section,but think just try it in this vanilla status.

```
gksudo gedit /etc/X11/xorg.conf
```

copy file's content,close saving changes.

---

### Post by mtdave on 2011-01-12
Ok, I added the /etc/X11/xorg.conf file with the contents of xorg.conf.net. Then rebooted.

I got an error on restart to do with the clock display.

Now what?

---

### Post by realzippy on 2011-01-12
error?Means you cannot boot?
So boot in recovery mode,drop to shell,log in,delete xorg.conf:

```
sudo rm /etc/X11/xorg.conf
sudo reboot
```

---

### Post by mtdave on 2011-01-12
I just rebooted again and it rebooted fine. The /etc/X11/xorg.conf is still in place.

For some reason it threw an error and the Gnome time and data did not display on the prior boot. All is fine now.

---

### Post by realzippy on 2011-01-12
..all fine?
Means just booting or monitor resolutions available?

---

### Post by mtdave on 2011-01-12
It is booting fine now in Ubuntu. I still have the same limited list of monitor resolutions. It is currently set at 1024x768 60hz. There is one higher but it is 16:9 ratio 1360x768 which isn't useful for me.

When I boot to Windows XP I have choices all the way up to 2048x1536. I have Windows set to 1400x1050 32bit color, 60hz which is about what I would like for Ubuntu.

---

### Post by realzippy on 2011-01-12
So you have to add Hsync Vsync values to the monitor section.
You have those for your NEC?

---

### Post by realzippy on 2011-01-12
Edit the monitor section,add H/Vsync.


```
Section "Monitor"
    Identifier   "Monitor0"
    VendorName   "Monitor Vendor"
    ModelName    "Monitor Model"
    HorizSync       28.0 - 83.0    #Vanilla values,do NOT use any higher
    VertRefresh     56.0 - 75.0    #resolution as formerly offered.
EndSection


```

---

### Post by mtdave on 2011-01-12
I actually found the manual for the thing (NEC MultiSync 90 CRT Monitor) in my files. It says:

Horizontal sync: Positive/Negative
Vertical sync: Positive/Negative

They recommend 1280x1024 55 to 90 hz or 1600x1200 55 to 76 hz

---

### Post by realzippy on 2011-01-12
Aaah,CRT.
No Hsync /Vrefresh range values?
Similar to
    HorizSync       28.0 - 83.0    
    VertRefresh     56.0 - 75.0    
?

---

### Post by mtdave on 2011-01-12
Ahh, It says under Syncronization Range:

Horizontal: 31kHz to 96 kHz
Vertical: 55 kHz to 160 kHz

Should I use this?

HorizSync 31.0 - 96.0    
    VertRefresh 55.0 - 160.0

Then what? Save /etc/X11/xorg.conf and Reboot?

---

### Post by realzippy on 2011-01-12
Yes.

```
Section "Monitor"
    Identifier   "Monitor0"
    VendorName   "Monitor Vendor"
    ModelName    "Monitor Model"
    HorizSync       31.0 - 96.0    
    VertRefresh     55.0 - 160.0   
EndSection
```

---

### Post by mtdave on 2011-01-12
Realzippy, thanks a ton! That did it!

Dave

---

### Post by realzippy on 2011-01-12
Ok.
So you are a successful threadnapper.  ;-)


@jimmys_

Back tomorrow..

---

### Post by mtdave on 2011-01-12
Yes, and I can't believe I had the monitor manual in my file cabinet. I should go buy a lottery ticket.

---

### Post by realzippy on 2011-01-13
@jimmys_

You should do what suggested in post #9.
Then get your Hsync/Vrefresh values from your monitor's manual,
and add them to the xorg.conf "monitor section" described in post #22..

---

