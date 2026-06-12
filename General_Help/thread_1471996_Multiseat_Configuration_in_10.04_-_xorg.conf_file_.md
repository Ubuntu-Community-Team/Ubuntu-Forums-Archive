---
title: "Multiseat Configuration in 10.04 - xorg.conf file posted, need opinions/ideas."
date: 2010-05-04
forum: General Help
---

### Post by sir_nasty on 2010-05-04
The title says it all.  Anyone have any luck with setting up a Multiseat configuration in 10.04?  I beat my head against the wall all day today.  I tried a variety of things but here's my xorg.conf file (with this file I get one working monitor and one black screen).  It's an nvidia Geforce 7300 - Let me know if anything stands out!  Thanks in advance!

```



Section "ServerFlags"

        # Even if mouse detection fails, X will start
    Option         "AllowMouseOpenFail" "yes"
        # VT switching is disabled
    Option         "DontVTSwitch" "yes"
        # X restart (Ctrl+Alt+Backspace) is disabled
    Option         "DontZap" "yes"
EndSection

Section "InputDevice"

    # generated from default
    Identifier     "Mouse0"
    Driver         "mouse"
    Option         "Protocol" "auto"
    Option         "Device" "/dev/input/event7"
    Option         "Emulate3Buttons" "no"
    Option         "ZAxisMapping" "4 5"
EndSection

Section "InputDevice"

    # generated from default
    Identifier     "Keyboard0"
    Driver         "kbd"
    Option   	   "Device" "/dev/input/event6"
EndSection


Section "InputDevice"

    # generated from default
    Identifier     "Mouse1"
    Driver         "mouse"
    Option         "Protocol" "auto"
    Option         "Device" "/dev/input/event5"
    Option         "Emulate3Buttons" "no"
    Option         "ZAxisMapping" "4 5"
EndSection

Section "InputDevice"

    # generated from default
    Identifier     "Keyboard1"
    Driver         "kbd"
    Option   	   "Device" "/dev/input/event3"
EndSection
Section "Monitor"

    # HorizSync source: edid, VertRefresh source: edid
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "DELL 2007WFP"
    HorizSync       30.0 - 83.0
    VertRefresh     56.0 - 76.0
EndSection

Section "Monitor"

    # HorizSync source: edid, VertRefresh source: edid
    Identifier     "Monitor1"
    VendorName     "Unknown"
    ModelName      "Acer H213H"
    HorizSync       31.0 - 83.0
    VertRefresh     56.0 - 76.0
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 7300 GT"
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection

Section "Screen"
   Identifier	   "Screen1"
   Device	   "Device0"
   Monitor	   "Monitor1"
   DefaultDepth    24
   SubSection      "Display"
	Depth	   24
   EndSubSection
EndSection

Section "ServerLayout"
    Identifier "Layout0"
    Screen 0 "Screen0" 0 0
    InputDevice "mouse0" "CorePointer"
    InputDevice "keyboard0" "CoreKeyboard"
    Option         "Xinerama" "0"
EndSection

Section "ServerLayout"
    Identifier "Layout1"
    Screen 1 "Screen1" RightOf "Screen0"
    InputDevice "mouse1"
    InputDevice "keyboard1" 
    Option         "Xinerama" "1"
EndSection


```

---

### Post by altavatar on 2010-05-05
I've been trying to get this to work as well. I've had limited success with two ATI 4350s. My xorg.conf looks similar and I start X on the console under two different user accounts with:

# I've tried starting the first xsession with -sharevts, but then I can't CTRL+ALT+F2 to a new console in order to start the 2nd xsession
startx -- :0 -nolisten tcp -layout workstation

startx -- :1 -nolisten tcp -sharevts -layout tv

This works for a very short while, then I get visual artifacting and the computer hangs and has to be hard-rebooted. Not sure if this indicates that I have a bad card or bad drivers (I've been using the fglrx drivers, but I will try the radeon ones too).

Also, I haven't been able to get gdm to start both Xsessions properly. I tried adding the following to /etc/gdm/custom.conf, but that hasn't worked:

```

[servers]
0=Standard0
1=Standard1

[server-Standard0]
name=Standard server 0
command=/usr/bin/Xorg -nolisten tcp -layout workstation -sharevts -isolateDevice PCI:1:0:0

[server-Standard1]
name=Standard server 1
command=/usr/bin/Xorg -nolisten tcp -layout tv -sharevts -isolateDevice PCI:5:0:0

```

---

### Post by sir_nasty on 2010-05-07
at this point I'm either going to dual boot with 9.10 for multi user and 10.04 for single or just say forget it.... I can't figure out what's going on and until someone else has some kickin ideas I'm done lol

I'm going to go play video games and lick my wounds.... lol

---

### Post by altavatar on 2010-05-07
I've made a little progress:

I switched out my 2 ATI Radeons for 2 Nvidia 210s with much better results - no more crashes and hangs!

i couldn't get GDM 2.30 working, so I downgraded to GDM 2.20. Even then, I can't boot into GDM as it complains that it couldn't detect my video configuration and then I have to exit to a console. The logs show X starting, then "giving up" without any errors, so I don't know what's going on. Anyway, I got around that by starting in a text-mode console and running the following as root: 

# gdm start

Here's the relevant section from my gdm.conf:

```

[servers]
0=Standard0
1=Standard1

[server-Standard0]
name=Standard server 0
command=/usr/bin/Xorg -nolisten tcp -novtswitch -layout workstation -isolateDevice PCI:1:0:0

[server-Standard1]
name=Standard server 1
command=/usr/bin/Xorg -nolisten tcp -novtswitch -sharevts -layout tv -isolateDevice PCI:5:0:0 

```[

Here's my xorg.conf:

```

Section "ServerLayout"
    Identifier     "workstation"
    Screen         "WorkstationScreen" 0 0
    InputDevice    "WorkstationKeyboard0" "CoreKeyboard"
    InputDevice    "WorkstationMouse0" "CorePointer"
    Option         "Xinerama" "0"
    Option         "AutoEnableDevices" "false"
    Option         "AutoAddDevices" "false"
EndSection

Section "ServerLayout"
    Identifier     "tv"
    Screen         "TVScreen" 0 0
    InputDevice    "TVKeyboard0" "CoreKeyboard"
    InputDevice    "TVMouse0" "CorePointer"
    Option         "Xinerama" "0"
    Option         "AutoEnableDevices" "false"
    Option         "AutoAddDevices" "false"
EndSection

Section "InputDevice"
    Identifier     "WorkstationKeyboard0"
    Option         "Device" "/dev/input/event4"
    Driver         "evdev"
    Option         "XkbLayout" "us"
    Option         "IgnoreRelativeAxis" "true"
    Option         "GrabDevice" "true"
EndSection

Section "InputDevice"
    Identifier     "WorkstationMouse0"
    Driver         "mouse"
    Option         "Protocol" "ExplorerPS/2"
    Option         "Device" "/dev/input/mouse1"
EndSection

Section "InputDevice"
    Identifier     "TVKeyboard0"
    Driver         "evdev"
    Option         "Device" "/dev/input/event7"
    Option         "XkbLayout" "us"
    Option         "XkbRules" "xorg"
    Option         "XkbModel" "pc104"
    Option         "GrabDevice" "true"
EndSection

Section "InputDevice"
    Identifier     "TVMouse0"
    Driver         "mouse"
    Option         "Protocol" "ExplorerPS/2"
    Option         "Device" "/dev/input/mouse2"
EndSection

Section "Monitor"
    # HorizSync source: edid, VertRefresh source: edid
    Identifier     "Dell"
    VendorName     "Unknown"
    ModelName      "DELL SP1908FP"
    HorizSync       30.0 - 81.0
    VertRefresh     56.0 - 76.0
    Option         "DPMS"
EndSection

Section "Monitor"
    # HorizSync source: edid, VertRefresh source: edid
    Identifier     "Samsung"
    VendorName     "Unknown"
    ModelName      "SAMSUNG"
    HorizSync       30.0 - 61.0
    VertRefresh     60.0 - 75.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "nvidia0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 210"
    BusID          "PCI:1:0:0"
EndSection

Section "Device"
    Identifier     "nvidia1"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 210"
    BusID          "PCI:5:0:0"
EndSection

Section "Screen"
    Identifier     "WorkstationScreen"
    Device         "nvidia0"
    Monitor        "Dell"
    DefaultDepth    24
    Option         "TwinView" "1"
    Option         "TwinViewXineramaInfoOrder" "DFP-0"
    Option         "metamodes" "CRT: nvidia-auto-select +1280+0, DFP: nvidia-auto-select +0+0"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection

Section "Screen"
    Identifier     "TVScreen"
    Device         "nvidia1"
    Monitor        "Samsung"
    DefaultDepth    24
    Option         "TwinView" "0"
    Option         "metamodes" "nvidia-auto-select +0+0"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection

```

Hope that helps!

(I also hope that someone can post a guide to GDM downgrading for 10.04, because it's not completely working for me)

---

### Post by sir_nasty on 2010-05-08
Wow, nice work!  I'm going to tackle this a bit more on Monday.  I'll keep working it a bit as well.  I've been doing a lot of reading but the video display side of linux is one that I feel the most weak in.... Thanks for posting that update, I'll start firing off as much info as I can and perhaps we can work this out.

P.S. I already tried modifying the debian release of userful and got it to install but it wouldn't work quite right for me.... and of course it's not supported in 10.04 lol

---

### Post by altavatar on 2010-05-08
A bit more info:

GDM 2.30 does not support Multiseat. You can, though, patch-in support as mentioned in this thread:

[http://mail.gnome.org/archives/gdm-list/2010-April/msg00003.html](http://mail.gnome.org/archives/gdm-list/2010-April/msg00003.html)

> 
For now, you need to build ConsoleKit and GDM with the multiseat patches yourself for multiseat support.


---

### Post by icyrainz on 2010-05-14
Hi,
I'm pretty new to Ubuntu. I would be grateful to hear some information about the GDM installation and configuration. Is it installed in default ubuntu installation ? And X.Org, is it possible to modify it to work on a Intel driver ?

---

### Post by JedMeister on 2010-05-30
I'm also looking for a way of achieving multiseat on 10.04. I haven't tried anything yet because no one else seems to have got it working from scratch. I'm fairly good at following instructions, but its a waste of time me trying to get it going when no-one else can!

If you're running 32 bit 10.04 then [Userful Multiplier(TM)]("http://www.userful.com/products/userful-multiplier") may be an option for you. The 10 seat trial version is in the multiverse repo. According to [this]("http://packages.ubuntu.com/lucid/userful-multiplier") it has a nag screen which can be removed; either by registering for the free 2 seat license or paying for a 10 seat license. I haven't tried it because I've got 64 bit and am otherwise very happy. I'd be very interested to hear how others go if they try it.

---

### Post by altavatar on 2010-06-08
As I mentioned in my previous post, you can get this working in ubuntu 10.04 by compiling a patched gdm 2.30 (I linked to a related discussion above).

You can also get this working by downgrading to gdm 2.20, which is what I've done.

The latter isn't a great solution, but it works well enough for me, for now. Hopefully the GDM folks will integrate the multiseat patch in 2.32 and release that sometime soon. Or hopefully someone will post a full guide for: compiling patched gdm 2.30, building and installing a custom .DEB.

Also, I found a custom package here:
[https://launchpad.net/~hmb1/+archive/multiseat/+build/1624864](https://launchpad.net/~hmb1/+archive/multiseat/+build/1624864)

Without instructions on how to configure gdm 2.30 with multiseat, I'm hesitant to try. I'm sure that it's possible, but I'm not going to break my working 2.20 installation just to try ;-).

Good luck!

---

### Post by nullchar on 2010-06-14
In case you do not want to install all the -dev packages to compile your own GDM and ConsoleKit, give KDM a try.  I had Multiseat working great in 9.04 Jaunty (both users could activate their seats via Ctrl+Alt+F7,F9,etc). I just now got 10.04 working the same by using KDM instead of GDM.  Of course, I had to modify the server commands.

I added the 10.04 section to this wiki:

[https://help.ubuntu.com/community/MultiseatX](https://help.ubuntu.com/community/MultiseatX)

---

### Post by altavatar on 2010-06-21
This blog was updated with more information on getting a patched gdm 2.30 working with multiseat:
[http://multiseatonlinux.blogspot.com/](http://multiseatonlinux.blogspot.com/)

---

### Post by lsmoker on 2010-08-01
Don't know if anyone is still following this thread other than me, but I have been unable to make MultiseatX work since upgrading to Lucid/10.04 (AMD64). I followed the MultiseatX documentation page and came up with the kdmrc and xorg.conf files listed below. I can only get the first seat (seat0) to come up. I was able to get both cards/displays working simultaneously with Xinerama, so I know that works.

Any ideas?

```
[General]
ConfigVersion=2.4
ConsoleTTYs=tty1,tty2,tty3,tty4,tty5,tty6
PidFile=/var/run/kdm.pid
ReserveServers=:2,:3
ServerVTs=7,9
StaticServers=:0,:1

[Shutdown]
BootManager=None
HaltCmd=/sbin/halt
RebootCmd=/sbin/reboot

[X-*-Core]
AllowNullPasswd=false
AllowRootLogin=false
AllowShutdown=Root
AutoReLogin=true
ClientLogFile=.xsession-errors-%d
Reset=/etc/kde4/kdm/Xreset
Session=/etc/kde4/kdm/Xsession
Setup=/etc/kde4/kdm/Xsetup
Startup=/etc/kde4/kdm/Xstartup

[X-*-Greeter]
AntiAliasing=false
ColorScheme=
FaceSource=AdminOnly
FailFont=Sans Serif,10,-1,5,75,0,0,0,0,0
GUIStyle=
GreetFont=Serif,20,-1,5,50,0,0,0,0,0
GreetString=Welcome to Kubuntu at %n
GreeterPos=50,50
HiddenUsers=
Language=en_US
LogoArea=Logo
LogoPixmap=/usr/share/kde4/apps/kdm/pics/kdelogo.png
MaxShowUID=29999
MinShowUID=1000
Preloader=/usr/bin/preloadkde
SelectedUsers=
ShowUsers=NotHidden
SortUsers=true
StdFont=Sans Serif,10,-1,5,50,0,0,0,0,0
Theme=/usr/share/kde4/apps/kdm/themes/ethais
UseBackground=true
UseTheme=true
UserCompletion=false
UserList=true

[X-:*-Core]
AllowNullPasswd=true
AllowShutdown=All
NoPassEnable=false
NoPassUsers=
ServerArgsLocal=-nr -nolisten tcp -logverbose 6
ServerCmd=/usr/bin/X

[X-:*-Greeter]
AllowClose=true
#DefaultUser=cjls
#FocusPasswd=true
LoginMode=DefaultLocal
PreselectUser=Previous

[X-:0-Core]
AutoLoginEnable=false
AutoLoginLocked=false
AutoLoginAgain=false
AutoLoginDelay=0
ClientLogFile=.xsession-errors
ServerVT=7
ServerCmd=/usr/bin/X -sharevts -layout seat0 -isolateDevice PCI:2:0:0 -keeptty

[X-:1-Core]
AutoLoginEnable=false
AutoLoginLocked=false
AutoLoginAgain=false
AutoLoginDelay=0
ClientLogFile=.xsession-errors
ServerVT=9
ServerCmd=/usr/bin/X -sharevts -novtswitch -layout seat1 -isolateDevice PCI:7:0:0 -keeptty

[Xdmcp]
Enable=false
Willing=/etc/kde4/kdm/Xwilling

```

```
Section "ServerLayout"
	Identifier     "seat0"
	Screen      0  "Screen0" 0 0
	InputDevice    "Mouse0" "CorePointer"
	InputDevice    "Keyboard0" "CoreKeyboard"
	Option      "AutoEnableDevices"     "False"
	Option      "AutoAddDevices"        "False"
	Option      "AllowEmptyInput"       "True"
EndSection

Section "ServerLayout"
	Identifier     "seat1"
	Screen      1  "Screen1" 0 0
	InputDevice    "Mouse1" "CorePointer"
	InputDevice    "Keyboard1" "CoreKeyboard"
        Inputdevice    "Keyboard1a" "SendCoreEvents"
	Option      "AutoEnableDevices"     "False"
	Option      "AutoAddDevices"        "False"
	Option      "AllowEmptyInput"       "True"
EndSection

Section "InputDevice"
        Identifier      "Keyboard0"
        Driver          "evdev"
        Option          "Device"        "/dev/input/event4"
EndSection

Section "InputDevice"
        Identifier      "Mouse0"
        Driver          "evdev"
        Option          "Device"        "/dev/input/event8"
EndSection

Section "InputDevice"
        Identifier      "Keyboard1"
        Driver          "evdev"
        Option          "Device"        "/dev/input/event6"
EndSection

Section "InputDevice"
        Identifier      "Keyboard1a"
        Driver          "evdev"
        Option          "Device"        "/dev/input/event7"
EndSection

Section "InputDevice"
        Identifier      "Mouse1"
        Driver          "evdev"
        Option          "Device"        "/dev/input/event5"
EndSection

Section "Monitor"
	Identifier   "Monitor0"
	VendorName   "Monitor Vendor"
	ModelName    "Monitor Model"
        Displaysize     345     195
EndSection

Section "Monitor"
	Identifier   "Monitor1"
	VendorName   "Monitor Vendor"
	ModelName    "Monitor Model"
EndSection

Section "Device"
	Identifier  "Card0"
        Driver  "nvidia"
        Option  "NoLogo"        "True"
        Option  "UseEvents"     "True"
        Option	"XvmcUsesTextures"      "False"  # necessary for color Chromakey OSD)
	BoardName   "NV43 [GeForce 6600 GT]"
	BusID       "PCI:2:0:0"
        Option      "UseEdidDpi"    "FALSE"
        Option  "ModeValidation"    "NoWidthAlignmentCheck"
EndSection

Section "Device"
	Identifier  "Card1"
        Driver  "nvidia"
        Option  "NoLogo"        "True"
        Option  "UseEvents"     "True"
        Option	"XvmcUsesTextures"      "False"  # necessary for color Chromakey OSD)
	BoardName   "G73 [GeForce 7600 GT]"
	BusID       "PCI:7:0:0"
        Option      "CustomEDID"    "DFP-0:/etc/X11/edid.bin"
EndSection

Section "Screen"
	Identifier "Screen0"
	Device     "Card0"
	Monitor    "Monitor0"
	DefaultDepth     24
EndSection

Section "Screen"
	Identifier "Screen1"
	Device     "Card1"
	Monitor    "Monitor1"
	DefaultDepth     24
EndSection

Section "Extensions"
        Option  "Composite"     "Disable"
EndSection

```

---

### Post by JedMeister on 2010-08-04
Hi lsmoker. I'm following this thread but I'm sorry I can't help you (I'm too newb!). I am very keen to see this working as I have a potential future use for it.

Good luck and I hope someone who can help you is a long shortly!

---

### Post by molafish on 2010-08-22
> **nullchar said:**
> I added the 10.04 section to this wiki:

[https://help.ubuntu.com/community/MultiseatX](https://help.ubuntu.com/community/MultiseatX)

nullchar, Can you give any insight on the isolateDevice and novtswitch switches you used for the ServerCmds? I have one video card I'm trying to get working with multiple seats. I left off the isolateDevice switches for obvious reasons, but the two X servers are showing backtraces in their respective logs and I'm not getting past the kubuntu splash screen with 5 filled in dots. Also, I've seen other people put the novtswitch on both X ServerCmds. Why did you only put it on the second?

My first X server is getting very far in the initialization, but the second one crashes almost right away. Additionally, I configured the seats to use VTs 7 and 9, but only the second seat is using what I told it to. The first server is using VT 2 for some reason.

I'm going to post a new thread with all the logs and conf files, but any insight you can give me about those two switches would be most welcome.

---

### Post by Userful on 2010-08-27
> **JedMeister said:**
> I'm also looking for a way of achieving multiseat on 10.04. I haven't tried anything yet because no one else seems to have got it working from scratch. I'm fairly good at following instructions, but its a waste of time me trying to get it going when no-one else can!

If you're running 32 bit 10.04 then [Userful Multiplier(TM)]("http://www.userful.com/products/userful-multiplier") may be an option for you. The 10 seat trial version is in the multiverse repo. According to [this]("http://packages.ubuntu.com/lucid/userful-multiplier") it has a nag screen which can be removed; either by registering for the free 2 seat license or paying for a 10 seat license. I haven't tried it because I've got 64 bit and am otherwise very happy. I'd be very interested to hear how others go if they try it.

Hi JedMeister,

We saw your post and wanted to give you a heads-up; the only working version of Userful Multiplier available in the repo is 320.20081015  and it only works with Ubuntu 8.04 (we are working to get the non-functioning packages removed).  

We do have a version -- Evaluation version 3.8 -- that supports Ubuntu 10.04 64 bit, it is available from [the Userful website]("http://www.userful.com/support/all-downloads/umx-download").

Thanks,

Userful Team

---

### Post by lsmoker on 2010-08-28
I would go with Userful if it allowed each seat to run directly on each video card.

For me MuliseatX worked fine when the X server had the RAC code in it. Now with the VGA Arbiter, it refuses to work for me. I see that some have gotten it to work with the nvidia binary driver. Maybe it depends on which cards are used...?

---

### Post by stafio on 2010-09-03
I started a [multiseat thread at the Linux Agora forums]("http://linuxagora.com/vbforum/showthread.php?t=764") a while back that I've finally updated with information for Lucid Lynx.

---

### Post by ville1ero on 2010-09-17
But how can you do that if /etc/gdm/gdm.con don't exist? Do you use KDE or Kubuntu? Do you think I can get 6 seat's?

---

### Post by ville1ero on 2010-09-17
Sorry I have to reed more, I replay too quick. I've try another thinks ([http://ubuntuforums.org/showthread.php?p=9857743#post9857743](http://ubuntuforums.org/showthread.php?p=9857743#post9857743), [http://multiseatonlinux.blogspot.com/2010/06/part-1-setting-up-base.html](http://multiseatonlinux.blogspot.com/2010/06/part-1-setting-up-base.html)) and don't work. I hope I can doit with you information Stafio.

---

### Post by ville1ero on 2010-09-19
Stafio, It work's!!!

But not for me :(... I have 3 video card's with dual head, and with KDE+Xorg I only have the ability to work with one head.

I'm try to downgrade GDM 2.30 to 2.20, but some things are missing (X11R6... and another stuff).

I don't know who compile the patch [https://bugzilla.gnome.org/show_bug.cgi?id=536355](https://bugzilla.gnome.org/show_bug.cgi?id=536355) (Here is the latest patch build against 2.31.92.)

This is my last chance to try 10.04 ([http://multiseatonlinux.blogspot.com/](http://multiseatonlinux.blogspot.com/)) if don't work again I will install 9.10 it look more simple to downgrade GDM 2.20[ ]("http://multiseatonlinux.blogspot.com/")

---

### Post by nicohaase on 2010-09-30
Is there also any way to configure the xorg.conf to use two displays, but on the same card? All tutorials I find tend to use on display on one video card and the second one, for another user, on a second card. Using Ubuntu 8.04, this also worked on one card, starting one X-server for both screens in extended mode and then two nested X-servers for each seat...

---

### Post by JedMeister on 2010-09-30
> **nicohaase said:**
> Is there also any way to configure the xorg.conf to use two displays, but on the same card? All tutorials I find tend to use on display on one video card and the second one, for another user, on a second card. Using Ubuntu 8.04, this also worked on one card, starting one X-server for both screens in extended mode and then two nested X-servers for each seat...I too am very interested in this scenario.

---

### Post by altavatar on 2010-10-06
For those still following GDM and Consolekit multiseat development, you may want to follow these bug tickets:

ConsoleKit
[https://bugs.freedesktop.org/show_bug.cgi?id=19333](https://bugs.freedesktop.org/show_bug.cgi?id=19333)

GDM
[https://bugzilla.gnome.org/show_bug.cgi?id=536355](https://bugzilla.gnome.org/show_bug.cgi?id=536355)

Looks like we're getting closer to a multiseat gdm+consolekit being merged into the master branch. Unfortunately, it didn't make gnome 2.32, but I'm hopeful that it'll make it into the next release. Until then it should be pretty safe to compile GDM + Consolekit with the latest mutliseat patches.

---

### Post by nicohaase on 2010-10-06
As KDM already supports multiseating out of the box, I see no need to patch my running system. My problem is that the xorg.conf I've posted at [http://paste.ubuntu.com/507543/](http://paste.ubuntu.com/507543/) does only start ONE X-server that is shown on both screens in clone mode. Moving the mice works for one move each, afterwards it does not take any more input, and the keyboards are not working at all. Does anybody see my error? Xorg.0.log doesn't give me any hints :(

---

### Post by altavatar on 2010-10-07
nicohaase:

```

Section "ServerLayout"
     Identifier     "LeftSeat" 
```

```
Section "ServerFlags"
...
     Option "DefaultServerLayout" "Left Seat" 
```

Note the extra space in the Server Flags version of "Left Seat"

---

### Post by ville1ero on 2010-10-13
**** It's a lot of work...   But I have a happy success...

Ubuntu 8.04.4
Xorg 7.3
Gdm 2.20 -geometry 1440x900+0+0
xephyr-precompiled.tar.bz2 (don't extract lib a serious crash)
Xephyr.sh (A serious and big modifications)
xkb-evdev.tar.gz
public.tgz
6 Terminals
3 Video-Cards dual head 1 "GeForce 7300 SE/7200 GS" and 2 "GeForce 6200"
6 Keyboards
model = "pc105"
keycodes = "evdev"
layout = "es"

OpenOffice 3.2.1
Single memory-usb per user (PolicyKit, gconf-editor)
Only Logout session (gnome-session-save --kill --silent)
Firefox 3.6.10
FlashPlugin 10.1.85.3
JavaPlugin 6Update21
emesene 1.6.3
....


A lot of things but don't have sound any ideas?

---

### Post by nicohaase on 2010-10-29
> **altavatar said:**
> nicohaase:

```

Section "ServerLayout"
     Identifier     "LeftSeat" 
``````
Section "ServerFlags"
...
     Option "DefaultServerLayout" "Left Seat" 
```Note the extra space in the Server Flags version of "Left Seat"Hmm, I've corrected this damn error, but my config posted [here](http://paste.ubuntu.com/522041/) still does not work, it is still frozen on login screen. If this could help to identify my errors: [here](http://paste.ubuntu.com/522042/) is my kdmrc, and [here](http://paste.ubuntu.com/522043/) is a logfile from Xorg. Each tiny hint could help me.... :)

---

### Post by ville1ero on 2010-10-29
You declared twice "Card1". And you call for "Card0" but you don't have.

But I don't know way you have the error "(EE) FBDEV(0): FBIOPUTCMAP: Invalid argument", I never seen before.

Way you don't try X -configure, this comand will make a /root/xorg.conf with the right drivers for your devices.

Then you can play with this /root/xorg.conf and try too start X (X -config /root/xorg.conf) every change you make. Make sure that you start with runlevel 1.

In my experience when I try tu use dual head in separate layout's a error ocurrs because the server can't find the screen 0 or the screen 1 in diferent ServerLayout. Maybe you can find the solution [here ]("http://ubuntuforums.org/showthread.php?t=1549793")but I don't try that.

*"Theres some conflict with screen1, which is used in both layouts. AFAIK  you cannot do this, there's no need to define some screen in one layout  "rightof" a screen in an other layout."*

---

