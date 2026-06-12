---
title: "How To Install A Generic KVM Switch (ie ones off e bay) UBUNTU 11.10 FULL resolutions"
date: 2012-04-23
forum: General Help
---

### Post by studiofreak on 2012-04-23
How to install a generic KVM switch box (ie like ones from e bay)

(take out all asterisks and replace with your own text)

First
-----

Insatall with NO KVM attached, and all your graphics cards resolutions will be available.


in terminal:
-----------

cvt *and your desired resolution*

ie

cvt 1680 1050

and note the output of the "modeline*

xrandr --newmode *Modeline*

ie 

xrandr --newmode "1680x1050_60.00"  146.25  1680 1784 1960 2240  1050 1053 1059 1089 -hsync +vsync

so everytihng with the quote marks around the monitor resolution up to the end of +vsync, the WHOLE line, into the terminal.

then:

xrandr --addmode VGA1 *resolution+frequency*

ie

xrandr --addmode VGA1 1680x1050_60.00 

now this will show up in the "displays" options in "system" ie system>displays

to add this new resolution if this wont take effect:

xrandr --output VGA1 --mode *resolution+frequency*

xrandr --output VGA1 --mode 1680x1050_60.00


Note: cvt every resolution your video card supports and take note of the *Modeline* and save it for the next step!

ie

xrandr returns the following:

VGA1 connected 1680x1050+0+0 (normal left inverted right x axis y axis) 477mm x 268mm
   1920x1080      60.0 +
   1680x1050      60.0* 
   1280x1024      75.0     60.0  
   1152x864       75.0  
   1024x768       75.1     60.0  
   800x600        75.0     60.3  
   640x480        75.0     60.0  
   720x400        70.1  


cvt 1920 1080

cvt *leaving out the one you want as you already have the Modline info*

cvt 1280 1024

cvt 1152 864

cvt 1024 768

cvt 800 600

cvt 640 480

cvt 720 400

THIS WILL NOT BE PERMINENT UNTIL YOU DO THIS:

We need to add the resolution to /etc/X11/xorg.conf

sudo gedit /etc/X11/xorg.conf

The xorg.conf will show the output like this: (if it doesnt and terminal returns that it doesn't exit then make a text file called xorg·conf and place it on your desk top as you build its code)

-------------------------------------------------------------------------------------------------------------- /* do not put the this line in */

Section "Monitor"
    Identifier    "Monitor0"
    Modeline "1280x800_60.00"   83.50  1280 1352 1480 1680  800 803 809 831 -hsync +vsync
    Modeline "1368x768_60.00"   85.25  1368 1440 1576 1784  768 771 781 798 -hsync +vsync
    Modeline "1024x768_60.00"   63.50  1024 1072 1176 1328  768 771 775 798 -hsync +vsync
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Card0"
    Monitor        "Monitor0"
    SubSection "Display"
        Modes      "1280x800_60.00" "1368x768_60.00" "1024x768_60.00"
    EndSubSection
EndSection

Section "Device"
    Identifier    "Card0"
    Driver        ""
EndSection

Add the new Modeline and resolution, for the “Driver” in the “Section Device” I just simply type “Intel” (because I’m using intel standard graphic card), if you are using Nvidia just simply type “nvidia”. The output is like:

-------------------------------------------------------------------------------------------------------------- /* do not put the this line in */

Section "Monitor"
    Identifier    "Monitor0"
    Modeline "1920x1080_60.00"  173.00  1920 2048 2248 2576  1080 1083 1088 1120 -hsync +vsync
    Modeline "1680x1050_60.00"  146.25  1680 1784 1960 2240  1050 1053 1059 1089 -hsync +vsync
    Modeline "1280x1024_60.00"  109.00  1280 1368 1496 1712  1024 1027 1034 1063 -hsync +vsync
    Modeline "1152x864_60.00"   81.75  1152 1216 1336 1520  864 867 871 897 -hsync +vsync
    Modeline "1024x768_60.00"   63.50  1024 1072 1176 1328  768 771 775 798 -hsync +vsync
    Modeline "800x600_60.00"   38.25  800 832 912 1024  600 603 607 624 -hsync +vsync
    Modeline "640x480_60.00"   23.75  640 664 720 800  480 483 487 500 -hsync +vsync
    Modeline "720x400_60.00"   22.25  720 744 808 896  400 403 413 417 -hsync +vsync

EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Card0"
    Monitor        "Monitor0"
    SubSection "Display"
        Modes      "1920x1080_60.00" "1680x1050_60.00" "1280x1024_60.00" "1152x864_60.00" "1024x768_60.00" "800x600_60.00" "640x480_60.00" "720x400_60.00"
    EndSubSection
EndSection

Section "Device"
    Identifier    "Card0"
    Driver        "intel"
EndSection

---------------------------------------------------------------------------------------------------------------  /* do not put the this line in */

Either safe the file or if you are making your own then input: nautilus

into the terminal, and navigate through the file system to: /etc/X11

and copy over the file you have made xorg.config that's on your desk top.

Restart and see the resolution setting is now permanent (if it hasnt set the resolution, then you can go into system>displays and choose the resolution you want! You might also want to do an auto set up on your actual monitor also!)

in short, NEVER install linux with a generic KVM switch box installed and then follow these instructions and you will have it working!

I have :-)

Have fun!

*Studio Freak*

p.s. any mistakes, I apologise, I will put them right and try and help best I can in between being as busy as I am.

BUT! I am using this right now and this DOES 100% actually work.

---

### Post by studiofreak on 2012-04-24
*update*

Once you shut down the PC and restart WITH the KVM attached, then ALL YOUR MONITORS CAPABLE resolutions WILL be available in system>displays.

):P

and then next time you restart or shut down and boot up again, your KVM and monitor will work perfectly.

Thanks,

Studio Freak

---

