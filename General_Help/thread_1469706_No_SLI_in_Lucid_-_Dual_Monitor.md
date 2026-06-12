---
title: "No SLI in Lucid - Dual Monitor"
date: 2010-05-02
forum: General Help
---

### Post by kuritsubaji on 2010-05-02
Hard details first:

EVGA nForce 750i SLI mobo
E8400 Wolfdale OC@4.23Ghz
2x GeForce GTS 250 1Gb
2x Acer AL2216W 

Soft details:

-Upgraded from 9.10 to 10.04
-I did not have a working SLI config in 9.10
-No matter what fix I tried, only one monitor
-Was running "190.53" 64-bit drivers
-I had spoofed the xorg.conf file to get both working, but only with both plugged into one board, and no SLI option enabled
-Functioning 3360x1050 workspace with the ability to move open apps across monitors, but unable to switch between multiple workspaces

-After the upgrade, my system would hang at the splash screen
-Used a LiveCD to boot up a recovery console and ran apt-get update/upgrade with the -f option
-This fixed the "195.36.15" driver and xorg.conf
-Now I have multiple workspaces with fully functioning Compiz effects--something I haven't enjoyed since the days of one monitor
-AND, my 2D and 3D framerates are remarkably faster than with the 190 drivers
-BUT still, no SLI
-Any attempt to cobble together a functioning xorg.conf only results in a one monitor solution with poor render response on both 2D and 3D applications

I've combed the threads and can't find any stories of success with SLI and dual monitors, regardless of release or driver.  Is there any hope for the poor sops out there like me?  Or am I destined to have a $150 board plugged into my machine that is doing nothing except moving air?

Woe is me...:frown:

---

### Post by ants280 on 2010-05-04
Kind of long and wordy/detailed, but here it goes:

I have found something interesting (see next paragraph).  I am unsure if my SLI is now fully enabled because I only have one screen and do not use Ubuntu for graphically intense applications (I use Windows for gaming, Linux for _everything_ else). 

I had a great deal of trouble in the past getting my Ubuntu/Linux to work with my 2x9600 setup.  In the end, the only way I got the manually installed NVidia driver to work on my system was  by putting the following lines in the "Driver" Section of my xorg.conf (/etc/X11/xorg.conf):
```

Busid "PCI:3:00:00"
Option "sli" "auto"

```
When I installed 10.04 (clean install), I started to perform my usual manual install of the NVidia driver (my graphics cards are blaringly loud with no driver present, so I can use my computer without 100000000dB of white-noise in the background).  The driver install failed.  After about an hour of struggling, I said what the h*** and installed the "current" driver that Ubuntu's "Hardware Drivers" GUI prompted me to install (195).  It worked!  It made my drives quiet, but the /usr/bin/nvidia-settings GUI didn't say it was in SLI mode _anywhere_.

Today, I tried putting the second line (Option "sli" "auto") in my xorg.conf.  After rebooting, my system completed a stable boot.  No noticeable difference to me, but I noticed some additions in the nvidia-settings GUI.  In the "OpenGL Settings" Section for "X Screen 0", a "Enable SLI Heads-Up-Display" checkbox appeared under the "Miscellaneous" sub-menu.  
On both "GPU 0 - (GeForce 9600 GT)" and "1" sections, the main part now has the phrase "(SLI)" appended to the "X Screens:" part - reading "X Screens \t Screen 0 (SLI".  "GPU 0" also lists my monitor as a display device, but "Display Devices: \t None" is listed for GPU 1.  I expected this difference between GPUs 0 and 1.
EDIT: Without the addition to xorg.conf, GPU 1 claims to have "X Screens: \t None" (yes, bad English on my part).  The "Display Devices" section remained unchanged by the xorg.conf addition.

If anyone wants me to run any tests on my computer or has a method for me to use to prove/disprove my SLI is working, let me know.  I have added/removed (Option "sli" "auto") to the "Devices" section of my xorg.conf THREE times, and the changes to the nvidia-settings GUI have shown up/disappeared each time.

---

### Post by dagrump on 2010-05-04
Looks as though I've added Option "SLI"  "SFR" in the screen section of my xorg.conf file. If you fire up nvidia-settings & look at X screen 0 it will list Both GPU's & you will be able to inable the headsup display.
I only use a single monitor, so you are on your own getting two configured.
I would search for posts about twinview?? after I was sure I had SLI working. I'm sorry I'm just to lazy to drag a second monitor in to play with it. I have a pair of monitors, same size & brand, but I just don't feel the need to fight that battle.
Good luck, & tell us if you get it working.


****edit****
I'm using a KVM switch with 2 boxes, so it would take some work to make the changes needed to play with 2 monitors on the 1 box. That is why I claim laziness as an excuse. Well that & my desk is a mess, would need to make room for the second monitor!

---

### Post by Truthseekernz on 2010-05-08
I have dual monitors working fine with my NVidia graphics adaptor (mumble 210?). 

The only issue I have is that any wallpaper I display no longer extends across both monitors, but instead is duplicated on EACH monitor. So my 2560x1024 wallpaper is all squashed up and repeated on both screens. 

I can drag / drop whatever I want between screens. They function fine that way. But I'm missing my huge, two-monitor wallpapers. 

Might go back to Karmic from my backup, as there doesn't appear to be any functional advantage in having upgraded to Lucid / v10.04. if anything, my DVD-RW drive seems to be having trouble with some disks it worked fine with before the upgrade.

---

### Post by MrQuincle on 2010-05-11
> **kuritsubaji said:**
> Hard details first:
EVGA nForce 750i SLI mobo
E8400 Wolfdale OC@4.23Ghz
2x GeForce GTS 250 1Gb
2x Acer AL2216W 

Hi Kuritsubaji! 

Would you mind to post your configuration files? Until now I always managed to get a "similar" system running with two graphics cards (GeForce 8600 GT) and two monitors (Iiyama PLE2200). I have the 32-bit 195.36.24 driver. 10.04 is the first version that really bugs me. I can't get my second monitor to work. Even less in an SLI configuration.

I would like to have a functioning xorg.conf again, so if you would post it, I would be really grateful!

(And yes, I can make it work by having both of my monitors plugged into one card, but I used to use two cards, one for each monitor, although without SLI).

---

### Post by kuritsubaji on 2010-05-24
UPDATE:

I've had to give up on trying to run SLI on a dual monitor setup.  I've settled for running both monitors, but on separate cards with no SLI.  I have Xinerama enabled and no Compiz effects.  It's a bummer, but I was getting a lot of lock-ups.  So far, this set up is stable.

Here's a copy of my xorg.conf:

```
# nvidia-settings: X configuration file generated by nvidia-settings
# nvidia-settings:  version 1.0  (buildd@yellow)  Fri Apr  9 11:51:21 UTC 2010


Section "ServerLayout"
# Removed Option "Xinerama" "0"
    Identifier     "Layout0"
    Screen      0  "Screen0" 0 0
    Screen      1  "Screen1" RightOf "Screen0"
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
    Option         "Xinerama" "1"
EndSection

Section "Files"
EndSection

Section "InputDevice"

    # generated from default
    Identifier     "Mouse0"
    Driver         "mouse"
    Option         "Protocol" "auto"
    Option         "Device" "/dev/psaux"
    Option         "Emulate3Buttons" "no"
    Option         "ZAxisMapping" "4 5"
EndSection

Section "InputDevice"

    # generated from default
    Identifier     "Keyboard0"
    Driver         "kbd"
EndSection

Section "Monitor"

    # HorizSync source: edid, VertRefresh source: edid
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "Acer AL2216W"
    HorizSync       30.0 - 82.0
    VertRefresh     56.0 - 76.0
    Option         "DPMS"
EndSection

Section "Monitor"
    Identifier     "Monitor1"
    VendorName     "Unknown"
    ModelName      "Acer AL2216W"
    HorizSync       30.0 - 82.0
    VertRefresh     56.0 - 76.0
    Option        "DPMS"
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce GTS 250"
    BusID          "PCI:3:0:0"
EndSection

Section "Device"
    Identifier     "Device1"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce GTS 250"
    BusID          "PCI:4:0:0"
EndSection

Section "Screen"

# Removed Option "TwinView" "1"
# Removed Option "metamodes" "DFP-0: nvidia-auto-select +0+0, DFP-1: nvidia-auto-select +1680+0"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "TwinView" "0"
    Option         "metamodes" "nvidia-auto-select +0+0"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection

Section "Screen"
    Identifier     "Screen1"
    Device         "Device1"
    Monitor        "Monitor1"
    DefaultDepth    24
    Option         "TwinView" "0"
    Option         "metamodes" "nvidia-auto-select +0+0"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection
```

---

### Post by Roasted on 2010-05-24
> **Truthseekernz said:**
> I have dual monitors working fine with my NVidia graphics adaptor (mumble 210?). 

The only issue I have is that any wallpaper I display no longer extends across both monitors, but instead is duplicated on EACH monitor. So my 2560x1024 wallpaper is all squashed up and repeated on both screens. 



System - Preferences - Appearance - Background

Lower left side, option "Style." Hit "Span" in the drop down.

---

### Post by CoreyS on 2010-06-20
> **Roasted said:**
> System - Preferences - Appearance - Background

Lower left side, option "Style." Hit "Span" in the drop down.

Tried to change the style. Didn't work. Still repeats the wallpaper on each screen. Karmic displayed it just fine.

Karmic -> Lucid upgrade. Problems: Firefox icon missing, wallpaper not spanning. Lost my automount of installed NTFS HDDs. NTFS config tool fixed easily. Working on wallpaper right now.

---

### Post by BlackShaddow on 2010-09-27
:evil: Please see NVidia documentation! :evil:

**_(1)_**  SLI will only work on _ONE_ (1) Monitor on a card with more than one Head!

**_(2)_**  SLI will only work if you have more than _ONE_ (1) GPU active!

I am using 2x8800GTX's, and SLI when enabled ...

No SLI 2x2 24" 2 Xscreen
SLI 1 24" ... Showing No Improvement :redface: ... (Wine Oblivion)

Note: SLI will NOT span screen's or X screens.

---

