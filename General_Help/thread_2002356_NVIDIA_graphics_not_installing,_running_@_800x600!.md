---
title: "NVIDIA graphics not installing, running @ 800x600!"
date: 2012-06-12
forum: General Help
---

### Post by Rebelli0us on 2012-06-12
This is a fresh install of 10.10 on a new machine with NVIDIA GTX 550 Ti. I followed official installation instructions here:

[http://www.ubuntuupdates.org/package/ubuntu-x-swat/maverick/main/base/nvidia-current]("http://www.ubuntuupdates.org/package/ubuntu-x-swat/maverick/main/base/nvidia-current")

After installation “Additional Drivers” shows NVIDIA driver installed and active, but system still runs @ 800x600. When I select “Monitors” I get this:
[IMG]http://ubuntuforums.org/attachment.php?attachmentid=219564&stc=1&d=1339508945[/IMG]


and then this:
[IMG]http://ubuntuforums.org/attachment.php?attachmentid=219565&stc=1&d=1339508945[/IMG]


Then when I reboot, I only have a command prompt (tty?). I installed several times, and in all cases Ubuntu self-destructed in similar fashion. I even downloaded driver from NVIDIA and installed from terminal, “sudo service gdm stop”, “sudo sh ../NVIDIA”... a disaster, never do this!

So, how do I get more than 800x600?

---

### Post by LinGNUbie on 2012-06-12
Nvidia's drivers always try to run in a "meta" mode (predetermined) so usually you have to specify the correct monitor settings with an xorg.conf file explicitly stating the HorizSync and VertRefresh and modelines to be used by the monitor.

---

### Post by Kundan Negi on 2012-06-12
Rebeli0us could u please tell me your system configuration.I encountered the same problem as my laptop was draining lot of battery and was getting heated.It was due working of both graphics cards (Intel and Nvidia). If you encounter the same problem,i recommend u to visit 
[http://www.omgubuntu.co.uk/2011/06/bumblebee-gets-a-ppa-brings-nvidia-optimus-graphics-switching-to-ubuntu](http://www.omgubuntu.co.uk/2011/06/bumblebee-gets-a-ppa-brings-nvidia-optimus-graphics-switching-to-ubuntu)

This might help u! And ya, don't install nvidia driver. I too installed and made my system stuck in 800*600.

---

### Post by Rebelli0us on 2012-06-12
> **LinGNUbie said:**
> Nvidia's drivers always try to run in a "meta" mode (predetermined) so usually you have to specify the correct monitor settings with an xorg.conf file explicitly stating the HorizSync and VertRefresh and modelines to be used by the monitor.

Thank you. How do I change the settings?

All I did so far is:

```
sudo apt-add-repository ppa:ubuntu-x-swat/x-updates
sudo apt-get update
sudo apt-get install nvidia-current nvidia-settings
```

---

### Post by LinGNUbie on 2012-06-12
You will need to create the /etc/X11/xorg.conf file (or re-create one if it exists) with the required settings for your particular monitor. I have a generic one that may help with creating one [here]("http://ubuntuforums.org/showthread.php?t=1923165"), just be sure to research your monitors documentation (or Google) for the correct HorizSync and VertRefresh rates for your monitor. Modelines can be generated [here]("http://www.arachnoid.com/modelines/index.html"). Standard in the US is 60Hz Refresh rate.

---

### Post by Rebelli0us on 2012-06-13
> **LinGNUbie said:**
> You will need to create the /etc/X11/xorg.conf file (or re-create one if it exists) with the required settings for your particular monitor. I have a generic one that may help with creating one [here]("http://ubuntuforums.org/showthread.php?t=1923165"), just be sure to research your monitors documentation (or Google) for the correct HorizSync and VertRefresh rates for your monitor. Modelines can be generated [here]("http://www.arachnoid.com/modelines/index.html"). Standard in the US is 60Hz Refresh rate.

What are the required settings? I don't really know. It seems that Linux does **not** support newer NVIDIA video hardware but works fine with older ones.

I'm thinking to temporarily install an older NVIDIA 8600GT which should work, and once the system is configured and the proprietary driver installed then switch to the NVIDIA GTX 550 Ti  :popcorn:

---

### Post by LinGNUbie on 2012-06-13
The "required settings" would be the correct Horizontal Sync and Vertical Refresh Range for your particular monitor. Googling or searching the forums here will help with the creation of the xorg.conf file.

Unfortunately it would seem that this process is needed for all Nvidia cards, as I am running an older card in a few boxes and had to do these steps to get them working correctly. I believe the issue lies within the drivers.

---

### Post by Rebelli0us on 2012-06-13
Thank you.

It's not fetching the drivers from ubuntu-x-swat:

```
**sudo apt-get install nvidia-current nvidia-settings**
Reading package lists... Done
Building dependency tree       
Reading state information... Done
nvidia-settings is already the newest version.
nvidia-current is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
```

even though I have 260.19.06 and it should be fetching 295.53 according to [ubuntuupdates.org]("http://www.ubuntuupdates.org/pm/nvidia-current")
```
**apt-cache policy nvidia-current**
nvidia-current:
  Installed: 260.19.06-0ubuntu1
  Candidate: 260.19.06-0ubuntu1
  Version table:
 *** 260.19.06-0ubuntu1 0
        500 http://us.archive.ubuntu.com/ubuntu/ maverick/restricted amd64 Packages
        100 /var/lib/dpkg/status
```


Any ideas? Otherwise it's back to the 1980s with 800x600:confused:

---

### Post by Rebelli0us on 2012-06-13
> **Bexarterfef said:**
> Just have to say - Great Post!

What did you like, the bunny or the pretty pictures?

---

### Post by LinGNUbie on 2012-06-13
First, what is the model of the monitor? Second, What does your current xorg.conf file have? 

I have them running without the swat ppa just the ones found in ubuntu's repos (no nouveau drivers).

---

### Post by Rebelli0us on 2012-06-15
> **LinGNUbie said:**
> First, what is the model of the monitor? Second, What does your current xorg.conf file have? 

I have them running without the swat ppa just the ones found in ubuntu's repos (no nouveau drivers).

Thank you, x-swat is listing nvidia driver for 10.10 but none is actually there, repositories don't support GTX 550 Ti, so I had no choice but to download & install from NVIDIA. Has to be done in terminal it seems, there are some script errors too, but video now works. Do you know what this means (photo attached)? It pops up during installation.

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=219751&stc=1&d=1339784912[/IMG]



And so as not to evade your question, monitor is NEC PA231W, here is my config:


```
# nvidia-xconfig: X configuration file generated by nvidia-xconfig
# nvidia-xconfig:  version 295.53  (buildmeister@swio-display-x86-rhel47-07.nvidia.com)  Sat May 12 00:34:20 PDT 2012

Section "ServerLayout"
    Identifier     "Layout0"
    Screen      0  "Screen0"
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
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
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "NEC PA231W"
    HorizSync       31.0 - 83.0
    VertRefresh     50.0 - 85.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    Option         "NoLogo" "1"
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

```

---

### Post by LinGNUbie on 2012-06-16
It is an autoinstaller for the OpenGL libraries, part of the Nvidia website driver, and should not hurt to run if it is asking at boot time as it will complete the driver install.

I would look into creating some modelines for your monitor section (if you aren't having the choice of capable resolutions).

---

### Post by Rebelli0us on 2012-06-19
> **LinGNUbie said:**
> It is an autoinstaller for the OpenGL libraries, part of the Nvidia website driver, and should not hurt to run if it is asking at boot time as it will complete the driver install.

I would look into creating some modelines for your monitor section (if you aren't having the choice of capable resolutions).

Thank you.

Several times the machine booted up and the **desktop was wider than the screen**, so I couldn't see the far left or the far right. 

Resolution in NVIDIA X-server display configuration was set to "Auto". Setting it to actual (1920x1080) fixes the problem. I also "saved" the new config file:


```
# nvidia-settings: X configuration file generated by nvidia-settings
# nvidia-settings:  version 295.53  (buildmeister@swio-display-x86-rhel47-07.nvidia.com)  Sat May 12 00:33:54 PDT 2012


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
    ModelName      "NEC PA231W"
    HorizSync       31.0 - 83.0
    VertRefresh     50.0 - 85.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce GTX 550 Ti"
    Option         "NoLogo" "1"
EndSection

Section "Screen"

# Removed Option "metamodes" "nvidia-auto-select +0+0; 1920x1080 +0+0"
# Removed Option "metamodes" "1920x1080 +0+0; nvidia-auto-select +0+0"
# Removed Option "metamodes" "nvidia-auto-select +0+0; 1920x1080 +0+0"
# Removed Option "metamodes" "1920x1080 +0+0; nvidia-auto-select +0+0"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "TwinView" "0"
    Option         "TwinViewXineramaInfoOrder" "CRT-1"
    Option         "metamodes" "nvidia-auto-select +0+0; 1920x1080 +0+0"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection


```


Whaddya think?  My widows VMs still have **no Direct 3d** so I can't run pinball full screen.:popcorn:

---

### Post by LinGNUbie on 2012-06-19
I do not use any VM's so I am not sure what could be going on there.

I would still create some modelines for resolutions, and add them to the Monitor section, so that they may be picked up by the driver. Once you have those in place ONLY use the desktop's included monitor app for changing resolutions, as the Nvidia app will overwrite certain settings within the xorg.conf file sometimes giving poor results.

---

### Post by Dlambert on 2012-06-19
I had to install my nvidia drivers twice manually in order for them to work, no clue why. Basically install, reboot, install again, working. It gets tedious after every new kernel.

---

