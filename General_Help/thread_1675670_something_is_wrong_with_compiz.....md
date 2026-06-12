---
title: "something is wrong with compiz...."
date: 2011-01-25
forum: General Help
---

### Post by u-noob-tu on 2011-01-25
just a few minutes ago i was looking through the window animations section of compiz config, and i enabled random effects for all events. as soon as i exited config, all my effects were disabled (and still are). confused, i tried re-enabling them, but they were all still checked. so i went to preferences>appearance and enabled effects through there. suddenly a small window popped up and said "looking for drivers". nothing happened after that, but i did have to log out once because the window borders disappeared. and this might not be related, but i lost my wifi connection for seemingly no reason while this happened. i only got it back by disconnecting and reconnecting. i tried removing and reinstalling compiz but it had kept all my settings so nothing changed. im kinda confused bcuz this is a fresh ubuntu install and i havent done anything with drivers. and all the effects i had enabled before worked just fine. any ideas?

---

### Post by u-noob-tu on 2011-01-26
okay, i got some more info on my problem. compiz will suddenly stop working at random times while im on my computer (so far as i can tell nothing is triggering it). i read online that if this happens you should run compiz in the teminal. this is only a temporary fix, and often results in disappearing window borders. also people have said they get errors when running compiz in the terminal. i get no errors, it just runs. i have no idea what made compiz go wonky. any ideas?

---

### Post by Krytarik on 2011-01-26
Try to remove/rename both directories, "~/.compiz" and "~/.gconf/apps/compiz". Note that this will unset all your Compiz settings.

---

### Post by u-noob-tu on 2011-01-26
> **Krytarik said:**
> Try to remove/rename both directories, "~/.compiz" and "~/.gconf/apps/compiz". Note that this will unset all your Compiz settings.

just did that, and nothing changed. my settings are all still there.

EDIT* it would seem that compiz is running without those folders. i ran compiz from the terminal and the effects came back, but not for long. its like its running from somewhere else.

---

### Post by Krytarik on 2011-01-26
Those should be all the relevant directories.

Please do this:

- logout
- switch to console by pressing Alt+Ctrl+F1
- login there
- remove those directories again, with "rm -rf DIR"
- switch back to GDM by pressing Alt+Ctrl+F7 or F8
- login there again

---

### Post by u-noob-tu on 2011-01-26
> **Krytarik said:**
> Those should be all the relevant directories.

Please do this:

- logout
- switch to console by pressing Alt+Ctrl+F1
- login there
- remove those directories again, with "rm -rf DIR"
- switch back to GDM by pressing Alt+Ctrl+F7 or F8
- login there again

thats a no go. it reset the settings but the same thing happened once i opened the config window. do you think that if i did this command again and then reinstalled compiz it might solve the issue?

---

### Post by Krytarik on 2011-01-26
> **u-noob-tu said:**
> thats a no go. it reset the settings but the same thing happened once i opened the config window. do you think that if i did this command again and then reinstalled compiz it might solve the issue?
No, I don't think so. Let's have a deeper look then.

- look into "/var/log/Xorg.0.log" and "~/.xsession-errors" for error messages
- what video card/chip is installed?
- what driver are you running?
- how did you install those?

---

### Post by u-noob-tu on 2011-01-27
> **Krytarik said:**
> No, I don't think so. Let's have a deeper look then.

- look into "/var/log/Xorg.0.log" and "~/.xsession-errors" for error messages
- what video card/chip is installed?
- what driver are you running?
- how did you install those?

hey, sorry it took me so long to reply, i was busy yesterday. my video chip is an intel i965 (it has a lot of other names, like x3100 or gm45) with mesa 7.9, i believe, which ubuntu set up by default. this was the only error i could find in xorg.0.log (i searched for the word "error" and i only got one result).```
 WW) warning, (EE) error, (NI) not implemented, (??) unknown.
``` other than that, i dont see anything that doesnt look right. as for ~/.xsession-errors, it seems i dont have that directory. no search could find it. im not sure whats changed. i havent messed with any drivers or anything.

EDIT* i might have found the problem. i had a ppa enabled that, for some reason, had installed some drivers for ATI and nvidia cards. removing those seems to have fixed the problem. ill keep you posted, though, if anything changes.

EDIT2* nope, problem came back. screen flickers for a moment and compiz effects stop.

---

### Post by Krytarik on 2011-01-27
As for the Xorg.0.log, look more careful, or post it here, in code-tags (#) or as attachment (probably archive).

The file ".xsession-error" is located in your home directory, therefore "~/".;-)

---

### Post by u-noob-tu on 2011-01-28
> **Krytarik said:**
> As for the Xorg.0.log, look more careful, or post it here, in code-tags (#) or as attachment (probably archive).

The file ".xsession-error" is located in your home directory, therefore "~/".;-)

sorry again for being late in responding. okay heres the entire Xorg.0.log. its pretty big so i compressed into a .gz file. i looked all throughout my home folder for .xsession-error and its not there. does that mean im not getting errors and one hasnt been made?

EDIT* in the meantime, i think i have found a temporary fix. i got the compiz fusion icon app from the software center so i can restart compiz as needed. still crashes a lot though.

---

### Post by Habitual on 2011-01-28
I had to use a desktop launcher for "compiz --replace" when I had a similar problem.

I changed themes and the issue went away.

---

### Post by Krytarik on 2011-01-28
I've missed a letter in my previous post, the file is actually called *".xession-errors"*, it shouldn't matter anyways, if you searched the directory. I don't have an idea why the file isn't there, usually minor errors are logged regularly.

As for your Xorg.0.log, I also don't see any serious error messages, but I'm bit concerned about the repeated statements of the monitor modes. It may make sense to create a "xorg.conf" and specify the values there.
[https://wiki.ubuntu.com/X/Config/Resolution](https://wiki.ubuntu.com/X/Config/Resolution)

You may also  try to upgrade the video driver to those provided by Ubuntu-X-Swat:
```
sudo add-apt-repository ppa:ubuntu-x-swat/x-updates
sudo apt-get update
sudo apt-get upgrade
```EDIT: Yeah, +1 for trying another theme (Habitual posted his/her message while I was composing mine, and studying your log).

---

### Post by u-noob-tu on 2011-01-28
i managed to find an .xsession-errors file (i thought it was a folder, thats why i didnt find it at first). its pretty big. one thing i noticed while looking at it is that it says "unable to find /usr/share/themes/human/" i looked there and i dont have a theme called human. then why is it looking for it? interestingly, on my previous install of ubuntu, i never had any issues with compiz and never even had xorg.conf. ill try making one though, to see if it helps. 

and changing the theme does not work.

wait a second, i just realized that at about the same time compiz stopped working i started using an external monitor with a higher resolution. and so far as i can remember, it has only happened while using that monitor. could that be the reason?

---

### Post by Krytarik on 2011-01-28
> **u-noob-tu said:**
> it says "unable to find /usr/share/themes/human/"

and changing the theme does not work.

Do you have a directory "Human" in the themes dir then? What theme do you currently use? Does the re-appear if you use any other theme than "Human"?
> **u-noob-tu said:**
> wait a second, i just realized that at about the same time compiz stopped working i started using an external monitor with a higher resolution. and so far as i can remember, it has only happened while using that monitor. could that be the reason?
That could be the root cause. When I set up a second monitor (TV) at my mum's machine, I experienced that desktop effects get disabled by default. Only after setting up another screen via xorg.conf Compiz is working at least at the main monitor, I believe I didn't check the TV. If you want to enable Compiz in that way, follow this guide:
[https://wiki.archlinux.org/index.php/Xorg#Multiple_monitors.2FDual_screen](https://wiki.archlinux.org/index.php/Xorg#Multiple_monitors.2FDual_screen)

---

### Post by u-noob-tu on 2011-01-28
okay, i made a xorg.conf. havent tried it with my second monitor yet, i want to make sure its all figured out with my primary display first. the link you gave me was for configuring dual screens with an nvidia chip. i have an intel (im not sure if i mentioned that). there was a link to an intel section, but it had nothing about dual displays. ill post my xorg.conf so you can take a look at it. the section "device" doesnt seem to have any defaults. im guessing X couldnt detect any. ```
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
    Load  "extmod"
    Load  "dri"
    Load  "record"
    Load  "dbe"
    Load  "glx"
    Load  "dri2"
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
        #Option     "AccelMethod"            # [<str>]
        #Option     "DRI"                    # [<bool>]
        #Option     "ColorKey"               # <i>
        #Option     "VideoKey"               # <i>
        #Option     "FallbackDebug"          # [<bool>]
        #Option     "Tiling"                 # [<bool>]
        #Option     "Shadow"                 # [<bool>]
        #Option     "SwapbuffersWait"        # [<bool>]
        #Option     "XvMC"                   # [<bool>]
        #Option     "XvPreferOverlay"        # [<bool>]
        #Option     "DebugFlushBatches"      # [<bool>]
        #Option     "DebugFlushCaches"       # [<bool>]
        #Option     "DebugWait"              # [<bool>]
        #Option     "HotPlug"                # [<bool>]
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
```EDIT* im not sure if it was taking out the vga cable for the external monitor or making xor.conf that solved the issue, but compiz has been working for a solid hour now. id like to get the second display to work (its a 22" 1690x1050 res lcd. very nice), but it wont be a big deal if i cant use it.

EDIT2* okay, problem is back. i opened up the software center and the screen flickered, and once again, had to restart compiz.

EDIT 3* i went through my installed software to see if i saw anything that might be causing the compiz bug, and i found some stuff that came from the x updates ppa (though i dont remember installing them). heres the list of things that are there: intel-gpu-tools (might have been preinstalled), libdrm-dev, libdrm-intel1, libdrm-nouveau1 (this one needs to go i think), libdrm-radeon1 (have no idea why this is installed. i have intel), libdrm2, libkms1, and xserver-xorg-video-intel (im pretty sure i need this one). i clicked on uninstall on the radeon one and it said that if it was removed then it would also uninstall plymouth, which, if im not mistaken, is necessary for the bootloader. not sure what to do about this.

---

### Post by Krytarik on 2011-01-28
The dual monitor setup in the guide is not *that* Nvidia specific, I use almost exact those setup for the dual monitor config at my mum's machine, and there is an ATI card installed. The only Nvidia specific option is "TwinView" and maybe the value of "Xinerama", which is otherwise also mentioned as "true" and "on", you may try them all.

Where did you get those entries of your current draft? I deleted the parts which should not be necessary, and commented those where you should add/change something.
```
Section "ServerLayout"
    Identifier     "X.org Configured"
    Screen      0  "Screen0" 0 0
EndSection

Section "Module"             [COLOR=Red]# this section may be completely not necessary[/COLOR]
    Load  "extmod"
    Load  "dri"
    Load  "record"
    Load  "dbe"
    Load  "glx"
    Load  "dri2"
EndSection

Section "Monitor"
    Identifier   "Monitor0"
    VendorName   "Monitor Vendor"
    ModelName    "Monitor Model"
[COLOR=Red]    HorizSync       30.0 - 107.0          # you have to enter your specific values here
    VertRefresh     48.0 - 120.0         # see guides below
    Modeline "1280x1024_60.00" 108.88 1280 1360 1496 1712 1024 1025 1028 1060 -HSync +Vsync Option
    "PreferredMode" "1280x1024_60.00"
[/COLOR]EndSection

Section "Device"
    Identifier  "Card0"
    Driver      "intel"
[COLOR=Red]    BusID       "PCI:0:2:0"      # remove that if you are not really sure that it is correct
[/COLOR]EndSection

Section "Screen"
    Identifier "Screen0"
    Device     "Card0"
    Monitor    "Monitor0"
[COLOR=Red]    DefaultDepth    24
[/COLOR]    SubSection "Display"
        Depth     24
[COLOR=Red]        Modes    "1280x1024" "1024x768"       # set your preferred mode(s) here
[/COLOR]    EndSubSection
EndSection
```To get the specific values of "HorizSync" and "VertRefresh" of your monitor(s):
```
sudo apt-get install hwinfo
hwinfo --monitor
```To get the correct "Modeline" follow this guide:
[https://wiki.ubuntu.com/X/Config/Resolution#Adding%20undetected%20resolutions]("https://wiki.ubuntu.com/X/Config/Resolution#Adding%20undetected%20resolutions")

---

### Post by Krytarik on 2011-01-28
> **u-noob-tu said:**
> i went through my installed software to see if i saw anything that might be causing the compiz bug, and i found some stuff that came from the x updates ppa (though i dont remember installing them).
How do you know that they are from Ubuntu-X-Swat's PPA, what packages do you mean?
But you didn't activate the PPA following my suggestion? Maybe before?
> **u-noob-tu said:**
> 
heres the list of things that are there: intel-gpu-tools (might have been preinstalled), libdrm-dev, libdrm-intel1, libdrm-nouveau1 (this one needs to go i think), libdrm-radeon1 (have no idea why this is installed. i have intel), libdrm2, libkms1, and xserver-xorg-video-intel (im pretty sure i need this one). i clicked on uninstall on the radeon one and it said that if it was removed then it would also uninstall plymouth, which, if im not mistaken, is necessary for the bootloader. not sure what to do about this.
Though I haven't explicitly checked, I believe that all those packages are pre-installed. If you indeed  somehow activated Ubuntu-X-Swat's PPA, some of those may got updated.

The driver for your chip is actually called "xserver-xorg-video-intel", I guess you meant those. Leave all those packages as they are, even if it seems that you don't need them. And yes, Plymouth is the graphical boot splash.

I forgot to mention in my previous post: You did indeed already say that you have an Intel chip, I took that into account.

---

### Post by u-noob-tu on 2011-01-29
im having trouble finding the refresh rate for the screen. the "hwinfo" command strangely does nothing. i think everything else looks okay. ill post it here so you can take another look at it. 

thanks for all the help. i noticed youre from berlin. i am actually teaching myself german (i can barely say hello, lol) mostly because i have family in nuremburg. its pretty fun. :P

---

### Post by Krytarik on 2011-01-29
```

Section "Monitor"
    Identifier   "Monitor0"
    VendorName   "Monitor Vendor"
    ModelName    "Monitor Model"
[COLOR=Red]    HorizSync       30.0 - 107.0          # you have to enter your specific values here
    VertRefresh     48.0 - 120.0         # see guides below
[/COLOR][COLOR=Red]    Modeline "1440x900"x0.0  109.50  1440 1510 1550 1974  900 901 904 912 -hsync -vsync Option
    "PreferredMode" "1440x900_55.50"
[/COLOR]EndSection

```How did you get those values for Modeline?
If you really want to use 55,5 Hz, maximize your terminal, enter those command to get the correct values, and then simply copy&paste it:
```
cvt 1440 900 55.50
```Regarding "hwinfo": Did you follow exactly the commands I posted?

If it still doesn't work, enter the following command, then press "Cancel" (!):
```
xvidtune
```Where do you live then, if I may ask that?

---

### Post by u-noob-tu on 2011-01-29
i looked through xorg.0.log and found that line in there. it looked like what i was looking for. the "xvidtune" command showed the refresh rates. 

i live in the US. Virginia, to be exact.

EDIT* okay, i think ive had a major issue happen. i was looking around the internet trying to find a fix for this when suddenly the screen went black and a lot of text showed up. it only lasted about one second so i couldnt read anything. i went and checked some logs and this is what i found in daemon.log.```
 Jan 29 16:32:17 ryan-Studio-1737 AptDaemon: INFO: Quiting due to inactivity
Jan 29 16:32:17 ryan-Studio-1737 AptDaemon: INFO: Shutdown was requested
``` it was at the very bottom of the log (meaning most recent), and note how the time is exactly the same. it happened once after this so i turned off compiz all together and went to metacity. havent been using that long enough to know if compiz is the issue or if there is something else to blame. it would seem to me (in my very limited knowledge) that X had crashed and recovered almost instantly (i was immediately brought to the login screen). also, upon going to google in firefox i noticed that things didnt look quite right. ive attached a screenshot of the google logo to show what i mean (note how the logo looks quite large and out of focus/pixelated). it looked as though the resolution had suddenly been changed, but the monitor settings hadnt changed. now things look normal again, but this is a bit concerning. :sad:

---

### Post by Krytarik on 2011-01-30
> **u-noob-tu said:**
> ```
 Jan 29 16:32:17 ryan-Studio-1737 AptDaemon: INFO: Quiting due to inactivity
Jan 29 16:32:17 ryan-Studio-1737 AptDaemon: INFO: Shutdown was requested
```
This seems to be completely unrelated to your issue.
[https://launchpad.net/aptdaemon](https://launchpad.net/aptdaemon)

Whereas the glitch in the screenshot is a further indication of either an issue with the video driver or the monitor settings.

You didn't see any serious error messages in the mentioned logs? Please check also "/var/log/Xorg.0.log.old", I realized today that "Xorg.0.log" is always only the log of the currently running xserver session.

PS: Please don't add such important things long after posting your original message, because the subscribed members doesn't get notified about *edits*. It was only coincidence that I noticed it.

---

### Post by u-noob-tu on 2011-01-30
im inclined to think that as soon as i started using that external monitor (which i am no longer using) it did something to X that would cause it to stop, or restart when triggered (i dont know by what though). i havent been using compiz for awhile and that seems to have negated the problem. but then theres the question of: is compiz messing up or X? 

and im not so sure about the driver because compiz had been working fine before the external monitor. 

i found the Xorg.0.log.old file but have no idea how to open it. what program could i use?

---

### Post by dino99 on 2011-01-30
all logs can be opened either by:
- right clic to choose a way
- double clic on it

---

### Post by Krytarik on 2011-01-30
> **u-noob-tu said:**
> 
i found the Xorg.0.log.old file but have no idea how to open it. what program could i use?
Right-click at it, choose "Open with Other Application...", then choose "gedit", uncheck "Remember this application...", then "Open" obviously.

To get it right: If you connect your external monitor during a session, xserver crashes/restarts. If it is connected before a session, either after a crash or after normal boot, you can't enable Compiz. Is that right?

In either case, if you want to enable Compiz also when the external monitor is connected, you have to set up a proper xorg.conf. Follow the discussed guides therefore.

---

### Post by u-noob-tu on 2011-01-30
i havent used the external monitor for a couple days, and the flickers/restarts have continued anyway. though it seems that the external monitor started the whole thing. i can enable compiz, but after a few minutes, it stops (seemingly at random, though it seems to happen mostly when minimizing/maximizing/closing and moving windows. i didnt think much of it when it happened, but another thing i should probably note is that when i tried to use the external monitor as an extra display, it would work until i used the keyboard (at which point it would use the laptop monitor only). it wouldnt work with both, only one or the other. that might have been what caused all this, somehow messing with the monitor. and i opened up the Xorg.0.log.old file and found a lot of lines referring to "EDID", which stands for external display identification data. heres what the log says:  ```
(II) intel(0): EDID vendor "LPL", prod id 0
[ 67328.824] (II) intel(0):     EDID quirk: Detailed timings give vertical size in cm.
[ 67328.824] (II) intel(0): Printing DDC gathered Modelines:
[ 67328.824] (II) intel(0): Modeline "1440x900"x0.0  109.50  1440 1510 1550 1974  900 901 904 912 -hsync -vsync (55.5 kHz)
```
and it repeats a couple more lines down. if im correct, it would seem that my computer is either still looking for that extra display and not using this one correctly, or it is trying to apply the settings for the external to my main monitor (which might explain the "55.5" khz number when the main monitor doesnt go lower than 60 khz). this is quite odd.

---

### Post by Krytarik on 2011-01-30
Like I pointed out earlier:
> **Krytarik said:**
> 
As for your Xorg.0.log, I also don't see any serious error messages, but I'm bit concerned about the repeated statements of the monitor modes. It may make sense to create a "xorg.conf" and specify the values there.
[https://wiki.ubuntu.com/X/Config/Resolution](https://wiki.ubuntu.com/X/Config/Resolution)

Where do you get those 55.50 Hz from then?

---

### Post by u-noob-tu on 2011-01-30
> **Krytarik said:**
> Like I pointed out earlier:

Where do you get those 55.50 Hz from then?

from the Xorg.0.log.old file. that section is repeated about 7 times in the log.

---

### Post by Krytarik on 2011-01-30
> **u-noob-tu said:**
> from the Xorg.0.log.old file. that section is repeated about 7 times in the log.
Oh, at the end of those line. :-)

---

### Post by u-noob-tu on 2011-01-30
oh yeah, im still working on the xorg.conf by the way.

---

### Post by u-noob-tu on 2011-01-31
just an update on things: i decided to try using the external monitor again yesterday without using compiz (using metacity at the moment), and no crashes at all. which still leaves me confused: is compiz not working? is X not working? or are they both not working? 

also the picture of the google logo i posted is still confusing me. if i right click on it (in firefox) and hit open image, it will display properly with no fuzziness. it only seems the be the logo and a few other things on google, which is puzzling.  :confused:

---

### Post by Krytarik on 2011-01-31
Compiz doesn't work with an -unconfigured- dual monitor setup, like I said. If X were not working, you wouldn't have a desktop at all.

Regarding the Google logo: It may be a misconfiguration of Firefox what causes this, try the following:
- "View -> Zoom -> Reset"
- open it with another browser

---

### Post by u-noob-tu on 2011-01-31
> **Krytarik said:**
> Compiz doesn't work with an -unconfigured- dual monitor setup, like I said. If X were not working, you wouldn't have a desktop at all.

Regarding the Google logo: It may be a misconfiguration of Firefox what causes this, try the following:
- "View -> Zoom -> Reset"
- open it with another browser

so, the monitor is the cause, then? if thats true, what can i do to fix it?

---

### Post by Krytarik on 2011-01-31
> **u-noob-tu said:**
> so, the monitor is the cause, then? if thats true, what can i do to fix it?
Proceed with setting up a proper xorg.conf:
> **Krytarik said:**
> That could be the root cause. When I set up a second monitor (TV) at my  mum's machine, I experienced that desktop effects get disabled by  default. Only after setting up another screen via xorg.conf Compiz is  working at least at the main monitor, I believe I didn't check the TV.  If you want to enable Compiz in that way, follow this guide:
[https://wiki.archlinux.org/index.php/Xorg#Multiple_monitors.2FDual_screen](https://wiki.archlinux.org/index.php/Xorg#Multiple_monitors.2FDual_screen)
What about the Google glitches?

---

### Post by u-noob-tu on 2011-01-31
The google thing must be a bug in either firefox 3.6 or google, because it looks it looks fine in firefox 4 b10. I'll ask if I have any more questions about xorg. Thanks for all your help. I really appreciate it.

---

### Post by Krytarik on 2011-01-31
You're welcome!

Btw., Google gets displayed by FF3 at my system. Are you running the 32-bit or the 64-bit version of Ubuntu/Firefox?

---

### Post by u-noob-tu on 2011-02-01
i have tried as hard as i could, but making the xorg.conf is just too far over my head. the guide you gave me is good, but im finding that its tough to figure out what to fill in the blanks with. if youre not already fed up with my thick head :p, i can give you all the information about my monitors and you can show me exactly what to put in and where to put it. i cant thank you enough man, vielen dank!

oh yeah, and im using 32 bit ubuntu/firefox.

---

### Post by Krytarik on 2011-02-01
Ok, lets start from your last scratch, I add what is necessary for the second monitor, and make notes to those which needs to be though of and/or adapted:
```
Section "ServerLayout"
    Identifier     "X.org Configured"
    Screen      0  "Screen0" 0 0
    Screen      1  "Screen1" RightOf "Screen0"
    Option         "Xinerama" "true"
EndSection

Section "Monitor"
    Identifier   "Monitor0"
[COLOR=Blue]    HorizSync    30.0 - 107.0          # 1a
    VertRefresh  48.0 - 120.0         # 1a
    Modeline                                    # 3a
    Option      "PreferredMode" "1440x900_55.50"  #4a
[/COLOR]EndSection

Section "Monitor"
    Identifier   "Monitor1"
[COLOR=Blue]    HorizSync    30.0 - 107.0          # 1b
    VertRefresh  48.0 - 120.0         # 1b
    Modeline                                    # 3b
    Option      "PreferredMode" "1440x900_55.50"  #4b
[/COLOR]EndSection

Section "Device"
    Identifier  "Card0"
    Driver      "intel"
    Screen      0
EndSection

Section "Device"
    Identifier  "Card1"
    Driver      "intel"
    Screen      1
EndSection

Section "Screen"
    Identifier "Screen0"
    Device     "Card0"
    Monitor    "Monitor0"
    DefaultDepth    24
    SubSection "Display"
        Depth     24
        Modes    "1440x900"
    EndSubSection
EndSection

Section "Screen"
    Identifier "Screen1"
    Device     "Card1"
    Monitor    "Monitor1"
    DefaultDepth    24
    SubSection "Display"
        Depth     24
[COLOR=Blue]        Modes    "1440x900"      # 2b
[/COLOR]    EndSubSection
EndSection

```First, onnect your external monitor.

1a/1b: get the specific specs of your monitor
- xvidtune
- manual/website

2b: What resolution do you want to set for your external monitor?

3a/3b: What refresh rate do you need/want to set?
- for LCDs 60 Hz is preferable
- for CRTs I recommend something above 75 Hz

3a: copy&paste the result of the following command in that field, maximize the terminal before:
```
cvt 1440 900 <3a>
```3b: like the above, with your desired values

4a/4b: put the values from the start of the above calculated modelines (between the " ") into those fields

---

