---
title: "Dual Monitors: Fullscreen goes on the wrong monitor"
date: 2010-04-11
forum: General Help
---

### Post by johnharris85 on 2010-04-11
I've got a dual monitor setup. The primary one is 1360*768 and the other is 1024*768. When I fullscreen a video on the web (e.g. [http://www.bbc.co.uk/iplayer/episode/b00rvwsx/Have_I_Got_News_for_You_Series_39_Episode_1/](http://www.bbc.co.uk/iplayer/episode/b00rvwsx/Have_I_Got_News_for_You_Series_39_Episode_1/)) it fullscreens to the smaller (non-primary) monitor, but cuts some off the right hand side, as if it is fullscreening the right size to display on the bigger monitor, but instead does it on the smaller one. It happens with any web video, if I click the fullscreen button on the player, it moves it fullscreen to the other monitor. Anyone got any ideas?

John

---

### Post by thebigob on 2010-04-11
I have also experienced this its is really annoying. I dont know the proper answer however a work around is just to switch off the other monitor temporarily. you can do this in system -> preferences -> display then check the off button this will set the only monitor as the one you want to full screen then it works. Lame workaround but handy for putting iplayer on the tv when you have a latop monitor that you cant unplug.

---

### Post by cblah001 on 2010-05-19
I am running into a similar problem. I want to use my second monitor to watch videos while I do other things on my laptop monitor. When I full screen a video on the second monitor, it switches over to my primary monitor and goes full screen.

---

### Post by mayliffe on 2010-06-26
I've just got my monitor added to my laptop setup and tried this. Using Twinview, full screen seems to display on the left hand monitor, regardless of which one is the primary. Now I may have to rearrange my desk if not my study. Ho hum.

---

### Post by premodern on 2010-06-28
I have the same problem and it is very annoying. 

Looking forward to a solution.

---

### Post by V.V.V. on 2010-06-29
Hello everyone! 
I've been having the same problem. 
My configuration is: Left monitor - 1280x1024, right, primary - 1920x1080. 
When I was trying to go fulscreen with an online video, it appeared on the left monitor with the proportions of the total size of two displays ((1280+1820)x1080). Now my problem is solved and the fulscreen video opens at my primary display.
I don't fully understand what has solved the problem, but I'll describe the steps I've taken before geting it working. Maybe somebody will find it helpfull.

1. Configure the XServer. This is a configuration that works for me:[INDENT]```
Section "ServerLayout"
    Identifier     "Layout0"
    Screen 0       "ScreenBig" 1280 0
    Screen 1       "ScreenSmall" RightOf "ScreenBig"
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
EndSection

Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "Samsung SyncMaster"
    HorizSync       30.0 - 81.0
    VertRefresh     56.0 - 75.0
    Option         "DPMS"
EndSection

Section "Monitor"
    Identifier     "Monitor1"
    VendorName     "Unknown"
    ModelName      "Samsung SyncMaster"
    HorizSync       30.0 - 81.0
    VertRefresh     56.0 - 75.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce GTX 260"
    Option         "ConnectedMonitor" "dfp, dfp"
    Option       "TwinView" "1"
    Option         "TwinViewXineramaInfoOrder" "DFP-1"
    Option         "Metamodes" "DFP-0: 1280x1024 +0+0, DFP-1: 1920x1080 +1280+0; DFP-0: NULL, DFP-1: 1920x1080 +0+0"
EndSection

Section "Screen"
    Identifier     "ScreenBig"
    Device         "Device0"
    Monitor        "Monitor1"
    DefaultDepth    24
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection

Section "Screen"
    Identifier     "ScreenSmall"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection
```[/INDENT]2. Install devilspie from ubuntu software center and it's GUI from [here]("http://code.google.com/p/gdevilspie/downloads/list3"). In the gDevilspie create a new configuration that will change the fullscreen window geometry:

[LIST]
[*]    Run gDevilspie, open some video in browser. Place gDevilspie window on the right monitor
[*]    Click Add
[*]    Set the video fullscreen
[*]    Click "Get" in gDevilspie. It will show you the list of all the opened windows. Remember that list, click "Get" without fullscreen video opened, compare the result, the missing window is the fullscreen video window. (If you use firefox the fullscreen window name is "Firefox")
[*]    On the "Matching" tab check "window_name", enter your fullscreen window's name into the "equal(s)" edit.
[*]    On the actions tab check "geometry" and fill all the edits. (for my configuration: xposition=1280, heigth=1080, width=1820)
[*]    On the "Raw" tab you've got to get something like this:
[/LIST]
[INDENT]    ( if 
    ( begin 
    ( is ( window_name ) "Firefox" )
    ) 
    ( begin 
    ( geometry "1920x1080+1280+" )
    ( println "match" )
    )
    )[/INDENT]
[LIST]
[*]    Click "Save" and restart the devilspie daemon.
[/LIST]
4. Now the fullscreen video got to open at the monitor you want (at the specified in devilspie position). The last problem is that the proportions of the video do not match the monitor ones. And I don't know how I've got it solved, but the only one I've done is updating system an browser and rebooting.
Now I've got a fullscreen video on my primary (right) monitor and it has correct proportions.

PS: [This problem is a bug in flashplayer ]("http://bugs.adobe.com/jira/browse/FP-562")[SIZE=1][Created: ]("http://bugs.adobe.com/jira/browse/FP-562")[08/19/08 01:28 PM. Please vote to get it solved]("http://bugs.adobe.com/jira/browse/FP-562")
[/SIZE]

---

### Post by UltraAnders on 2010-10-27
This more or less works for me. The full-screen window from Firefox now opens on the monitor I want it to. However it displays in the resolution of whichever screen the main Firefox window is on (which it was it was doing before thinking about it). My full-screen window is called "<Unknown>".

---

### Post by V.V.V. on 2010-11-05
Nice little workaround of this problem for Chrome users: [Window Expander For YouTube]("https://chrome.google.com/extensions/detail/fkpaakpeehepibjpdmoocdaonognfiog")

---

### Post by shad0wslay3r on 2011-01-01
When I try to "get" the new fullscreen window, no new windows show up in the list.  I'm using chrome, and tried just using the name of the current window but that didn't work.  are there any other known solutions for this?

---

### Post by shad0wslay3r on 2011-01-03
bump

---

### Post by F.G. on 2011-01-03
hi,
sorry if this seems a silly question. I can't figure out how to configure Xserver.  I gather that the file you need to edit is etc/X11/xorg.conf ?? or something like this. however I don't seem to have that file. am I looking in the right place?
thanks for any help.

---

### Post by shad0wslay3r on 2011-01-03
Just figured this out:

Just right clicking the desktop -> change Desktop Background -> Visual Effects -> None

Now I can watch Youtube on either screen (even both screens) in full screen no problem, but I have no idea what exactly is the going on here.  but it works.. for now

---

### Post by V.V.V. on 2011-01-04
I'm using Chromium 8.0.552.215 and Flash player 10.3.162.29. The fullscreen window name is "exe", so the devilspie settings are:
```
( if 
( begin 
( is ( window_name ) "exe" )
) 
( begin 
( geometry "1920x1080+1280+0" )
( println "match" )
)
)
```

---

### Post by V.V.V. on 2011-01-04
> **F.G. said:**
> hi,
sorry if this seems a silly question. I can't figure out how to configure Xserver.  I gather that the file you need to edit is etc/X11/xorg.conf ?? or something like this. however I don't seem to have that file. am I looking in the right place?
thanks for any help.
The file name is **/**etc/X11/xorg.conf, and you've got to have it if you're using Xserver.

---

### Post by KJ KJ KJ on 2011-01-04
> **V.V.V. said:**
> The file name is **/**etc/X11/xorg.conf, and you've got to have it if you're using Xserver.

I may be wrong, but I think it has become optional recently, which is why some people can't find it. The X server can often just work things out for itself.

I use two monitors, one at 1280x1024, the other at 1680x1050. I used the 'nvidia X server settings' tool to generate my xorg.conf. 

I chose to have_ two distinct X screens_, rather than one desktop over the two monitor areas. This way I can full screen an application in one monitor and it fills just the current screen. 

The downside is that I can't move windows from one monitor to the other, but with separate panels it's not an issue, just launch from the panel on the monitor you want to use.

Here is my xorg.conf as a reference. I'm using Maverick.

```

# nvidia-settings: X configuration file generated by nvidia-settings
# nvidia-settings:  version 260.19.06  (buildd@yellow)  Mon Oct  4 15:59:51 UTC 2010


Section "ServerLayout"
    Identifier     "Layout0"
    Screen      0  "Screen0" 0 0
    Screen      1  "Screen1" RightOf "Screen0"
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
    ModelName      "DELL 1704FPT"
    HorizSync       30.0 - 81.0
    VertRefresh     56.0 - 76.0
    Option         "DPMS"
EndSection

Section "Monitor"

    # HorizSync source: edid, VertRefresh source: edid
    Identifier     "Monitor1"
    VendorName     "Unknown"
    ModelName      "SAMSUNG"
    HorizSync       30.0 - 81.0
    VertRefresh     60.0 - 75.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 6600"
    BusID          "PCI:1:0:0"
    Screen          0
EndSection

Section "Device"
    Identifier     "Device1"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 6600"
    BusID          "PCI:1:0:0"
    Screen          1
EndSection

Section "Screen"

# Removed Option "metamodes" "CRT: nvidia-auto-select +0+0"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "TwinViewXineramaInfoOrder" "CRT-0"
    Option         "TwinView" "0"
    Option         "metamodes" "DFP: nvidia-auto-select +0+0"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection

Section "Screen"

# Removed Option "metamodes" "DFP: nvidia-auto-select +0+0"
    Identifier     "Screen1"
    Device         "Device1"
    Monitor        "Monitor1"
    DefaultDepth    24
    Option         "TwinView" "0"
    Option         "metamodes" "CRT: nvidia-auto-select +0+0"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection



```

---

### Post by F.G. on 2011-01-04
hi,
i've got a fairly standard installation of Meerkat. yet here's the contents of X11:
```
bob@bob-Satellite-Pro-L300:/etc/X11$ ls
app-defaults             fonts    xinit   Xreset.d    Xsession.d
cursors                  rgb.txt  xkb     Xresources  Xsession.options
default-display-manager  X        Xreset  Xsession    Xwrapper.config
```

no xorg.conf, so I guess i'll have to make one.

---

### Post by F.G. on 2011-01-04
oops posted twice.

---

### Post by mahy on 2011-03-16
I'm witnessing the same problem. The only solution I found is to arrange your displays (both physically and logically) so that your intended primary monitor is on the left-hand side. That way you'll get newly opened fullscreen apps on the correct display.

---

### Post by kfu on 2011-04-23
Hi,

I'm using two monitors having the main monitor/display on the right. Somehow all of the operations like  pop-ups, creation of new file/directory, and starting a program considers the other monitor/display (on the left) as if it is the main window.

I cannot change the locations of the monitors or make the one on the left as the main display since it is used for other purposes.

Do you know how can we overcome this problem?

Thanks...

---

### Post by F.G. on 2011-04-23
hello folks,
so, having had a stab at this a while back i'm revisiting the issue.  my main issue is that I can't get stuff in full screen on one monitor whilst using the other one to work on.  playing around a bit I can get stuff to go full screen on either, with the correct ratio (turning of the visual effects does seem to make everything stay in its current screen). although i'm happy enough only being able to use one monitor full screen, if I can use the other to work on, but as soon as I click on anything the screen goes small again (eg watching a flash video in a browser on the left monitor, trying edit stuff on the right).

regarding the xorg.conf file I should point out that it is not necessarily there in /etc/X11, even if you do have the xserver running, though you can auto-generate one by typing
 
```
Xorg -configure
```

though you may have to do this a shell before the xserver starts (eg the root shell via the recovery mode).

I've tried to cobble one together to the two monitors seperately, as KJKJKJ suggested (thanks for the example). though their behaviour is still the same. here's what my xorg.conf file currently looks like:
```
Section "ServerLayout"
    Identifier     "Layout0"
    Screen      0  "Screen0" 0 0
    Screen      1  "Screen1" LeftOf "Screen0"
    InputDevice    "Mouse0" "CorePointer"
    InputDevice    "Keyboard0" "CoreKeyboard"
    #Option         "Xinerama" "0"
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


Section "InputDevice"
	Identifier  "Keyboard0"
	Driver      "kbd"
EndSection

Section "InputDevice"
	Identifier  "Mouse0"
	Driver      "mouse"
	Option	    "Protocol" "auto"
	Option	    "Device" "/dev/input/mice"
	Option	    "ZAxisMapping" "4 5 6 7"
EndSection


Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "Unknown"
EndSection

Section "Monitor"
    Identifier     "Monitor1"
    VendorName     "Unknown"
    ModelName      "Viewsonic"
EndSection

Section "Device"
```
If anyone has any suggestions about how to edit this, so full screen can remain on one, with other stuff on the other id be most grateful.
the output from ~$lshw lists two displays
'display:0' and 'display:1 UNCLAIMED'
I don't know if that is significant, or means anything though thought maybe it wasn't associating with the specifics in the xorg.conf file. anyway, thanks for any more help, and anyone who has already responded.

---

### Post by skriv on 2012-05-13
For Chrome users, this extension works well with Vimeo and Youtube (haven't tried elsewhere): 

Multiple Monitor Full Screen
[https://chrome.google.com/webstore/detail/fdnjdibmddfgbdohgacjakddhncfhpcf](https://chrome.google.com/webstore/detail/fdnjdibmddfgbdohgacjakddhncfhpcf)

---

### Post by snledbetter on 2012-05-15
Thanks for that.  It works on a lot of other sites.

---

