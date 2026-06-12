---
title: "Information on Ubuntu and Monitors"
date: 2009-11-02
forum: General Help
---

### Post by Gosport on 2009-11-02
Why does Ubuntu not display or give me the proper options for my particular monitor?  The monitor suggests 1440x900 but Ubuntu does not give me this option.  Depending on which option I chose people (or circles or whatever) are either too fat or too tall.  The monitor controls are unable to compensate for this distortion.  
I have tried the proprietary driver suggested by Ubuntu but that made my monitor unusable. 

Is there a list of monitors that will work better with Ubuntu or is this a different kind of issue?

---

### Post by t0p on 2009-11-02
There are a couple of utilities that I've found most useful when configuring monitors: **xrandr** comes installed by default, but it's a command-line program so not attractive to everyone; or you can install **grandr** which does the same job but has a GUI.

---

### Post by Giblet5 on 2009-11-02
X (the linux gui subsystem), when it first starts, attempts to ask your monitor what its capabilities are.

If you have a monitor that's less than 10 years old, it has the ability to respond to that request.......if you have the right cable.

If the monitor responds with garbage info, or if you have the wrong kind of cable (VGA HD15 cables are notorious), then X can't figure out what you have and it'll make a guess at something safe.

The way to correct this is to get the monitor's technical specifications from the vendor and tell X how to use those specs via /etc/X11/xorg.conf.

You'll need the "Horizontal Sync Frequency Range" which will be specified in KHz, and you need the "Vertical Refresh Frequency Range" specified in Hz.

Then you can create an xorg.conf file by opening a terminal window and entering ```
sudo gedit /etc/X11/xorg.conf
```

Get the specs for your monitor and then replace the two floating point numbers from the following example with your monitor's values.

This is an example for an HP F2304 LCD monitor: ```
Section "Monitor"
    Identifier     "HP f2304"
    HorizSync       30.0 - 94.0
    VertRefresh     48.0 - 85.0
EndSection

Section "Device"
    Identifier     "GPU"
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "GPU"
    Monitor        "HP f2304"
    DefaultDepth    24
EndSection
```

Save it and run this in a terminal window: ```
sudo /etc/init.d/gdm restart
```

It should now provide all of the native resolutions that your monitor supports, but certain graphics (like the boot splash) will still be the wrong aspect ratio because that's not under X's control.


PS: xrandr is useful only when X can determine the monitor's capabilities accurately. That is not always the case, and this is one of them. The xrandr/grandr tools will tell you what System -> Preferences -> Display already told you, and we know that is wrong.

---

### Post by jbrown96 on 2009-11-02
It's probably a graphics driver issue. ATI and Nvidia both release clients that can adjust resolution better. 

You can check what you have with ```
lspci | grep VGA
``` 
If you have ATI or Nvidia, go to System-->Admin-->hardware drivers and make sure you install the drivers, then reboot. The resolution should be much better, but if it's not try the following.


For Nvidia:
Alt+F2 then nvidia-settings. On the left choose "X server display configuration." Try changing the resolution, then click apply. If that works well, then you need to make it permanent. Exit (don't save X configuration file). Re-open with administrator privileges. Alt+F2 ```
gksu nvidia-settings
``` enter you password, then set your resolution again. Choose "save to X configuration file" then click save. Your resolution should set automatically now.


For ATI:
there should be a utility in Applications called Catalyst Control Center. Open it and there should be a section to set your resolution.

---

### Post by lavinog on 2009-11-02
> **Giblet5 said:**
> 
Get the specs for your monitor and then replace the two floating point numbers from the following example with your monitor's values.

This is an example for an HP F2304 LCD monitor: ```
Section "Monitor"
    Identifier     "HP f2304"
    HorizSync       30.0 - 94.0
    VertRefresh     48.0 - 85.0
EndSection

Section "Device"
    Identifier     "GPU"
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "GPU"
    Monitor        "HP f2304"
    DefaultDepth    24
EndSection
```


+1 for editing the xorg file.  The xrandr method isn't user friendly at all.
I find that it is easier to just add a modes line in the screen section with all of the modes you would like to use.  (sync values are not always available for older monitors)

I have  a couple of monitors that ubuntu tries to use resolutions greater than what the monitor can handle...one of them will actually display the higher resolution for some undocumented reason.

---

### Post by Giblet5 on 2009-11-02
> **lavinog said:**
> I have  a couple of monitors that ubuntu tries to use resolutions greater than what the monitor can handle...one of them will actually display the higher resolution for some undocumented reason.

Yep. That example F2304 is one of those.

Supposedly, it can't do 1920x1200 @ 75Hz, but it does and it's beautiful at that setting.

---

### Post by Gosport on 2009-11-15
> **Giblet5 said:**
> 
The way to correct this is to get the monitor's technical specifications from the vendor and tell X how to use those specs via /etc/X11/xorg.conf.

You'll need the "Horizontal Sync Frequency Range" which will be specified in KHz, and you need the "Vertical Refresh Frequency Range" specified in Hz.

Then you can create an xorg.conf file by opening a terminal window and entering ```
sudo gedit /etc/X11/xorg.conf
```Get the specs for your monitor and then replace the two floating point numbers from the following example with your monitor's values.

This is an example for an HP F2304 LCD monitor: ```
Section "Monitor"
    Identifier     "HP f2304"
    HorizSync       30.0 - 94.0
    VertRefresh     48.0 - 85.0
EndSection

Section "Device"
    Identifier     "GPU"
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "GPU"
    Monitor        "HP f2304"
    DefaultDepth    24
EndSection
```Save it and run this in a terminal window: ```
sudo /etc/init.d/gdm restart
```It should now provide all of the native resolutions that your monitor supports, but certain graphics (like the boot splash) will still be the wrong aspect ratio because that's not under X's control.


**I tried this and my monitor gave me the "Out of Range" message.  **
[B]
This is what my xorg.conf file looks like:[/B]

                                 # xorg.conf (X.Org X Window System server configuration file)  
 #  
 # This file was generated by dexconf, the Debian X Configuration tool, using  
 # values from the debconf database.  
 #  
 # Edit this file with caution, and see the xorg.conf manual page.  
 # (Type "man xorg.conf" at the shell prompt.)  
 #  
 # This file is automatically updated on xserver-xorg package upgrades *only*  
 # if it has not been modified since the last upgrade of the xserver-xorg  
 # package.  
 #  
 # Note that some configuration settings that could be done previously  
 # in this file, now are automatically configured by the server and settings  
 # here are ignored.  
 #  
 # If you have edited this file but would like it to be automatically updated  
 # again, run the following command:  
 #   sudo dpkg-reconfigure -phigh xserver-xorg  
 

 Section "Device"  
     Identifier    "Configured Video Device"  
 EndSection  
 

 Section "Monitor"  
     Identifier    "Configured Monitor" 
 EndSection  
 

 Section "Screen"  
     Identifier    "Default Screen"  
     Monitor        "Configured Monitor" 
     Device        "Configured Video Device" 
 EndSection
 
[B]
And these are the specifications for my monitor:[/B]

                                 ModelName "ViewSonic VA1916wSERIES"
HorizSync 24.0 - 82.0
VertRefresh 50.0 - 75.0


**Any ideas??**

---

### Post by Romanrp on 2009-11-15
Same problem here.
The way I solved it was to run 1366x786 on a laptop which resulotion is meant to be 1024x786

---

### Post by Gosport on 2009-11-16
> **Romanrp said:**
> Same problem here.
The way I solved it was to run 1366x786 on a laptop which resulotion is meant to be 1024x786

Yes, but the options I am given distort the picture slightly.

---

### Post by Gosport on 2009-11-17
> **jbrown96 said:**
> It's probably a graphics driver issue. ATI and Nvidia both release clients that can adjust resolution better. 

You can check what you have with ```
lspci | grep VGA
```If you have ATI or Nvidia, go to System-->Admin-->hardware drivers and make sure you install the drivers, then reboot. The resolution should be much better, but if it's not try the following.


For Nvidia:
Alt+F2 then nvidia-settings. On the left choose "X server display configuration." Try changing the resolution, then click apply. If that works well, then you need to make it permanent. Exit (don't save X configuration file). Re-open with administrator privileges. Alt+F2 ```
gksu nvidia-settings
``` enter you password, then set your resolution again. Choose "save to X configuration file" then click save. Your resolution should set automatically now.


For ATI:
there should be a utility in Applications called Catalyst Control Center. Open it and there should be a section to set your resolution.

**I downloaded the proprietary ATI graphics driver and again, my monitor gave me the same "Out of Range" message.  Is there an issue with ViewSonic monitors or just mine?**

---

### Post by jbrown96 on 2009-11-17
What type of graphics card do you have? Post the output of ```
lspci | grep VGA
```

---

### Post by Gosport on 2009-11-19
> **jbrown96 said:**
> What type of graphics card do you have? Post the output of ```
lspci | grep VGA
```

[B]01:05.0 VGA compatible controller: ATI Technologies Inc Device 9710

Have any ideas??
[/B]

---

### Post by Gosport on 2009-11-20
> **Gosport said:**
> [B]01:05.0 VGA compatible controller: ATI Technologies Inc Device 9710
[/B]

Is this a common graphics card?

---

### Post by Gosport on 2009-11-22
Anybody??

---

