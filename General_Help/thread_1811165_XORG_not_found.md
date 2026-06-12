---
title: "XORG not found"
date: 2011-07-24
forum: General Help
---

### Post by MrChainBlueLightnin on 2011-07-24
I just installed ubuntu 10.04 on an HP with a viewsonic VE175b monitor.  When I type sudo Xorg -configure to add my monitor I get this:
Fatal server error:
Server is already active for display 0
    If this server is no longer running, remove /tmp/.X0-lock
    and start again.


Please consult the The X.Org Foundation support 
     at [http://wiki.x.org](http://wiki.x.org)
 for help. 

 ddxSigGiveUp: Closing log


Can someone help me repair the XORG?

---

### Post by realzippy on 2011-07-24
..you have to stop running Xserver before running command.
Means,eg. press
Ctrl+Alt+F2
log in at shell,then:
```
sudo service gdm stop
```
..then you can create a new xorg.conf with *Xorg -configure*

Edit:

btw, doubt it solves a monitor related problem...

---

### Post by bodhi.zazen on 2011-07-24
> **MrChainBlueLightnin said:**
> I just installed ubuntu 10.04 on an HP with a viewsonic VE175b monitor.  When I type sudo Xorg -configure to add my monitor I get this:
Fatal server error:
Server is already active for display 0
    If this server is no longer running, remove /tmp/.X0-lock
    and start again.


Please consult the The X.Org Foundation support 
     at [http://wiki.x.org](http://wiki.x.org)
 for help. 

 ddxSigGiveUp: Closing log


Can someone help me repair the XORG?

xorg.conf is depreciated, use xrandr

[http://blog.bodhizazen.net/linux/use-xrandr-to-set-a-screen-resolution/](http://blog.bodhizazen.net/linux/use-xrandr-to-set-a-screen-resolution/)

If xrandr does not set your resolution, what video card do you have ? You likely need to install the drivers.

---

### Post by MrChainBlueLightnin on 2011-07-24
I have a Matrox MGA 2064W video card.  I have not found a driver for it.  There are none when I go to sys admin -->hardware drivers

---

### Post by realzippy on 2011-07-24
There is no additional driver you can install..
*xserver-xorg-video-mga*
should be installed already.There is a tool:
*matroxset*
you can install (Read about it in SoftwareCenter or Synaptic).
Doubt it helps but it won't do any harm...

Anyway,run -as suggested- :

```
xrandr -q

```

to see available resolutions.

---

### Post by MrChainBlueLightnin on 2011-07-24
so then is it possible to adjust reso. above 832?  xrandr -q says that is as high as it gets:
Screen 0: minimum 400 x 300, current 800 x 600, maximum 840 x 624
default connected 800x600+0+0 0mm x 0mm
   832x624        75.0  
   800x600        75.0*    72.0     60.0     56.0     65.0  
   840x525        75.0     70.0     60.0  
   700x525        75.0     70.0     60.0  
   640x512        75.0     60.0  
   720x450        60.0  
   640x480        75.0     73.0     67.0     60.0  
   720x400        70.0  
   680x384        60.0  
   576x432        75.0     70.0     60.0  
   512x384        75.0     70.0     60.0  
   416x312        75.0  
   400x300        75.0     72.0     60.0     56.0

---

### Post by realzippy on 2011-07-24
See
[https://wiki.archlinux.org/index.php/Xrandr](https://wiki.archlinux.org/index.php/Xrandr)
section "adding undetected resolutions"...
guess you need 1280 x 1024
Feel free to ask ...

---

### Post by MrChainBlueLightnin on 2011-07-24
I keep getting this:
 xrandr --addmode VGA-1 1024x768
xrandr: cannot find output "VGA-1"

It says my max display reso is 1280x1024

---

### Post by MrChainBlueLightnin on 2011-07-24
I now show this:
xrandr -q
Screen 0: minimum 400 x 300, current 800 x 600, maximum 840 x 624
default connected 800x600+0+0 0mm x 0mm
   832x624        75.0  
   800x600        75.0*    72.0     60.0     56.0     65.0  
   840x525        75.0     70.0     60.0  
   700x525        75.0     70.0     60.0  
   640x512        75.0     60.0  
   720x450        60.0  
   640x480        75.0     73.0     67.0     60.0  
   720x400        70.0  
   680x384        60.0  
   576x432        75.0     70.0     60.0  
   512x384        75.0     70.0     60.0  
   416x312        75.0  
   400x300        75.0     72.0     60.0     56.0  
  1024x768_60.00 (0x132)   63.0MHz
        h: width  1024 start 1072 end 1176 total 1328 skew    0 clock   47.4KHz
        v: height  768 start  771 end  775 total  798           clock   59.4Hz

---

### Post by realzippy on 2011-07-24
..according to your xrandr output it had to be:

```
xrandr --addmode default 1024x768
```

---

### Post by realzippy on 2011-07-24
Since we are cross-posting,I suggest to
wait a minute (or 2) before this gets confusing..

---

### Post by MrChainBlueLightnin on 2011-07-24
I tried VGA and VGA-1 but default is the only one that shows up.  However, even when I used ubuntu 9.04 I my monitor showed up as default as well.  Won't these changes be temporary?  Do I not have to change xorg to make perm changes?

---

### Post by realzippy on 2011-07-24
yes.It is
*default*
not VGA-1 or whatever.Just use *default* instead.
Yes,this would be temporarely,as mentioned in bodhi's
blog,this had to be edited to startup programs eg.
An *xorg.conf* would also do this...:P (post #2;you did not react)

---

### Post by MrChainBlueLightnin on 2011-07-24
you lost me.  why are we bothering with xrandr????????????  why not get xorg where it will open and i can save it?  I tried your code from post 2 "sudo service gdm stop".  It restarted my comp and put me on the black boot up screen where it locked up and I had to power off.  This did not help me create a xorg.

---

### Post by realzippy on 2011-07-24
Because it might have worked with a little less effort.
So run
```
Xorg -configure
```
 after you stopped the Xserver as suggested in post #2.
Then we had to edit the file a little,so post
*xorg.conf.new* you have created.


BTW,
I do not have a matrox card.(Nearly nobody I guess).I cannot
promise that it will work...

---

### Post by realzippy on 2011-07-24
> **MrChainBlueLightnin said:**
> "sudo service gdm stop".  It restarted my comp ...

Then start in recovery mode,drop to shell,log in,then run
```
Xorg -configure
```

---

### Post by MrChainBlueLightnin on 2011-07-24
LOL!  I know, I need to get a new video card.  Here is my new xorg, I made some changes based on what we have discussed, but they may be wrong.

Section "ServerLayout"
    Identifier     "X.org Configured"
    Screen      0  "Screen0" 0 0
    Screen      1  "Screen1" RightOf "Screen0"
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
    Load  "dbe"
    Load  "dri2"
    Load  "glx"
    Load  "extmod"
    Load  "dri"
    Load  "record"
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
    #DisplaySize      340   270    # mm
    Identifier   "Monitor0"
    VendorName   "VSC"
    ModelName    "VE175b-2"
    HorizSync    30.0 - 82.0
    VertRefresh  50.0 - 75.0
    Option        "DPMS"
Modeline "1024x768_75.00"   82.00  1024 1088 1192 1360  768 771 775 805 -hsync +vsync
EndSection

Section "Monitor"
    Identifier   "Monitor1"
    VendorName   "Monitor Vendor"
    ModelName    "Monitor Model"
EndSection

Section "Device"
        ### Available Driver options are:-
        ### Values: <i>: integer, <f>: float, <bool>: "True"/"False",
        ### <string>: "String", <freq>: "<f> Hz/kHz/MHz"
        ### [arg]: arg optional
        #Option     "NoAccel"                # [<bool>]
        #Option     "AccelMethod"            # <str>
        #Option     "HWCursor"               # [<bool>]
        #Option     "SWCursor"               # [<bool>]
        #Option     "ShadowFB"               # [<bool>]
        #Option     "Rotate"                 # [<str>]
        #Option     "UseBIOS"                # [<bool>]
        #Option     "LCDClock"               # <freq>
        #Option     "ShadowStatus"           # [<bool>]
        #Option     "CrtOnly"                # [<bool>]
        #Option     "TvOn"                   # [<bool>]
        #Option     "PAL"                    # [<bool>]
        #Option     "ForceInit"              # [<bool>]
        #Option     "Overlay"                # [<str>]
        #Option     "TransparencyKey"        # [<str>]
        #Option     "ForceInit"              # [<bool>]
        #Option     "DisableXVMC"            # [<bool>]
        #Option     "DisableTile"            # [<bool>]
        #Option     "DisableCOB"             # [<bool>]
        #Option     "BCIforXv"               # [<bool>]
        #Option     "DVI"                    # [<bool>]
        #Option     "IgnoreEDID"             # [<bool>]
        #Option     "BusType"                # [<str>]
        #Option     "DmaType"                # [<str>]
        #Option     "DmaMode"                # [<str>]
        #Option     "AGPMode"                # <i>
        #Option     "AGPSize"                # <i>
        #Option     "DRI"                    # [<bool>]
        #Option     "AGPforXv"               # [<bool>]
    Identifier  "Card0"
    Driver      "savage"
    VendorName  "S3 Inc."
    BoardName   "ProSavage KM133"
    BusID       "PCI:1:0:0"
EndSection

Section "Device"
        ### Available Driver options are:-
        ### Values: <i>: integer, <f>: float, <bool>: "True"/"False",
        ### <string>: "String", <freq>: "<f> Hz/kHz/MHz"
        ### [arg]: arg optional
        #Option     "SWcursor"               # [<bool>]
        #Option     "HWcursor"               # [<bool>]
        #Option     "PciRetry"               # [<bool>]
        #Option     "SyncOnGreen"            # [<bool>]
        #Option     "NoAccel"                # [<bool>]
        #Option     "ShowCache"              # [<bool>]
        #Option     "MGASDRAM"               # [<bool>]
        #Option     "ShadowFB"               # [<bool>]
        #Option     "UseFBDev"               # [<bool>]
        #Option     "ColorKey"               # <i>
        #Option     "SetMclk"                # <freq>
        #Option     "OverclockMem"           # [<bool>]
        #Option     "VideoKey"               # <i>
        #Option     "Rotate"                 # [<str>]
        #Option     "TexturedVideo"          # [<bool>]
        #Option     "Crtc2Half"              # [<bool>]
        #Option     "Crtc2Ram"               # <i>
        #Option     "Int10"                  # [<bool>]
        #Option     "AGPMode"                # <i>
        #Option     "AGPSize"                # <i>
        #Option     "DigitalScreen1"         # [<bool>]
        #Option     "DigitalScreen2"         # [<bool>]
        #Option     "TV"                     # [<bool>]
        #Option     "TVStandard"             # [<str>]
        #Option     "CableType"              # [<str>]
        #Option     "NoHal"                  # [<bool>]
        #Option     "SwappedHead"            # [<bool>]
        #Option     "DRI"                    # [<bool>]
        #Option     "MergedFB"               # [<bool>]
        #Option     "Monitor2HSync"          # [<str>]
        #Option     "Monitor2VRefresh"       # [<str>]
        #Option     "Monitor2Position"       # [<str>]
        #Option     "MetaModes"              # [<str>]
        #Option     "OldDmaInit"             # [<bool>]
        #Option     "ForcePciDma"            # [<bool>]
        #Option     "AccelMethod"            # [<str>]
        #Option     "KVM"                    # [<bool>]
    Identifier  "Card1"
    Driver      "mga"
    VendorName  "Matrox Graphics, Inc."
    BoardName   "MGA 2064W [Millennium]"
    BusID       "PCI:0:13:0"
EndSection

Section "Screen"
    Identifier "Screen0"
    Device     "Device0"
    Monitor    "Monitor0"
        DefaultDepth 16
    SubSection "Display"
        Depth 24
                Modes "1024x768"
    EndSubSection
EndSection

Section "Screen"
    Identifier "Screen1"
    Device     "Card1"
    Monitor    "Monitor1"
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

---

### Post by realzippy on 2011-07-24
Ehm,
where is the device section with the "SIS" graphics from !!!!!!!!!?????**?**
Can you please post the original,unmodified 
xorg.conf.new ?

Why not 1280x1024 ?
Isn't that your monitor's native?

---

### Post by MrChainBlueLightnin on 2011-07-24
I deleted most of the screen (0) section and added the modeline to the monitor section

---

### Post by bodhi.zazen on 2011-07-24
> **MrChainBlueLightnin said:**
> you lost me.  why are we bothering with xrandr????????????  why not get xorg where it will open and i can save it?  I tried your code from post 2 "sudo service gdm stop".  It restarted my comp and put me on the black boot up screen where it locked up and I had to power off.  This did not help me create a xorg.

As I explained in my first post, xorg.conf is depreciated, and thus the preferred tool is now xrandr.

If xrandr does not show your desired resolution sometimes you can write an xorg.conf, and sometimes use some tricks, and sometimes not.

Most of what you are trying to do is depreciated.

Try using the following lines in xrog.conf (and remove the rest)

```
Section "Screen"
    Identifier "Screen0"
    Device     "Card0"
    Monitor    "Monitor0"
    DefaultDepth 16
    SubSection "Display"
        Viewport   0 0
	Depth     16
        Modes "1024x768"
    EndSubSection
EndSection
```

Again, use only those lines, log out and back in, and then post the output of xrandr again ;)

---

### Post by MrChainBlueLightnin on 2011-07-24
Screen 0: minimum 400 x 300, current 800 x 600, maximum 840 x 624
default connected 800x600+0+0 0mm x 0mm
   832x624        75.0  
   800x600        75.0*    72.0     60.0     56.0     65.0  
   840x525        75.0     70.0     60.0  
   700x525        75.0     70.0     60.0  
   640x512        75.0     60.0  
   720x450        60.0  
   640x480        75.0     73.0     67.0     60.0  
   720x400        70.0  
   680x384        60.0  
   576x432        75.0     70.0     60.0  
   512x384        75.0     70.0     60.0  
   416x312        75.0  
   400x300        75.0     72.0     60.0     56.0

---

### Post by bodhi.zazen on 2011-07-24
Although it should not make a difference, you can try restarting gdm and/ore rebooting.

I am not sure I can get that card to perform better then with that xorg.conf I gave you.

---

### Post by realzippy on 2011-07-24
> **bodhi.zazen said:**
> As I explained in my first post, xorg.conf is depreciated, and thus the preferred tool is now xrandr.


In this case you **need** an xorg.conf.
xrandr gets none/wrong monitor data.
Or *how* would you set 16 bit depth with xrandr (maybe neccessary for matrox indeed) or increase
the vanilla 33 Hsync X uses (..would bet Xorg.0.log shows)  without
Monitor Section
using xrandr?

I would suggest to add a valid Hsync/Vrefresh values to the xorg.conf you have suggested,like
```

Section "Monitor"
	Identifier	"Configured Monitor"
        HorizSync   30.0 - 82.0
        VertRefresh 50.0 - 75.0
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
        DefaultDepth   16
        SubSection  "Display"
        Viewport   0 0
	Depth     16
        Modes "1024x768"
        EndSubSection
EndSection
```

but am concerned that problem goes deeper...did not ask for fun
why there is a "SIS" device section beneath the "matrox/mga" device section.
Guess running onboard graphics... ?

---

### Post by realzippy on 2011-07-24
@BlueLight
 
edited post above,can you test suggested as /etc/X11/xorg.conf?

If no success,(very likely),can you show the unmodified xorg.conf.new?

Edit:
And could you run 

```
lspci |grep VGA
```

 (I am puzzled because of the "SIS" device section)

Edit2:

OMG,it is 1:33 AM.
Now this gets interesting,but have to sleep.Back tomorrow,sorry,real life calling.

---

### Post by MrChainBlueLightnin on 2011-07-24
Here is the code output

00:0d.0 VGA compatible controller: Matrox Graphics, Inc. MGA 2064W [Millennium] (rev 01)
01:00.0 VGA compatible controller: S3 Inc. ProSavage KM133 (rev 03)

Rebooting now with changes to xorg.conf

---

### Post by MrChainBlueLightnin on 2011-07-24
No luck with putting xorg.conf.new into xorg.conf

---

### Post by MrChainBlueLightnin on 2011-07-24
which one should i try to modify? which one affects my display settings, xorg.conf or xorg.conf.new?

---

### Post by realzippy on 2011-07-25
Morning. ;)

> **MrChainBlueLightnin said:**
> Here is the code output

00:0d.0 VGA compatible controller: Matrox Graphics, Inc. MGA 2064W [Millennium] (rev 01)
01:00.0 VGA compatible controller: S3 Inc. ProSavage KM133 (rev 03)


As you can see from the output,there are indeed 2 graphic devices:
1.Your matrox card
2.A SIS onboard graphics chip.

You should open your BIOS to see if there is kinda switch to disable
the onboard graphics before we go on editing your xorg.conf....

**Edit:**

Just realising that your  MGA 2064W device has **4** MB RAM.
!
You should use the onboard graphics.

---

### Post by MrChainBlueLightnin on 2011-07-25
sorry it took so long to get back.  i think i can post back and forth from work though from now on.  about to try the disable option for one of the vid cards.

---

### Post by MrChainBlueLightnin on 2011-07-25
REAL ZIPPY YOU ARE A GENIUS!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!  I took out the Matrox and booted up with onboard video and voila, I have resolution options all the way up to 1280 x 1024.  Bodhi Zazen, give this guy some kind of bump.

---

### Post by realzippy on 2011-07-26
No genius,more an idiot,because I *should* have asked you to run
```
lspci |grep VGA
```
in my very 1rst post.If I did,it would have saved you from messing around with xorg.conf/xrandr ...
Anyway,glad you solved your problem,sorry for the inconvenience.
Would you please mark thread as "solved" (Threadtools) !?

Have fun!

---

### Post by realzippy on 2011-08-22
Just cleaning up my subscribed threads.
Please set thread as solved (ThreadTools)...thanks

---

