---
title: "Problem editing xorg.conf with NVIDIA X Server Settings GUI"
date: 2010-01-15
forum: General Help
---

### Post by auh2o on 2010-01-15
**Original title: Problem editing xorg.conf with NVIDIA X Server Settings GUI**

After a fresh install of Ubuntu 9.10 on a computer with a NVIDIA GeForce4 graphics card, I was asked if I wanted to install the proprietary accelerated graphics driver (version 96). I did this, but it initially led to some trouble. The vertical refresh value was set much higher than my screen could handle, so I was greeted with a black screen at login and had to go into the recovery console and edit the corresponding values xorg.conf. Then I could log in, but only had a 640x480 screen resolution to choose from. Well, I was able to fix that, **and** the problem that arose when I later turned on visual effects - that the top title bar of all windows disappeared. Everything from the command line! Having never dealt with linux at all up until a few days ago I feel quite proud! But, I could never have done it without this forum! There's really an abundance of valuable info here for a complete newbie like me.

However, there is one last NVIDIA-related problem I can't seem to solve on my own, so I will humbly ask for help! I can edit /etc/X11/xorg.conf manually, but any changes I make through the NVIDIA X Server Settings GUI doesn't stick. When trying to save the configuration I get the error message "Unable to remove old xconfig backup file /etc/X11/xorg.conf.backup". I removed the backup manually, but then I got the message that it was unable to create a new backup file. And when I restart the X server again, I am back to a 1600x1200 resolution, which is too much for my 19" screen. 1280x1024 is what I want.

xorg.conf and xorg.conf.backup are both under root ownership with read & write access. What should I do? I'll include my current xorg.conf below, even if it isn't directly related to this problem:

```
Section "ServerLayout"
    Identifier     "Layout0"
    Screen      0  "Screen0" 0 0
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
EndSection

Section "Files"
EndSection

Section "Module"
    Load           "dbe"
    Load           "extmod"
    Load           "type1"
    Load           "freetype"
    Load           "glx"
EndSection

Section "ServerFlags"
    Option         "Xinerama" "0"
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
    # HorizSync source: xconfig, VertRefresh source: xconfig
    Identifier     "Monitor0"
    VendorName     "Acer"
    ModelName      "AC915"
    HorizSync       30.0 - 80.0
    VertRefresh     50.0 - 80.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce4 Ti 4200 with AGP8X"
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "TwinView" "0"
    Option         "AddARGBGLXVisuals" "true"
    Option         "metamodes" "1600x1200 +0+0; 1280x1024_75 +0+0; 1024x768 +0+0; 800x600 +0+0; 640x480 +0+0"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection
```

---

### Post by sisco311 on 2010-01-17
You have to run nvidia-settings as root. Press Alt+F2 and run:
```
gksu nvidia-settings
```

---

### Post by audiomick on 2010-01-17
sisco is right. Took me a while to figure that out too...

---

### Post by auh2o on 2010-01-20
Well, of course... Almost too easy! But that means the launcher under System/Administration on the main menu is essentially useless. I miss being able to edit menu items.

In any case, yes, xorg.conf now saves just fine, and I now get the resolution I set in the NVIDIA Settings GUI after I log in, BUT... I still get 1600x1200 at the login screen! Anyone care to guess as to why that is? I tried installing the startupmanager that is available in the software center, since it supposedly lets you set both boot loader and startup resolution, and I'm not all that confident editing configuration files on my own. But that didn't solve it either. It changed GRUB to the resolution of my liking, but when I got to the login screen it reverted back to 1600x1200. Then after logging in, it switches back again to my set NVIDIA option of 1280x1024.

(Should I maybe create another topic for this problem, or is it ok to continue here...?)

---

### Post by wojox on 2010-01-20
Your screen section looks weird. Compare yours to mine:

```
Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "TwinView" "1"
    Option         "TwinViewXineramaInfoOrder" "CRT-0"
    Option         "metamodes" "CRT-0: 1024x768 +0+0, CRT-1: 1024x768 +1024+0"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection
```

---

### Post by auh2o on 2010-01-20
Indeed, simply removing "1600x1200 +0+0" from the metamodes line gives me a 1280x1024 login screen. That line was created by nvidia-settings though, and I thought it was a list of supported modes, not the currently chosen mode. Anyway, another problem solved!

---

### Post by leehach on 2010-01-20
> **auh2o said:**
> Well, of course... Almost too easy! But that means the launcher under System/Administration on the main menu is essentially useless. I miss being able to edit menu items.

I had the same problem, but this is easily fixed. Go to System&#8594;Preferences&#8594;Main Menu. Then find the NVIDIA X Server Settings launcher. Right-click, select Properties. Then on the Command line prepend gksudo. Not at my machine right now, but the end result should look something like```
gksudo [path]/nvidia-settings
```

Saves you from having to launch from the command line every time.

---

### Post by auh2o on 2010-01-20
leehach> Great! Thanks! It would be nice to be able to access those properties for each program straight from the main menu upon right-clicking though. Maybe a minor feature suggestion for the developers?

Thanks for the help everybody.

---

### Post by auh2o on 2010-01-21
Well, it seems my problems are not over after all...

All was fine until I logged out from the Gnome desktop. I've restarted several times since i thought I fixed the login screen display problem, but when I logged out instead of restarting, the login screen now went to 800x600! And unlike before, when my login screen was 1600x1200 but I would still get my 1280x1024 setting once logged in, it now stays at 800x600 all the time! And I can't choose any other modes in the NVIDIA Settings GUI! It only has an "Auto" screen resolution option now. Restarting doesn't help either.

I don't get it. Nothing has changed in xorg.conf. Why would a simple logout have caused this?

Edit: Ok, so after yet another restart, my login screen opened at 1024x768! I've soon been through every resolution in the book. After logging in, I was still on this resolution, but once again able to choose 1280x1024 in the NVIDIA settings. Hower, I just tried 'switch user' to get me back to the login screen, and resolution then changed to 800x600! When getting back to the desktop it now switches back to 1280x1024 again. Wonder what surprise I'll get on next restart?

Something is obviously acting up here, and I need someone with a linux knowledge not as lacking as much as my own to tell me what.

---

### Post by pbrane on 2010-01-21
Try looking at *man nvidia-settings* and note that nvidia-settings does not preserve values between runs of the X server. However the screen resolution should stick if it's configured in your xorg.conf. Maybe *man nvidia-settings* will have a clue.

What I have done is create a ~/.nvidia-settings-rc with nvidia-settings and run it in System->Preferences->Startup Applications with *nvidia-settings --load-config-only*. Every time I log in all my settings are applied.

---

### Post by auh2o on 2010-01-21
That is indeed a good way to ensure the right settings are applied* after* login. But where are the settings for the login screen specified? I will still get 800x600 or whatever as soon as I log out.

As long as I just restarted or shut down from my desktop, all was fine. But as soon as I logged out instead, I ran into problems. That's a bit weird too, since if the login screen settings are specified somewhere they should be applied regardless.

---

### Post by pbrane on 2010-01-21
The login screen resolution is set in /etc/default/grub. run *update-grub* after editing. This assumes you are using grub2. For grub legacy edit /boot/grub/menu.lst.

Check out this link: [https://help.ubuntu.com/community/Grub2]("https://help.ubuntu.com/community/Grub2")

---

### Post by leehach on 2010-01-21
From [the man page for xorg.conf]("http://linux.die.net/man/5/xorg.conf"): "This optional [Modes] entry specifies the list of video modes to use. <snip> The first valid mode in this list will be the default display mode for startup. <snip> If the Monitor section contains no modes, then the selection will be taken from the built-in VESA standard modes."

With the NVIDIA drivers the Modes list is replaced with the Option "metamodes" line, but I think the effect is the same. If you want to default to 1280x1024, just make sure that that's at the front of the list. If it is at the front of the list but X is starting in some other mode, the first mode isn't working for some reason. 

I ran into the same problem in that 1280x1024 would only work at 60Hz. I would set 1280x1024 in NVIDIA X Server Settings, save to xorg.conf, reboot, and it would default to the next resolution in the list. I guess X couldn't figure that out the correct refresh rate, but I was able to define 1280x1024 @ 60Hz with a Modeline generated with
```
cvt 1280x1024
```
The relevant sections of my xorg.conf look like this:
```
Section "Monitor"

    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "Princeton Graphics Systems VL173"
    # HorizSync source: edid, VertRefresh source: edid
    HorizSync       31.0 - 60.0
    VertRefresh     56.0 - 75.0
    Modeline       "1280x1024_60"  109.00  1280 1368 1496 1712  1024 1027 1034 1063 -hsync +vsync
    Option         "DPMS"
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "TwinView" "0"
    Option         "TwinViewXineramaInfoOrder" "CRT-0"
    Option         "metamodes" "1280x1024_60 +0+0; 1280x960 +0+0; 1024x768 +0+0; 800x600 +0+0; 640x480 +0+0"
    SubSection     "Display"
        Depth       24
       #Modes      "1280x1024_60" "1280x960" "1024x768" "800x600" "640x480"
    EndSubSection
EndSection

```

**Notes**
[LIST=1]
[*]The identifier 1280x1024_60 in the metamodes list references the Modeline in the Monitor Section
[*]When I have NVIDA X Server Settings save the xorg.conf and don't have "Merge with existing file" checked, it deletes the Modeline and the 1280x1024 mode fails on reboot
[*]Without the NVIDIA driver the metamodes list would be replaced with the commented out Modes list in SubSection "Display"
[*]I haven't yet tested whether user changes via System&#8594;Preferences&#8594;Screen Resolution will persist, and whether they will do so without altering the default display mode saved in xorg.conf, but it will make an interesting experiment
[/LIST]

---

### Post by auh2o on 2010-02-03
leehach, a belated thank you for your reply. I followed your advice and got cvt values for the framerates I know the monitor can support at my preferred resolution. I then added them to xorg.conf.

However, my resolution problems remain, and the X server is a bit shaky! Everything might be fine for a couple of restarts, but every once in a while the resolution will revert back to 800x600 (like today)! I then have NO way of changing it, because in the NVIDIA Settings GUI the only option given for resolution is "Auto".

I tried to restart several times, but was still in 800x600 after each restart, and no way to change the resolution in the GUI. I then tried switching user, and lo and behold, I got to the login screen at 1280x1024. But when I went back in to the desktop, it reverted to 800x600 again, with still no way to change. So, I logged myself out, and the login screen dropped back to 1280x1024. I logged in again, and this time the resolution stayed! But who knows for how long...

WHAT is the problem here? What except xorg.conf is it that could be behind these problems?

The Monitor and Screen sections of xorg.conf look like this now:

```
Section "Monitor"
    # HorizSync source: xconfig, VertRefresh source: xconfig
    Identifier     "Monitor0"
    VendorName     "Acer"
    ModelName      "AC915"
    HorizSync       30.0 - 75.0
    VertRefresh     50.0 - 85.0
    Modeline "1280x1024_85"  159.50  1280 1376 1512 1744  1024 1027 1034 1078 -hsync +vsync
    Modeline "1280x1024_75"  138.75  1280 1368 1504 1728  1024 1027 1034 1072 -hsync +vsync
    Modeline "1280x1024_65"  118.50  1280 1368 1496 1712  1024 1027 1034 1066 -hsync +vsync
    Modeline "1280x1024_60"  109.00  1280 1368 1496 1712  1024 1027 1034 1063 -hsync +vsync
    Option         "DPMS"
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "AddARGBGLXVisuals" "true"
    Option         "TwinView" "0"
    Option         "metamodes" "1280x1024_85 +0+0; 1280x1024_75 +0+0; 1280x1024_65 +0+0; 1280x1024_60 +0+0; 1280x1024 +0+0"
    SubSection     "Display"
        Depth       24
        Modes      "1280x1024_85" "1280x1024_75" "1280x1024_65" "1280x1024_60"
    EndSubSection
EndSection
```Also, though I know that the monitor itself can handle both 85 and 75Hz (and I run 85 on Windows with the Windows driver), the NVIDIA settings won't let me set more than 65 regardless of the additional lines in xorg.conf. I get an option of either 60 or 65, or Auto, which I run on now (it gives 65Hz). What could be the problem here? The NVIDIA driver?

---

### Post by auh2o on 2010-02-04
And now it has happened again! I have about 6 or 7 restarts since last time things got back to normal, but now suddenly I'm back at the dreaded 800x600 with no way to change! I did NOTHING even remotely related to display settings before last restart. I have tried switching user or logging out several times, but now that doesn't work either. And I've restarted 3 times to no avail either.

I have set GRUB to display 1280x1024x32 at boot, and that works just fine. I have also set the virtual terminal to the same resolution, and that ALSO works correctly when switching from this desktop, but when I hit Ctrl-Alt-F7 I'm back to 800x600 again.

WHY? HOW? This is really starting to piss me off.

---

### Post by kelvin spratt on 2010-02-04
You don't do anything with your xorg file you do it by setting it all up with gksu nvidia-settings make sure you click on save settings that will write the settings to your xorg file correctly do not play with any other display program in the preferences menu as it gives incorrect settings ie 50hz instead of 75hz in my case. If you restart and its not correct its cause you did not use gksu correctly you cannot make changes to nvidia using sudo.

---

### Post by auh2o on 2010-02-04
Well, after yet another restart I am now back to the right resolution. Fancy that. I did absolutely no changes to the system prior to the last restart.

kelvin, that's some pretty weird advice. Indeed I do have, or have had, to edit xorg.conf manually to enter all necessary values. And why shouldn't or wouldn't I? nvidia-settings is just a frontend for the configuration file anyway. As is noted above, after the initial confusion I do use gksu for nvidia-settings. That is certainly not the problem, since I can write to xorg.conf just fine via the GUI. The problem is that SOME times upon booting the system - seemingly totally at random - something seems to override xorg.conf or cause it not to be implemented properly. And at those times, resolution can't be changed at all from within nvidia-settings, and the only thing I can rely on to get me back to normal is dumb luck!

---

### Post by kelvin spratt on 2010-02-04
How long have you been using Ubuntu You should do some reading their is a How TOs  on setting up Nvidia cards Nvidia uses its own tools to set up xorg. 
In 4 years and everything from BSD/ Arch/ Gentoo/down to Ubuntu. never have I had a problem setting up a nvidia its basically the same in all off them.
Read the How too install a nvidia card? as i said you can not make the settings stick using root you have to be a super user hence gksu nvidia-settings and save in the nvidia gui .

---

### Post by auh2o on 2010-02-05
I appreciate your attempts at helping, but what would be even more helpful is if you actually read the thread first. What you say is addressed already in the second post. That is not the problem here.

---

### Post by kelvin spratt on 2010-02-05
> **auh2o said:**
> I appreciate your attempts at helping, but what would be even more helpful is if you actually read the thread first. What you say is addressed already in the second post. That is not the problem here.
Watch this this is the correct way ttp://www.youtube.com/watch?v=V0_uCQnK_t4
its all on google and youtube.

---

### Post by auh2o on 2010-02-05
Again, the second post in this thread addressed that issue already. Inability to save to xorg.conf - either through the NVIDIA GUI or by manually editing the file - is NOT the issue I'm having. I have as of now edited the original topic to reflect this.

---

### Post by Jackzor on 2010-02-05
Have you tried just installing newer drivers? I am going to go look for a simple way to install better nvidia drivers if any for you. Will be back in a few minutes.

First thing that I thought about was drivers. Btw. And I skimmed the thread and didn't see any attempts. I may be wrong though :(

---

### Post by audiomick on 2010-02-05
There is a way of including a nVidia repository in synaptic. Has that already been mentioned? I will wait for Jackzor to get back, he is likely to find a how to. If  not, I will have a look for it.

---

### Post by auh2o on 2010-02-05
My NVIDIA card is not exactly new, it's a GeForce4 Ti 4200 with AGP8X. The latest corresponding driver version for this card is version 96.43.13. That is what I have installed through the Hardware Drivers GUI. It is "activated and currently in use".

Including a NVIDIA repository in the package manager hasn't been mentioned, but I wonder if that could be a solution. There are already two later drivers in the Canonical repository for 9.10 (173 & 185), but those drivers are not for my card but for later cards.

If it wasn't for my monitor working just fine in Windows, I'd almost venture to think it was some kind of hardware problem, but I doubt that could be so. Mind you, things are working just fine MOST of the time - that's what's so confusing. It's just every once in a while upon booting that these problems occur.

---

### Post by TheBig3 on 2010-02-05
I had similar problems trying to edit my xorg.conf file. 
Here's what worked for me:

At the terminal, type: ```
sudo nvidia-xconfig
```

You should get a response like 
```
Using X configuration file: "/etc/X11/xorg.conf".

VALIDATION ERROR: Data incomplete in file /etc/X11/xorg.conf.
                  Undefined Device "(null)" referenced by Screen "Default
                  Screen".

Backed up file '/etc/X11/xorg.conf' as '/etc/X11/xorg.conf.backup'
New X configuration file written to '/etc/X11/xorg.conf'
```

After you should be able to run either ```
sudo nvidia-settings
``` or ```
gksu nvidia-settings
```

I hope this helps....

---

### Post by auh2o on 2010-02-08
Thanks, but no. I already solved that problem. I guess I should have started a new thread about my current predicament since I can't edit the original topic title.

Anyway, I've had another 6 or 7 good restarts, and I thought that maybe after updating the kernel and the automatic reinstallation of the NVIDIA driver that followed, this problem might have gone away. But no, today when turning on the computer, it happened again. The GRUB screen popped up as normal at 1280x1024, but the login screen appeared at 800x600, and after logging in there was no way to change the resolution in the NVIDIA Settings. One simple restart solved the problem this time though. I could do nothing but cross my fingers as it booted up again. I'm still waiting for someone to offer up some kind of explanation as to why the hell this keeps happening...

---

### Post by oshunluvr on 2010-02-08
I just came to this thread so forgive me if this repeats anything...

I haven't seen your log file. Have you viewed /var/log/Xorg.0.log during these errors?

I suggest booting, save a copy of the above file to your desktop, boot again until it fails, go to the text console and save another copy of the file (different name) to your desktop again, reboot until it comes back, compare the files.

I'd be interested to see what it says when it crashes. Also consider since you have an older card, the maybe it would work better with and older version of the driver.

**FYI: Just in case anyone reads this thread looking to edit their own xorg.conf file:**

nvidia-settings is designed as a USER tool, not an admin tool. That is why it won't over write the system file unless you use "sudo" or run it as root. There are several ways to save and access settings using nvidia-settings both system wide and in userspace. I think the idea is that each user can have his or her own personal settings come up when they log in. Assuming your kids use your computer - do you really want THEM to have control over your xorg configuration? I think not!

In practice : I think most of use want optimal settings for every user. I believe the difference between older CRT type monitors which are easily capable of very different resolutions and scan rates vs. LCD type which really only look good at their native settings is where the userspace setting idea came from.

---

### Post by auh2o on 2010-02-09
Thanks for the reply. I'll certainly try your suggestion. I have saved a copy of Xorg.0.log in its current state (which was written after a "good" restart) and try to get the problem to happen again. It might take a few restarts though!

When looking through the current, "good" log, I do come across a few interesting lines, even though they may have nothing to do with this specific resolution problem:

```
(II) NVIDIA(0): Assigned Display Device: CRT-1
(WW) NVIDIA(0): No valid modes for "1280x1024_85+0+0"; removing.
(WW) NVIDIA(0): No valid modes for "1280x1024_75+0+0"; removing.
(II) NVIDIA(0): Validated modes:
(II) NVIDIA(0):     "1280x1024_65+0+0"
(II) NVIDIA(0):     "1280x1024_60+0+0"
(II) NVIDIA(0):     "1280x1024+0+0"
(II) NVIDIA(0): Virtual screen size determined to be 1280 x 1024
(WW) NVIDIA(0): Unable to get display device CRT-1's EDID; cannot compute DPI
(WW) NVIDIA(0):     from CRT-1's EDID.
(==) NVIDIA(0): DPI set to (75, 75); computed from built-in default
```No valid modes for 75 and 85Hz, even though I have specified them with Modelines in the config file, and I know the monitor supports them? Could this be purely a driver limitation?

Also, what does it mean that it's unable to get EDID from the monitor and instead uses a default value? Sure, the monitor is several years old, but not so old that it doesn't send EDID - which has been around since the mid-90s. Not that the default DPI value is bad, so maybe I should just ignore that.

I doubt an older driver would be better for me; this card is specifically supported by the 96 version driver. And an older driver is not in the repositories anyway; I'd have to look elsewhere.

Edit: I've restarted lots of times, but no "luck" yet. It's bound to happen sooner or later though. I'll be back when it does.

---

### Post by auh2o on 2010-02-21
The resolution problem STILL hasn't appeared again. I'm almost starting to think I've shaken it off somehow. But I will be back to this thread with an update on the logfiles should the problem occur again.

In the meantime, I'll turn the part about not being able to get all screen refresh rates to work into a new thread. This one has gotten too crowded and strayed somewhat from the original topic.

---

### Post by auh2o on 2010-02-24
It "finally" happened again today. Now I know what happens, but I don't know why. Per the Xorg.0.log:

```
(**) NVIDIA(0): Depth 24, (--) framebuffer bpp 32
(==) NVIDIA(0): RGB weight 888
(==) NVIDIA(0): Default visual is TrueColor
(==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
(**) NVIDIA(0): Option "TwinView" "0"
(**) NVIDIA(0): Option "MetaModes" "1280x1024_85 +0+0; 1280x1024_75 +0+0; 1280x1024_65 +0+0; 1280x1024_60 +0+0; 1280x1024 +0+0"
(**) NVIDIA(0): Option "AddARGBGLXVisuals" "true"
(**) NVIDIA(0): Enabling RENDER acceleration
(II) NVIDIA(0): Support for GLX with the Damage and Composite X extensions is
(II) NVIDIA(0):     enabled.
(II) NVIDIA(0): NVIDIA GPU GeForce4 Ti 4200 with AGP8X at PCI:1:0:0 (GPU-0)
(--) NVIDIA(0): Memory: 131072 kBytes
(--) NVIDIA(0): VideoBIOS: 04.28.20.05.11
(II) NVIDIA(0): Detected AGP rate: 4X
(--) NVIDIA(0): Interlaced video modes are supported on this GPU
(--) NVIDIA(0): Connected display device(s) on GeForce4 Ti 4200 with AGP8X at
(--) NVIDIA(0):     PCI:1:0:0:
(--) NVIDIA(0):     @@@ (CRT-1)
(--) NVIDIA(0): @@@ (CRT-1): 350.0 MHz maximum pixel clock
(II) NVIDIA(0): Assigned Display Device: CRT-1
(WW) NVIDIA(0): No valid modes for "1280x1024_85+0+0"; removing.
(WW) NVIDIA(0): No valid modes for "1280x1024_75+0+0"; removing.
(WW) NVIDIA(0): No valid modes for "1280x1024_65+0+0"; removing.
(WW) NVIDIA(0): No valid modes for "1280x1024_60+0+0"; removing.
(WW) NVIDIA(0): No valid modes for "1280x1024+0+0"; removing.
(WW) NVIDIA(0): 
(WW) NVIDIA(0): Unable to validate any modes; falling back to the default mode
(WW) NVIDIA(0):     "nvidia-auto-select".
(WW) NVIDIA(0): 
(II) NVIDIA(0): Validated modes:
(II) NVIDIA(0):     "nvidia-auto-select"
(II) NVIDIA(0): Virtual screen size determined to be 800 x 600
(==) NVIDIA(0): DPI set to (75, 75); computed from built-in default
(--) Depth 24 pixmap format is 32 bpp
```Suddenly, no valid modes AT ALL. But why? And this then ties in with me not being able to get the frame rate I want either, because 75 and 85 are *never* detected as valid.

It took two restarts, and then I was back to:

```
(II) NVIDIA(0): Validated modes:
(II) NVIDIA(0):     "1280x1024_65+0+0"
(II) NVIDIA(0):     "1280x1024_60+0+0"
(II) NVIDIA(0):     "1280x1024+0+0"
```So that's where I am again now. I entered the exact modelines I got with the cvt command into xorg.conf, so I don't see how that should be a problem.

Any help please?

---

### Post by auh2o on 2010-03-06
Since my last post, this has happened one more time (getting to the login screen at 800x600), but I just restarted again and all was fine. It's not a major annoyance, but I would really appreciate any input that could help me solve it once and for all. Also, I would like to be able to run a higher refresh rate than 65.

---

### Post by auh2o on 2010-03-07
Alright, today it was worse. It took four consecutive reboots and one complete power-off/on to get out of the 800x600 trap. Same error each time:
```

(WW) NVIDIA(0): No valid modes for "1280x1024_85+0+0"; removing.
(WW) NVIDIA(0): No valid modes for "1280x1024_75+0+0"; removing.
(WW) NVIDIA(0): No valid modes for "1280x1024_65+0+0"; removing.
(WW) NVIDIA(0): No valid modes for "1280x1024_60+0+0"; removing.
(WW) NVIDIA(0): No valid modes for "1280x1024+0+0"; removing.
```

Finally the 60 and 65 modes managed to get validated and I'm back to normal. I never know what the next reboot will bring, though.

---

### Post by auh2o on 2010-03-26
Well, it's finally time to put this thread to rest. I wondered above whether this may have really been a hardware problem, and it turns out it was. My old monitor gave up on me yesterday, so I swapped in a new monitor of the **exact** same model. Guess what? The monitor now properly sends its EDID, and *all* modes work. Marking this as solved! 'scuse me for taking up your time!

---

