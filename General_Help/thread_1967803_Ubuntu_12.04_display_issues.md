---
title: "Ubuntu 12.04 display issues"
date: 2012-04-28
forum: General Help
---

### Post by carranty on 2012-04-28
Hi,

I've just installed Ubuntu 12.04 and am having dsplay issues.  I have two monitors.  There were no issues whatsoever with the LiveCD, however after rebooting (after it had finished installation) my log in screen was horrifically distorted - so much so I could not even manage to restart without falling back the the command line (The screen brought up by pressing Ctrl-Alt-F4 works fine).  I've followed the advice on a couple of threads advising me to type "nomodeset" in my grub boot menu.  I've just done that and it's improved things to the point I can now navigate the install.  I've attached a screenshot of what things currently look like.

I've opened up the monitors application but it doesn't detect my second monitor.  I've also tried to open 'Additional drivers' but can't, clicking on the icon seems to do nothing.  I ideally want each monitor to have a seperate xscreen (but splitscreen will do).  I've been using such a setup in 10.04 and Mint 9 without problem for years. My Graphics card is a GeForce 7500 LE.  Any help on getting things working but be most appreciated! 

Edit 29/04/12 : **This original issue is now solved, however a number of us are unable to use two monitors in separate x-screen mode.  We have the proprietary driver installed, we have configured out xorg.conf file correctly by using nvidia-settings however the screen connected by a dvi cable appears grey, and the cursor is a black cross (the desktop background is shown briefly immediately after I log in, but vanishes after ~0.5 seconds).  This setup worked fine for us in previous versions of Ubuntu.  If anyone knows how to solve this issue please post it here.**

---

### Post by carranty on 2012-04-28
Hmm, I've just seen that the screenshot I took actually looks fine.  Unfortunately that is not what my monitors show.  I basically have a series of thin horizontal lines all across my screen that are very quickly appearing and disappearing.

EDIT : I've fixed the flickering issue by lowering the resolution (though now half my desktop is missing from my screen).  This also seems to have sorted the additional drivers application.  I shall download the recommended proprietary driver and see if that helps.

---

### Post by ventrical on 2012-04-28
> **carranty said:**
> Hmm, I've just seen that the screenshot I took actually looks fine.  Unfortunately that is not what my monitors show.  I basically have a series of thing horizontal lines all across my screen that are very quickly appearing and dissappearing.

EDIT : I've fixed the flickering issue by lowering the resolution (though now half my desktop is missing from my screen).  This also seems to have sorted the additional drivers application.  I shall download the recommended proprietary driver and see if that helps.

Let us know how that works out.

thanks..

---

### Post by carranty on 2012-04-28
Ok, so using the NVIDIA accelerated graphics driver (Recommended) has resolved the flickering issues.  Everything is now working fine however I can only get one monitor working.  Even with both monitors plugged in I'm not able to get Ubuntu to detect both.  Has anyone managed to resolve this?

---

### Post by ventrical on 2012-04-28
> **carranty said:**
> Ok, so using the NVIDIA accelerated graphics driver (Recommended) has resolved the flickering issues.  Everything is now working fine however I can only get one monitor working.  Even with both monitors plugged in I'm not able to get Ubuntu to detect both.  Has anyone managed to resolve this?


May I ask what type of monitor the other monitor is?  The reason i ask is that Unity 3D may have a problem detecting a suitable monitor.

---

### Post by carranty on 2012-04-28
The monitor that is being detected is a HP w2007 connected via VGA.  The one not being detected is a Samsung 2032W connected by DVI. Each monitor works fine when connected with the standard PC cable (I call it VGA but this might be wrong).  It's whichever one is connected by DVI I can't detect.  I'm hopeful that installing nvidia-settings will do the trick, however I'm currently downloading a couple of other packages from the repositories which are taking a VERY long time to download so I may not get a chance to try it until tomorrow.

The only monitor I seem able to detect in Unity is 'Laptop'.

---

### Post by carranty on 2012-04-29
Just an update to people who are having similar issues, nvidia-settings is able to detect both monitors and set them up to use twinview.  I've been using it for the past hour and all seems fine.  I still can't get it to use two separate x-screens (the screen connected via DVI is always blank, if I move the cursor over to it it turns from an arrow into a cross).  I've tried both proprietary drivers in both Ubuntu and Ubuntu 2D - I'm not sure why it won't work since it was fine in 10.04 so surely can't be my hardware?.  If anyone knows how to solve this I'd appreciate the heads up.  

I can however live with the system as it is, and so will mark the thread as solved.

---

### Post by Bealer on 2012-04-29
I'm suffering from exactly the same issue.

I have my normal monitor hooked up via DVI and my Samsung 32" tv which goes from DVI on my pc to HDMI on my tv.

The "Displays" app only recognises my monitor. However the nvidia-settings app recognises both, but I can only run it in TwinView.

This worked previously in 11.10.

---

### Post by carranty on 2012-04-29
> **Bealer said:**
> I'm suffering from exactly the same issue.

I have my normal monitor hooked up via DVI and my Samsung 32" tv which goes from DVI on my pc to HDMI on my tv.

The "Displays" app only recognises my monitor. However the nvidia-settings app recognises both, but I can only run it in TwinView.

This worked previously in 11.10.

I really don't get why twinview works when a separate x-screen doesn't.  And I don't see how its a hardware issue when we both had working dual monitors on a previous version.  If you find a solution please let me know (and I'll do the same), this twinview is ok, but it keeps momentarily trapping the cursor in between the screens whenever I move from one to the other.  It didn't bother me at first but its really starting to annoy me!

---

### Post by Kreeyon on 2012-04-29
Why is this thread marked as Solved?

I'm having the exact same issue with my Dell XPS M1330.  Ubuntu recognises my internal screen but fails to recognise any external screen.  The Nvidia Application will recognise the external screen but will only work in twin view which is less than ideal.  The resolution of the external screen is not correct either displaying a flickering image.

---

### Post by carranty on 2012-04-29
> **Kreeyon said:**
> Why is this thread marked as Solved?

I'm having the exact same issue with my Dell XPS M1330.  Ubuntu recognises my internal screen but fails to recognise any external screen.  The Nvidia Application will recognise the external screen but will only work in twin view which is less than ideal.  The resolution of the external screen is not correct either displaying a flickering image.

I originally created the thread because I had such a heavily distorted desktop that the OS was unusable.  This is now sorted and so I marked the thread as solved.  However, due to the number of us that are all having exactly the same problem  -- and the fact there is no solution as far as I can tell -- I've set the thread back to unsolved.

Edit : I've amended my initial post accordingly

---

### Post by carranty on 2012-05-01
I am now beyond the point of frustration.  I'm still unable to use separate x screens for my monitors and twinview has an **incredibly** annoying habit of preventing me from moving my cursor from one screen to another -- it seems to get trapped at the side of the screen it is in and I have to vigorously move it from left to right (or right to left) to get it to move across. This wouldn't be a huge issue except that applications keep opening in both screens at once.  For example I might open Firefox from the dash in screen 1, it opens in screen 1 but then if I go to Edit >> Preferences the preferences box opens up in the other screen, and to edit/close it involves a return trip of my cursor, which then gets trapped twice! This is happening with nearly every application I use.

Has **anyone** got either two x screens working, or know how to fix this twinview issue I'm having??

---

### Post by carranty on 2012-05-01
Since this habit of twinview to trap my mouse in a particular screen doesn't exist in either Xubuntu or Lubuntu 12.04 and since it only occurs when going from side to side across the Unity bar (not for screens above and below each other) I'm pretty sure its a bug with unity.

[B]If you are experiencing the same problem please take a look at this bug report and let the developers know it affects you too

[/B][HTML]https://bugs.launchpad.net/ubuntu/+bug/992725[/HTML]

The more people the devs know are affected by the bug, the more likely they are to take it seriously.

---

### Post by Xenosis on 2012-05-31
I too am having the exact same problem and across two separate computers with entirely different hardware (one laptop one desktop). It is possible through nvidia-settings to disable the one that was defaulted to be used and re-enable the secondary monitor. After restarting lightdm, the external monitor will be working but the main monitor will be disabled, or if enabled, will be gray with an x cursor.

---

### Post by skey. on 2012-07-10
I'm having the same problem here as well, however when I shut down or disconnect the second monitor I lose 3d unity, I have tried just about every-thing I've found on the net, nothing works part a fresh install. I want to get the second monitor working properly with-out doing a fresh install

---

### Post by gwpritch on 2012-07-18
Similar problem here.  HP laptop with external monitor attached.
The external monitor is recognised and displays if I mirror the displays but when I try to extend the desktop the screen locks up. Everything worked fine under 11.10.
Can anyone provide or point to a solution.

---

### Post by pcm_man on 2012-07-19
I just did a clean install of 12.04 since I had to build a new computer after my motherboard died.  My 24" Gateway monitor is also being reported as a "Laptop" display.  I have done all updates and checked that the Nvidia display driver is installed.  Of course all of this worked well and fast using the 10.10 release.

Unity is TERRIBLE as a desktop computer interface!  I am now exploring alternatives but I am still going to use Ubuntu 12.04 LTS as the base.  It does look like this is a very very solid release and once I find an alternative to Unity this will be fully supported for FIVE YEARS!  YES!

I advise everyone to take a look at SnowLinux2.  I think this is what I will be going with.

---

### Post by HullDown on 2012-08-03
I'm having the same issue with getting dual monitors on my desktop working (they worked fine for a time). The X server would often crash (blackout) and sometimes log me out. 

One thing I noticed, is that the Display settings in Ubuntu are set to "laptop" now and will not let me change them to anything else. NVidia will not alllow me make any changes and thinks my second LCD is a CRT.

---

### Post by gweedoh565 on 2012-08-29
I have also experience this problem  on a Dell Precision M6400 with Ubuntu 12.04 64-bit. I had a gray LCD screen with an X cursor that was unusable while the external monitor worked fine. 

This was a dual-boot system (with Windows 7), and it first happened after booting Ubuntu after restarting from Windows.  For whatever reason, after rebooting in Windows and then again to Ubuntu, the problem disappeared.

---

### Post by Bartender on 2012-08-29
Similar issues with an old Dell 470 Precision, with two monitors and an ASUS nVidia GeForce 210 card.  Main monitor is an Acer P243W on DVI, second monitor is an ASUS VH242H on HDMI.  I've been running 10.04 on this rig for quite a while now, hesitant to go to 12.04.

Dropped an SSD into the 470, unhooked the original HDD, installed 12.04, then used the "Additional Drivers" utility to get the recommended nVidia drivers.  I couldn't find my danged notes from last time, but I *think* the correct way to bring up the nVidia app in terminal is: 

```
gksu nvidia-settings
```

The monitors were identified correctly, and the proper resolutions were identified without my input.  I chose "TwinView".  Everything seemed to work pretty much like the last time i remember using the nVidia drivers.  However, when I tried to "Save to X Configuration File" I got the following error in the terminal screen which I'd used for the above command.

```
VALIDATION ERROR:  Data incomplete in file /etc/X11/xorg.conf.
Device section "Default Device" must have a Driver line.
```

Having no idea what that meant, I just moved on.

Went into System Settings>Displays to get the launcher on just the main display.

So, it only took a coupla minutes to identify the following issues which did NOT occur in 10.04:
- Any window that I drag to the ASUS (secondary) from the Acer (primary) will jump back to the Acer as soon as I try to maximize it.  If I drag it just short of maximize it'll stay on the secondary.  If I maximize it, then follow the window back to the primary, then minimize it, it jumps *back* to the secondary again.
- I get the very annoying pause across the monitors unless I pull the window across the boundary vigorously.  The pause seems to be tied to things that Unity is doing - changing the title in the upper left corner of the upper panel, plus I get the yellow box effect, where it looks like Unity is guessing where I plan to go with the window.
EDIT: Appears the fix for this isn't [terribly geeky]("http://askubuntu.com/questions/109338/how-do-i-disable-mouse-magnet-on-middle-edge-with-multi-monitors")
- In System Settings>Displays I also get the false "Laptop" I.D.

I'm gonna unplug the SSD and go back to 10.04.

Oh, hey, here's my xorg.conf file:

```
# nvidia-settings: X configuration file generated by nvidia-settings
# nvidia-settings:  version 295.33  (buildd@zirconium)  Fri Mar 30 13:38:49 UTC 2012

Section "ServerLayout"
    Identifier     "Layout0"
    Screen      0  "Screen0" 0 0
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
    Option         "Xinerama" "0"
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
    ModelName      "Acer P243W"
    HorizSync       30.0 - 94.0
    VertRefresh     56.0 - 75.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 210"
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "TwinView" "1"
    Option         "TwinViewXineramaInfoOrder" "DFP-0"
    Option         "metamodes" "DFP-0: nvidia-auto-select +0+0, DFP-1: nvidia-auto-select +1920+0"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection
  

```
 
I'm not sure how to read these, but I don't see a "Default Device" Section at all. There are Sections for: Server Layout, Files, Input Device (two of these), Monitor, Device, & Screen.

EDIT:  If you google "unity mouse magnet" you'll find some threads that talk about going to Display and turning off Sticky Edges.  That stopped things from sticking across the threshold between the two monitors.  I found some threads where the guy claimed to have found a work-around for the windows jumping back to the main display when maximized by downloading/installing Compiz and turning on Wobbly Windows, which disables Snapping Windows.  That also worked for me.

In the end I went back to 10.04 on the magnetic drive because there does not seem to be a BIOS option to [set the drives to AHCI]("http://support.dell.com/support/edocs/systems/ws470/en/ug_en/advfeat.htm#wp1101281").  Under "SATA Operation" there's only the choice between RAID ON or RAID OFF.  I followed some directions for how to enable TRIM, then check TRIM, and the check said it wasn't working.  I took the drive to another PC that is set to AHCI and the TRIM test said it was working.

---

### Post by ausrick on 2012-11-12
I wanted to pitch in that I'm having similar issues.  I didn't really notice it until I actually started using my XPS M1330 for its desired purpose after I got on the road.  some emarrasing meetings.

When I used this computer in 10.04 I had none of these problems. I could connect a projector to the monitor out, and my Fn F5 combo would even work when it came to switching between mirroring or extending, or disabling the onboard and using the projector only.

Now at best, I have to log off, log back on, and rather than settings showing two monitors, or giving me choices to either mirror or extend it just turns it into one really wide monitor.  Usually projectors don't have near identical resolution. lap top displays are a different aspect ratio than 4:3 projectors. my mouse gets hung up in the middle, and I can't maximize or full screen anything on the projector section.

I don't have an xorg.conf or even a series of confs in a xorg.conf.d directory.  So far I haven't had to... and I'm loathe to start specifying things this way on my laptop.  On my 2 servers and workstation this wasn't an issue because I'm not changing monitors and configs and resolutions all the time, but on this laptop I am plugged into different projectors on a daily basis... 

Often I need the ability to be single monitor, then plug it in to a projector and choose at that time whether to be mirrored or extended, often switching mid presentation, and then when finished go back to being a single monitor.  I don't want to (often don't have the ability to) close out of graphical applications running in the gnome shell and or log off and or reboot. (for instance if I have a web site that requires log on cred's and I get it up and going with just my onboard monitor, then I plug into their projector, and wat to project just that website full screen through the projector... I find I have to log out or restart the xserver which coincidently closes my browser and any other open apps.) and editing xorg .confs on the fly invariably leads to restarting xorg or unity or logging out or rebooting the server... :(

Also, I use Compiz and have a bunch of the animations, transparencies, desktop cube, etc. active. (I feel cheep for saying this but having such arcane computer flair going on when in the presence of common users adds a level of wow/mysticism/magician/cred that can captivate a bored audience and get more out of my work presentations as they are more engaged and take more away from it... so beyond mere eye candy I actually need a solution that works with Compiz and Unity3D so some of the conversations I've stumbled into that say it switches to 2D, or 2D is fine, or some solution isn't compatible with Compiz scares me a little.

FYI the card in my Dell XPS M1330 is an nVidia GTX-8800M I believe.

Any advice would be helpful. I feel like what I need vs what tools I know about and understand can deliver are very separate, yet somehow weren't in 10.04 and I'm not sure why. :confused:

---

### Post by Paul_Michael on 2013-10-22
I've read everyone's issues on the 2 displays.  I'm having the same issue.  I noticed that it happened ONLY after the last firmware update.  Fresh install, everything worked just fine.  Just some tweaks to the display settings.  After the firmware update, I have to unplug the second monitor or the whole system is crashed.

linux-firmware (1.79.6,179.7)

---

