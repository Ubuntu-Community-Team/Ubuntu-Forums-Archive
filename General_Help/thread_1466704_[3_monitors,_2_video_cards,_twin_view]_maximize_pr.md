---
title: "[3 monitors, 2 video cards, twin view] maximize problems"
date: 2010-04-30
forum: General Help
---

### Post by Conzar on 2010-04-30
So let me start out by saying that in 9.04, I did not have this problem.

When I updated to 9.10 and now with 10.04, I still have this problem.  Problem listed below.

**Hardware**: 2 nvidia video cards, 3 monitors.  1 Video card powers 2 monitors and is setup in twin-view mode.

**Problem**: When I try to maximize a window on screen 0 (twin view enabled), the window maximizes across both monitors.

If I turn off Screen 1 (from the nvidia settings), log out and log back in, the windows on screen 0(twin view mode) maximize to 1 monitor (the desired functionality).

**Question**: Why does Screen 1 effect the way windows maximize in Screen 0?

Thanks for any help

Relevant Sections of the xorg.conf file with Screen 0 and 1 enabled.
```

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 8600 GT"
    BusID          "PCI:1:0:0"
EndSection

Section "Device"
    Identifier     "Device1"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 6200"
    BusID          "PCI:5:0:0"
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "TwinView" "1"
    Option         "TwinViewXineramaInfoOrder" "DFP-0"
    Option         "metamodes" "DFP-0: 1280x768 +0+0, DFP-1: 1024x768 +1280+0"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection
Section "Screen"

# Removed Option "metamodes" "nvidia-auto-select +0+0"
    Identifier     "Screen1"
    Device         "Device1"
    Monitor        "Monitor1"
    DefaultDepth    24
    Option         "TwinView" "0"
    Option         "metamodes" "1024x768 +0+0"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection

```

[COLOR="Red"]UPDATE[/COLOR]:
User stderr's [solution]("http://ubuntuforums.org/showpost.php?p=9413320&postcount=3") worked for me!  Thanks stderr!!!

---

### Post by bernd.juchems on 2010-05-20
Hi there ...

I am running a likely configuration with two NVIDIA-cards and three monitors on Karmic.
And since a xserver-update from yesterday, I am facing the same problems.

NVIDIA-Config docs say:
> 
Will window managers be able to appropriately place windows (e.g., avoiding placing windows across both display devices, or in inaccessible regions of the virtual desktop)?
	

Yes. The NVIDIA X driver provides a Xinerama extension that X clients (such as window managers) can use to discover the current TwinView configuration. Note that the Xinerama protocol provides no way to notify clients when a configuration change occurs, so if you modeswitch to a different MetaMode, your window manager will still think you have the previous configuration. Using the Xinerama extension, in conjunction with the XF86VidMode extension to get modeswitch events, window managers should be able to determine the TwinView configuration at any given time.

Unfortunately, the data provided by XineramaQueryScreens() appears to confuse some window managers; to work around such broken window mangers, you can disable communication of the TwinView screen layout with the "NoTwinViewXineramaInfo" X config Option (please see Appendix D, X Config Options for details).

[http://http.download.nvidia.com/XFree86/Linux-x86/1.0-9626/README/appendix-g.html](http://http.download.nvidia.com/XFree86/Linux-x86/1.0-9626/README/appendix-g.html)

Unfortunately, I am not very deep into xserver-configuration; in most cases I rely on nvidia-settings manager; so far this worked.

But I would like to restore my old screen behaviour; the way it now works really sucks ...

B.

---

### Post by stderr on 2010-06-05
I'm in a similar boat, but managed to get it working by using Compiz, no less.

NB: CCSM is CompizConfig Settings Manager

Open CCSM ***in the x screen with twinview***, click on "General Options" at the top,  then the "Display Settings" tab. Deselect the "Detect Outputs" checkbox and enter two output lines in the Outputs box by using the "New" button; one for each of the two monitors in the twinview setup, respectively left-to-right. Use this format for each line:

H_RESxV_RES+H_OFFSET+V_OFFSET

e.g. (for two monitors in twinview, 1680x1050 on the left and 1280x1024 on the right)

1680x1050+0+0
1280x1024+1680+0

Don't forget to set the H_OFFSET in the second monitor line to the H_RES of the first monitor, as in the example.

Then quit CCSM. Open CCSM again but ***in the x screen with 1 monitor only***. Go to the same place, and do the same thing - deselect "Detect Outputs", and add an Output, but obviously only set one monitor line. However, here you need to set the H_OFFSET to the total H_RES of the twinview x-screen, i.e. H_RES1 + H_RES2, or in the example, 1680 + 1280 (=2960).

e.g. (for one monitor, 1920x1200)

1920x1200+2960+0 

Quit CCSM, then try to start Compiz using whichever method you prefer.

```
compiz --replace
```

Hopefully, that should work. If not, you can return to a pre-compiz state of affairs with

```
metacity --replace
```

To restore the CCSM settings, you need only reselect 'Detect Outputs' on each x screen.

@Conzar: No problem, glad it helped!

---

### Post by bernd.juchems on 2010-06-05
For my system, the problem is solved;

I rebooted, went to recovery mode and dropped directly to shell (no X running).
I had the installer package of NVIDIA ready (not installed via "Hardware Drivers").
Then I uninstalled the driver with "nvidia-uninstall" and reinstalled it with the installer package.

Everything is fine now.

I think, the last xserver-update provided some inner changes. As the nvidia installer does something like building kernel package, changes to xserver's behaviour may do the damage, and rebuilding the kernel package will fix it.

I am not very into xserver or kernel internals, so this is just a guess. Anyway, it worked for me.

---

### Post by Zbuntu on 2010-07-04
:guitar: Hurray!!! Your compiz method worked like a charm. Now if only we could get triple view to work, I like to drag the windows around. Or not have firefox issues.

Thanks! :grin:

---

### Post by Seinfeld on 2011-03-07
Hi..

I really appreciate your advice here. I am using two monitors with my dual head nvidia GF Asus 8600 GT. No problems so far.
Now I really need to add one or two monitors to work in TwinView to expand my desktop. My motherboard does support dual video cards (Intel DX58SO). Can I add another card to my motherboard and just simply plug the third monitor ?? No xorg.conf editing necessary ?? I am using Maverick..
Also, could I use an Asus 7600GS (got it on ebay now ) or should it be an 8xxx as well ??

Thanks v. much in advance

---

### Post by pjbgravely on 2011-03-25
Seinfeld, start an new thread.

---

