---
title: "Display issues after installing nvidia drivers"
date: 2010-06-21
forum: General Help
---

### Post by skullkid2424 on 2010-06-21
Hey all,

I'm just starting out with ubuntu (10.04), and installed it using a live cd on my alienware m5500.  I had the update manager update everything, and then went looking on how to properly use my nvidia graphics card (geforce go 7600) because the graphics weren't looking very good, and I couldn't use any desktop effects.

I followed  [the directions found here]("https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia") in order to blacklist nouveou and enable the current nvidia driver.  However after rebooting, and every time I time I turn on the computer, it never makes it to the desktop, i usually end up seeing the ubuntu startup and/or the nvidia logo before it proceeds to one of several screens (none of which allow me to click or type, although sometimes i can move the mouse).
-black screen
-black screen with light gray bars top and bottom
-black screen with vertical green line
-orange and purple horizontal stripes
-purple and light purple horizontal stripes

Thinking that it could be one of the listed bugs from the directions, I followed the work around for "Screen Blanks/Monitor Turns Off", but the problem persists.  I have used the live disc to do a fresh install and attempt it about 3 times.  I have been unable to find anything online that helps.  

Anyone know what this could be, or have advice for troubleshooting?   Let me know if I can provide any other information that may prove useful - I'm fairly new to linux in general, but I can probably get some information from recovery mode if I've got a little guidance.

---

### Post by fooman on 2010-06-21
on a fresh install....have you tried enabling the current drivers, via "hardware drivers" in system > administration > hardware drivers *without blacklisting the nouveau drivers?*

---

### Post by xifer on 2010-06-21
> **skullkid2424 said:**
> 

  I had the update manager update everything, and then went looking on how to properly use my nvidia graphics card (geforce go 7600) because the graphics weren't looking very good, and I couldn't use any desktop effects.

I followed  [the directions found here]("https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia") in order to blacklist nouveou and enable the current nvidia driver. 

I'd suggest getting rid of ALL the nvidia current and everything else.  Just have the ones that say 185 in the package name.

Even then you might have a screwed up config file /etc/X11/xorg.conf so check if anything is customised in there for nvidia and remove it.  Once you get it working reasonably well you can look at tweaking xorg.conf to get compositing (desktop effects) working.

---

### Post by skullkid2424 on 2010-06-21
Thanks for the quick replies.

I'm doing a fresh install right now just to undo anything I might have messed up.  Once its ready I'll get updates and check out the hardware drivers.  If I remember right there are 3 nvidia ones (96, 173, and current) with current being recommended.  I'll activate the recommended one.

I'll be back once the install is done and post with the results.

---

### Post by skullkid2424 on 2010-06-21
Ok - Did fresh install.  Updated everything. Rebooted.  Activated nvidia current driver in hardware drives without out doing anything else.  Reboot.  Blank screen after ubuntu loading screen.

I rebooted about 5 times, got mostly blank screens, although one was a blank screen with a third of the screen blue (doubt that helps at all, but its not always a blank screen).

How would I go about removing nvidia drivers?  It would be nice to simply boot into recovery and remove nvidia drivers so that I don't have to do a fresh install every time I attempt to solve this.

Anything else to try?

EDIT:  Wow what? I've seen duplicate posts before but ignore the next 4 posts...

---

### Post by skullkid2424 on 2010-06-21
Duplicate post #1
Wonder how to delete all these...

---

### Post by skullkid2424 on 2010-06-21
Duplicate post #2

---

### Post by skullkid2424 on 2010-06-21
Duplicate post #3...

---

### Post by skullkid2424 on 2010-06-21
Duplicate post #4...not sure how that happened but sorry for the unintentional spam

And I'm actually going to turn this into a semi-useful post with my xorg.conf - it was mentioned that I could tweak this to help my graphics issue without the nvidia driver at all?

```
Section "Screen"
        Identifier        "Default Screen"
        DefaultDepth      24
EndSection

Section "Module"
        Load    "glx"
EndSection

Section "Device"
        Identifier        "Default Device"
        Driver    "nvidia"
        Option    "NoLogo"        "True"
EndSection

```

---

### Post by xifer on 2010-06-22
> **skullkid2424 said:**
> Ok - Did fresh install.  Updated everything. Rebooted.  Activated nvidia current driver in hardware drives without out doing anything else.  Reboot.  Blank screen after ubuntu loading screen.

I rebooted about 5 times, got mostly blank screens, although one was a blank screen with a third of the screen blue (doubt that helps at all, but its not always a blank screen).

How would I go about removing nvidia drivers?  It would be nice to simply boot into recovery and remove nvidia drivers so that I don't have to do a fresh install every time I attempt to solve this.

Anything else to try?

EDIT:  Wow what? I've seen duplicate posts before but ignore the next 4 posts...
like I said - use NVIDIA-185 NOT CURRENT. Remove the rest using any package manager - apt-get on the command line is probably your best option at this point.

If 185 doesn't work for you try the nvidia webseite
[http://www.nvidia.com/object/linux-display-ia32-195.36.31-driver.html](http://www.nvidia.com/object/linux-display-ia32-195.36.31-driver.html)

---

### Post by skullkid2424 on 2010-06-22
> **xifer said:**
> like I said - use NVIDIA-185 NOT CURRENT. Remove the rest using any package manager - apt-get on the command line is probably your best option at this point.

If 185 doesn't work for you try the nvidia webseite
[http://www.nvidia.com/object/linux-display-ia32-195.36.31-driver.html](http://www.nvidia.com/object/linux-display-ia32-195.36.31-driver.html)

installed 185 using 
```
sudo apt-get install nvidia-glx-185
```
seemed to install without any issues

i then tried to load it with 
```
sudo modprobe nvidia
```
but got "FATAL: Module nvidia not found."

i then tried to check it with
```
sudo lsmod | grep -i nvidia
```
and it gave me nothing


I am going about this right or do i simply restart from here to get it to work?

---

### Post by xifer on 2010-06-22
> **skullkid2424 said:**
> installed 185 using 
```
sudo apt-get install nvidia-glx-185
```
seemed to install without any issues

i then tried to load it with 
```
sudo modprobe nvidia
```
but got "FATAL: Module nvidia not found."

i then tried to check it with
```
sudo lsmod | grep -i nvidia
```
and it gave me nothing


I am going about this right or do i simply restart from here to get it to work?


If you haven't restarted then you do need to - the kernel needs to load the correct modules.  Also remove reference to nvidia module from your xorg.conf.

There is a package called nvidia-settings that can help in setting up the xorg.conf.  But that's for later - first try without anything specific in there.

You will get this working - I know it can be frustrating - i have a very old nvidia card in this pc and every upgrade breaks it!  Stick with it.

---

### Post by skullkid2424 on 2010-06-22
> **xifer said:**
> If you haven't restarted then you do need to - the kernel needs to load the correct modules.  Also remove reference to nvidia module from your xorg.conf.

There is a package called nvidia-settings that can help in setting up the xorg.conf.  But that's for later - first try without anything specific in there.

You will get this working - I know it can be frustrating - i have a very old nvidia card in this pc and every upgrade breaks it!  Stick with it.

Holy crap progress.  Thank you.  It rebooted successfully.  It automatically lowered the screen resolution, like it was doing before, but it actually successfully booted.  

Alright - now what do I do.  I have no xorg.conf file and I'm half afraid that my usual bumbling about will break it.

---

### Post by xifer on 2010-06-22
Excellent.  so it is working but in a basic configuration.

install the nvidia-settings package and run it.

```
sudo apt-get install nvidia-settings
```

It has an option to scan the hardware and autodetect correct settings, and write the xorg.conf for you.

Mostly that will work - certain monitors won't play nice - they won't report their capabilities - forcing you to set everything manually.

FYI, there are a heap of settings you can fiddle with to get compositing working and get the screen resolution you are after.

Here is my xorg.conf - you probably don't need everything that i have - my card is old and needed a lot of tweaking to make everything work.  But pay attention to the screen/module/Monitor and Device sections - if you are editing manually ensure the identifiers you use are consistent. the nvidia-settings program will give you a good starting point. Good luck!


```
Section "ServerLayout"
    Identifier     "Layout0"
    Screen      0  "Screen0" 0 0
EndSection

Section "Files"
EndSection

Section "Module"
    Load           "dbe"
    Load           "extmod"
        Load           "record"
    Load           "glx"
        Load    "dri"
        Load    "dri2"
EndSection

Section "ServerFlags"
        Option "Xinerama" "0"
        Option "DontZap" "False"
EndSection



Section "Monitor"
    # HorizSync source: edid, VertRefresh source: edid
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "HP L1906"
    HorizSync       30.0 - 83.0
    VertRefresh     50.0 - 76.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "Videocard0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce2 MX 100/200"
#       Option "PixmapCacheSize" "9000000"
        Option "Coolbits" "4"
        Option "RenderAccel" "true"
#       Option "AccelMethod" "XAA"
#       Option "OnDemandVBlankInterrupts" "true"
#       Option "AllowIndirectPixmaps" "true"
#       Option "AllowSHMPixmaps" "false"
        Option "BackingStore" "true"
        Option "DamageEvents" "true"
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Videocard0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "metamodes" "1280x1024 +0+0; 1152x864 +0+0; 1280x960 +0+0; 1024x768 +0+0; 800x600 +0+0; 832x624 +0+0"
    Option         "DPI" "96 x 96"
    Option         "NvAGP" "3"
    Option         "UseEvents" "on"
    Option         "AddARGBGLXVisuals" "True"
    Option         "AllowGLXWithComposite" "True"
    Option         "DPMS" "True"

    SubSection     "Display"

        Depth       24
        Modes      "1600x1200" "1280x1024" "1024x768" "800x600" "640x480"
    EndSubSection
EndSection

Section "Extensions"
        Option "Composite" "true"
        Option "RENDER" "true"
        Option "DAMAGE" "true"
EndSection

```

---

### Post by skullkid2424 on 2010-06-22
> **xifer said:**
> Excellent.  so it is working but in a basic configuration.

install the nvidia-settings package and run it.

```
sudo apt-get install nvidia-settings
```

It has an option to scan the hardware and autodetect correct settings, and write the xorg.conf for you.

Mostly that will work - certain monitors won't play nice - they won't report their capabilities - forcing you to set everything manually.

FYI, there are a heap of settings you can fiddle with to get compositing working and get the screen resolution you are after.


I broke it :(

Installed nvidia-settings and ran it - a message came up saying I needed to do "nvidia-xconfig" as root and then restart my xserver.  I did that and I'm back to having blank screens.  Rebooted several times and get same thing.  Did I mess up and can I run nvidia-settings from recovery (I'm not sure how I would go about this, used to the graphical program for it).


Pardon the random tangent, its not too important - when starting up theres a "pop" sound - what is that?  I would find it amusing if it is the kernel popping, but I don't know if it is or how amused I should be...

---

### Post by xifer on 2010-06-23
oh dear. never mind.  back to package manager.  get rid of everything. clear out xorg.conf.  install nvidia-185 ONLY again. restart.  When you get back to where you were.  run nvidia-settings and only use it to scan your hardware and create a new xorg.conf - don't let it do anything else - but you've learnt that now ;-)  i had the same problem once - on the nvidia website they offer a tool to do the complete install for you, choosing driver, reconfiguring kernel, reboot and reconfig xorg.  IT never worked.  Just do each stage yourself and make sure it is right before going onto the next one.

---

### Post by skullkid2424 on 2010-06-23
> **xifer said:**
> oh dear. never mind.  back to package manager.  get rid of everything. clear out xorg.conf.  install nvidia-185 ONLY again. restart.  When you get back to where you were.  run nvidia-settings and only use it to scan your hardware and create a new xorg.conf - don't let it do anything else - but you've learnt that now ;-)  i had the same problem once - on the nvidia website they offer a tool to do the complete install for you, choosing driver, reconfiguring kernel, reboot and reconfig xorg.  IT never worked.  Just do each stage yourself and make sure it is right before going onto the next one.

Alright i think i can do that - but how do i go about getting rid of everything?  Up until now I'm just been doing fresh installs, but I think this time I haven't screwed up that much.  I'm in recovery mode, but my lack of unix commands is coming into play.  I need to get rid of xorg.conf (and possibly xorg.conf.backup? does it automatically check for that if I don't have a xorg.conf?), nvidia-settings, and nvidia-185?

---

### Post by VanEyck on 2010-06-23
I think my problem is a little bit different than this one.

I used the text-based installer to install 10.4 on a new laptop (Sony Vaio) with an Nvidia graphics card.  And I think the video card is preventing me from seeing anything.

GRUB comes up and I select Ubuntu (I also have Windows on the machine).  Once I select Ubuntu, I get a black screen and I cannot do anything.  I cannot even see the word Ubuntu appear on the screen to show that it is loading.

I'm thinking that the graphics card is the problem, but I am not sure.  What can I do?

---

### Post by xifer on 2010-06-23
backup copies can be ignored - I'd remove or rename the xorg.conf 

 ```
mv xorg.conf xorg.old
```

and remove all the packages like this 

 ```
apt-get remove nvidia*
```


then install the 185 stuff again like you did before

```
apt-get install nvidia-glx-185
```

reboot and cross your fingers! but it should show the desktop.

then if the nvidia-settings program doesn't want to play properly and insists on running nvidia-xconfig and you can't get past it you'll need to find your monitors refresh rates and stuff yourself- should be available on the web

---

### Post by xifer on 2010-06-23
> **VanEyck said:**
> I think my problem is a little bit different than this one.

I used the text-based installer to install 10.4 on a new laptop (Sony Vaio) with an Nvidia graphics card.  And I think the video card is preventing me from seeing anything.

GRUB comes up and I select Ubuntu (I also have Windows on the machine).  Once I select Ubuntu, I get a black screen and I cannot do anything.  I cannot even see the word Ubuntu appear on the screen to show that it is loading.

I'm thinking that the graphics card is the problem, but I am not sure.  What can I do?

others have found that certain new laptops just will not play - i had the problem myself on a new Windows7 laptop at xmas and could only get black screen.  Almost like something deliberately blocked in the hardware api...  if you do <CTRL>-<ALT>-<F1> you might be able to log in and look for logs.  I never found the solution and didn't have time at the time as it were.

---

### Post by VanEyck on 2010-06-23
> **xifer said:**
> others have found that certain new laptops just will not play - i had the problem myself on a new Windows7 laptop at xmas and could only get black screen.  Almost like something deliberately blocked in the hardware api...  if you do <CTRL>-<ALT>-<F1> you might be able to log in and look for logs.  I never found the solution and didn't have time at the time as it were.

If I try installing an older version (ie. Jaunty) instead of Lucid, do you think it will work?

---

### Post by xifer on 2010-06-23
> **VanEyck said:**
> If I try installing an older version (ie. Jaunty) instead of Lucid, do you think it will work?

no,  more research is required to find the problem.  i suspect trickery on the part of the hardware manufacturer and microsoft.

i'd love to be proved wrong.

---

### Post by skullkid2424 on 2010-06-23
> **xifer said:**
> backup copies can be ignored - I'd remove or rename the xorg.conf 

 ```
mv xorg.conf xorg.old
```

and remove all the packages like this 

 ```
apt-get remove nvidia*
```


then install the 185 stuff again like you did before

```
apt-get install nvidia-glx-185
```

reboot and cross your fingers! but it should show the desktop.

then if the nvidia-settings program doesn't want to play properly and insists on running nvidia-xconfig and you can't get past it you'll need to find your monitors refresh rates and stuff yourself- should be available on the web

Ok - removed nvidia stuff and xorg.conf - its working properly again.  When I open nvidia-settings it gives me the nvidia-xconfig message, but I can click cancel and mess with the nvidia-settings.  However I'm not at all sure of what to do to have it write the xorg.conf based on my stuff...

Basically on the left side is a box that has only one option "nvidia-settings Configuration" and its highlighted.  On the right it has checkboxes for "Enable Tooltips", "Display Status Bar", "Slider Text Entries", "Include X Display Names in the Config File", and "Show 'Really Quit?' Dialog".  All of those are checked by default except "include x display names..."  Theres a "Save Current Configuration" and "Quit" button, along with a help button that explains what the check options are for.

The only thing I can really see to do would be click "Save Current Configuration", but I haven't seen any settings or anything that makes me think "detect hardware capabilites".  

Bleh, sorry for being so inexperienced, and thanks again for the help.

---

### Post by xifer on 2010-06-23
> **skullkid2424 said:**
> Ok - removed nvidia stuff and xorg.conf - its working properly again.  When I open nvidia-settings it gives me the nvidia-xconfig message, but I can click cancel and mess with the nvidia-settings.  However I'm not at all sure of what to do to have it write the xorg.conf based on my stuff...

Basically on the left side is a box that has only one option "nvidia-settings Configuration" and its highlighted. 
Bleh, sorry for being so inexperienced, and thanks again for the help.
hmm - mine shows lots of options on the left box - not just nvidia-settings configuration. It has the option 'x-server display configuration' which when clicked, opens up on the right a page containing a button 'Detect displays' and one labelled 'save to x configuration file'.

So, again i say: hmm.


Ok, so maybe we have to take a different tack and create xorg.conf manually.  Get your monitor model details and websearch for the refresh rates etc - use the xorg.conf i posted above as a start but get the right numbers in the monitor and device sections.


might be worth re-installing nvidia-settings again - just to make certain it knows about your current module - i'm guessing now tho - hope someone that knows more might show up!

---

### Post by skullkid2424 on 2010-06-23
> **xifer said:**
> hmm - mine shows lots of options on the left box - not just nvidia-settings configuration. It has the option 'x-server display configuration' which when clicked, opens up on the right a page containing a button 'Detect displays' and one labelled 'save to x configuration file'.

So, again i say: hmm.


Ok, so maybe we have to take a different tack and create xorg.conf manually.  Get your monitor model details and websearch for the refresh rates etc - use the xorg.conf i posted above as a start but get the right numbers in the monitor and device sections.


might be worth re-installing nvidia-settings again - just to make certain it knows about your current module - i'm guessing now tho - hope someone that knows more might show up!

Alas I think I'm giving up...There seems to very little information on my display, and it isn't even in the laptop's user manual.  Using xrandx and ddcprobe didn't get me much, it got to edid and it failed.  Guessing and using default values to create a xorg.conf from your information didn't work.  Using "Xorg -configure" while in recovery mode to create a xorg.conf would partially load the desktop and freeze - the mouse can still move, but no clicking or typing has any effect.  I'm thinking I'll have to go without the fancy graphics.  If theres any more ideas let me know, but I think I'm about done.

Thanks for your help and patience though - I learned quite a bit about linux and ubuntu that will certainly be useful down the road.

---

### Post by xifer on 2010-06-24
> **skullkid2424 said:**
> Alas I think I'm giving up...There seems to very little information on my display, and it isn't even in the laptop's user manual.  Using xrandx and ddcprobe didn't get me much, it got to edid and it failed.  Guessing and using default values to create a xorg.conf from your information didn't work.  Using "Xorg -configure" while in recovery mode to create a xorg.conf would partially load the desktop and freeze - the mouse can still move, but no clicking or typing has any effect.  I'm thinking I'll have to go without the fancy graphics.  If theres any more ideas let me know, but I think I'm about done.

Thanks for your help and patience though - I learned quite a bit about linux and ubuntu that will certainly be useful down the road.

i'm sorry to hear that.  annoying when it's only one step away from working.  I found this site useful before
 [http://www.linlap.com/](http://www.linlap.com/)

the information must be out there somewhere.

---

