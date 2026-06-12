---
title: "Couldn't find matching GLX visual"
date: 2010-12-17
forum: General Help
---

### Post by jtkiv on 2010-12-17
using nvidia_173 driver from repository with nvidia geforce fx5500

sping returns this:

Could not set video mode:
Couldn't find matching GLX visual

would installing nvidia-glx-173 package be the solution?


---

just realized i had the nvidia_173 driver activiated, but not in use.

ran "sudo nvidia-xconfig"

boots in tty1, so i navigated to the X11 directory and deleted xorg.conf, boots to gnome now :)

---

how do i keep it from going to tty1?  

p.s. i know there are threads on this here and there, but most leave you with the default driver, and i want to keep nvidia_173

---

### Post by TeoBigusGeekus on 2010-12-17
Have you tried running
```
gksu nvidia-settings
```
?

---

### Post by jtkiv on 2010-12-17
if i run that when i can see, i get 
> 
You do not appear to be using the NVIDIA X driver. Please edit your X configuration file (just run `nvidia-xconfig` as root), and restart the X server. 

if i enable the nvidia driver, im stuck at tty1.  

what setting would i change anyhow?

---

### Post by jtkiv on 2010-12-20
any other ideas?

---

### Post by Krytarik on 2010-12-21
What version of Ubuntu are you running?

How did you install the driver? Via "System -> Administration -> Hardware Drivers/Additional Drivers"?

Try re-installing the driver via Synaptic.

If starting the desktop after that fails again, please post the contents of the xorg.conf and /var/log/Xorg.0.log".

---

### Post by jtkiv on 2010-12-21
running 10.10

i installed from synaptic originally.  Additional Drivers never found anything.

from tty1, i deleted xorg.conf so as to disable the nvidia driver.  currently operating without it.  i also have deleted the nouveau drivers which were very buggy/slow.  so i suppose im currently running more or less in failsafe mode?  that would mean im using "vesa" driver?

im linking to /var/log/Xorg.0.log (too big to att) i have others like, Xorg.3.log, do you want those too?

[https://sumcqa.blu.livefilestore.com/y1p2t43g5YPxnHeU0TXwc9yMcR7CcbFhlvc3Pap27p0ZvEeOAckxfpzOCo5q_DQZAiPNmBjDI3BQyPQwwqTLpdCrJShaxLESCZB/Xorg.0.log.txt?psid=1](https://sumcqa.blu.livefilestore.com/y1p2t43g5YPxnHeU0TXwc9yMcR7CcbFhlvc3Pap27p0ZvEeOAckxfpzOCo5q_DQZAiPNmBjDI3BQyPQwwqTLpdCrJShaxLESCZB/Xorg.0.log.txt?psid=1)

---

### Post by Krytarik on 2010-12-21
> **jtkiv said:**
> running 10.10

i installed from synaptic originally.  Additional Drivers never found anything.

from tty1, i deleted xorg.conf so as to disable the nvidia driver.  currently operating without it.  i also have deleted the nouveau drivers which were very buggy/slow.  so i suppose im currently running more or less in failsafe mode?  that would mean im using "vesa" driver?

im linking to /var/log/Xorg.0.log (too big to att) i have others like, Xorg.3.log, do you want those too?

[https://sumcqa.blu.livefilestore.com/y1p2t43g5YPxnHeU0TXwc9yMcR7CcbFhlvc3Pap27p0ZvEeOAckxfpzOCo5q_DQZAiPNmBjDI3BQyPQwwqTLpdCrJShaxLESCZB/Xorg.0.log.txt?psid=1](https://sumcqa.blu.livefilestore.com/y1p2t43g5YPxnHeU0TXwc9yMcR7CcbFhlvc3Pap27p0ZvEeOAckxfpzOCo5q_DQZAiPNmBjDI3BQyPQwwqTLpdCrJShaxLESCZB/Xorg.0.log.txt?psid=1)
Additional Drivers should be able do find the proper driver for you, at least it did for me in 10.04.
[https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia](https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia)

So if it really doesn't work you should try to install additional packages that might be missing, unfortunately I can't tell you right now which packages completes the set because I'm currently not at my machine (until after new years edge).

If that doesn't work try the latest version of the offered drivers or try those offered by the the Ubuntu-X-Swat:
[https://launchpad.net/~ubuntu-x-swat/+archive/x-updates]("https://launchpad.net/%7Eubuntu-x-swat/+archive/x-updates")

You may also try to install the drivers offered via the Nvidia-website, remove any previously installed driver packages before. Imo that would be the least choice because each time the kernel is updated the boot fails to the console and you have to re-compile/install the driver.

PS: The link you provided doesn't deliver anything, altough I even logged in with my LiveID.
The driver used by default should be "nv", "vesa" is also possible, check the Xorg.0.log for that. If you want to attach a bigger text file you just can compress it and attach the created archive.

---

### Post by jtkiv on 2010-12-22
from [https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers/+bug/619008](https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers/+bug/619008)

                 > "I was experiencing this same problem and found a way to fix it.
 I just received a new Lenovo T410 laptop with discrete NVidia  graphics accelerator today.  Installed Ubuntu 10.10 and everything  worked fine.  When I installed the NVidia driver and rebooted, the  system would hang on "checking battery state" message and not progress  any further.
 The cause and solution:  I checked the bios of the T410 and there is a  graphics setting that switches between "integrated" (no acceleration)  "discrete" (activates NVidia accelerator at all times) and "NVidia  Optimus".  The "Optimus" setting was on by default, with this  description:
 "If enabled, System BIOS automatically switches Graphics Device  setting to NVIDIA Optimus mode if the OS supports the feature, and to  Discrete Graphics if the OS does not support it."
 I changed the setting to "discrete" and Ubuntu booted with no  problems.  I assume that Linux does not currently support NVIDIA Optimus  :)"

        

could this be the solution?  boot is hanging at "checking battery state" (never says ok though, but is a desktop), so surely that is caused by the nvidia drivers since simply deleting "xorg.conf" will allow it to boot fully.  i have no idea how/where to edit this optimus/discrete thing though.  im not sure what 10.10 has to do with this, doesnt make a whole lot of sense.

---

### Post by Krytarik on 2010-12-23
Do you also have an onboard graphics chip then?

Apparently the "Checking battery state"-output is always the last one does see when falling back to console.

Remove any parts of drivers you have tried get working and try again with "Additional Drivers" or Ubuntu-X-Team drivers.

If both doesn't work, please attach the failing xorg.conf and Xorg.0.log.

---

### Post by jtkiv on 2011-01-01
sorry for late reply...

removed drivers tried x-team, tried nvidia-173 from synaptic, no better. 

i did find a backup xorg.conf from 10.04, and used it with better results than the "nvidia-xconfig" generated xorg.conf.  but, by better i only mean that x started.  menus wouldn't pop-up, lag was other-worldly, gnome panels would sometimes fail to appear... basically useless.

attached a .zip with the 10.04 conf, the failsafe which i assume it uses when there is no xorg.conf, the conf generated by nvidia-xconfig, and xorg.0.log (added other logs, didnt know if those were needed).

---

### Post by Krytarik on 2011-01-01
Your xorg.conf.nvidia looks ok. However there may be a problem with detection the supported modes of your monitor or the location of the kernel module.

Check if the HorizSync and VertRefresh values are correctly specified:
```
sudo apt-get hwinfo
sudo hwinfo --monitor
```

Try adding the correct modeline to the xorg.conf:
[https://wiki.ubuntu.com/X/Config/Resolution#Adding%20undetected%20resolutions](https://wiki.ubuntu.com/X/Config/Resolution#Adding%20undetected%20resolutions)

Check the location of the installed kernel module via Synaptic and try passing it through the xorg.conf, like this:
```
Section "Files"
    ModulePath  "/usr/lib/nvidia/xorg/modules"
    ModulePath  "/usr/lib/xorg/modules"
EndSection
```

Try setting the driver to "nv" instead of "nvidia" in the xorg.conf.

Is the display working correctly if running a LiveCD?

---

### Post by jtkiv on 2011-01-02
the output of hwinfo
```
34: None 00.0: 10000 Monitor                                    
  [Created at monitor.95]
  Unique ID: rdCR.WkJwHqHhV58
  Hardware Class: monitor
  Model: "Gateway Monitor"
  Vendor: GWY "Gateway"
  Device: eisa 0x06d6 
  Resolution: 720x400@70Hz
  Resolution: 640x480@60Hz
  Resolution: 640x480@75Hz
  Resolution: 800x600@60Hz
  Resolution: 800x600@75Hz
  Resolution: 832x624@75Hz
  Resolution: 1024x768@60Hz
  Resolution: 1024x768@75Hz
  Resolution: 1280x1024@75Hz
  Resolution: 1280x1024@60Hz
  Size: 338x270 mm
  Detailed Timings #0:
     Resolution: 1280x1024
     Horizontal: 1280 1328 1440 1688 (+48 +160 +408) +hsync
       Vertical: 1024 1025 1028 1066 (+1 +4 +42) +vsync
    Frequencies: 108.00 MHz, 63.98 kHz, 60.02 Hz
  Driver Info #0:
    Max. Resolution: 1280x1024
    Vert. Sync Range: 56-75 Hz
    Hor. Sync Range: 30-83 kHz
    Bandwidth: 108 MHz
  Config Status: cfg=new, avail=yes, need=no, active=unknown

```

so i changed
```
Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "Unknown"
    HorizSync       30.0 - 110.0
    VertRefresh     50.0 - 150.0
    Option         "DPMS"
EndSection
```

to
```
Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "Unknown"
    HorizSync       30.0 - 83.0
    VertRefresh     56.0 - 75.0
    Option         "DPMS"
EndSection
```

X actually booted sort of.  good news is that it didnt take me to tty1,  bad news is the screen is black (cept cursor) until i click on a gnome  panel, pop up a window, etc.  then, wherever the window was i'm able to  see.  sounds like a refresh problem... 

after that, changed "nvidia" to "nv", but when i run NVIDIA X Server  Settings, it says nvidia drivers are not being used.  i take that to  mean "nv" doesn't work.

---

### Post by Krytarik on 2011-01-03
"nv" is the default open source driver for Nvidia cards, I just wanted to check if it works at least with those.

I searched a little at the specific blank screen behaviour.

Try setting the "NvAGP"-option in xorg.conf:
[http://ubuntuforums.org/showthread.php?t=1349553](http://ubuntuforums.org/showthread.php?t=1349553)

It may also be a Compiz issue, so try disabling it by setting:
```
Section "Extensions"
    Option "Composite" "Enable"
EndSection
```in xorg.conf.

---

### Post by Krytarik on 2011-01-03
Check if all needed packages are installed.
```
dpkg -l | grep nvidia
```
I'm using the version 96 (old video card), my packages are:
```

ii  nvidia-173-modaliases                 173.14.22-0ubuntu11                             Modaliases for the NVIDIA binary X.Org drive
ii  nvidia-96                             96.43.17-0ubuntu1                               NVIDIA binary Xorg driver, kernel module and
ii  nvidia-96-modaliases                  96.43.17-0ubuntu1                               Modaliases for the NVIDIA binary X.Org drive
ii  nvidia-common                         0.2.23                                          Find obsolete NVIDIA drivers
ii  nvidia-current-modaliases             195.36.24-0ubuntu1~10.04                        Modaliases for the NVIDIA binary X.Org drive
ii  nvidia-settings                       195.36.08-0ubuntu2                              Tool of configuring the NVIDIA graphics driv

```

---

### Post by jtkiv on 2011-01-03
no luck with NvAGP or Compiz settings...

```
ii  nvidia-173                           173.14.28-0ubuntu1                                NVIDIA binary Xorg driver, kernel module and VDPAU library
rc  nvidia-96                            96.43.18-0ubuntu1                                 NVIDIA binary Xorg driver, kernel module and VDPAU library
rc  nvidia-common                        0.2.24                                            Find obsolete NVIDIA drivers
ii  nvidia-glx-173                       173.14.28-0ubuntu1                                Transitional package for nvidia-glx-173
ii  nvidia-settings                      260.19.29-0ubuntu1~xup                            Tool of configuring the NVIDIA graphics driver

```

based off your package list i should get "nvidia-common" "nvidia-current-modaliases" "nvidia-173-modaliases"?

---

### Post by jtkiv on 2011-01-03
installed those packages, no improvement.  been a while now, perhaps its time to clean install 10.04 and stick with that.  of course, hoping that the drivers work on that again...

---

### Post by Krytarik on 2011-01-03
Try purging the package "nvidia-96".

EDIT: And re-install "nvidia-glx-173" after that.

Try this way to disable compiz:
[http://ptspts.blogspot.com/2010/06/how-to-disable-compiz-fusion-and-enable.html](http://ptspts.blogspot.com/2010/06/how-to-disable-compiz-fusion-and-enable.html)

Also try to create a new user and log in with those.

---

### Post by jtkiv on 2011-01-04
purged 96 and ran those two commands to disable compiz.  result is a functional nvidia driver!

spring goes black, so that tells me something is still not quite right, but otherwise system seems to be working fine.  thanks for the help, ill post back if i figure out whats stopping spring.

---

### Post by Krytarik on 2011-01-04
Fine improvement so far. Then please post your current xorg.conf.

And try the new user thing please, enabling Compiz again before.

EDIT: Oh, you don't have to enable it manually, because it's a new user, and Compiz is the default. ;-)

---

### Post by Krytarik on 2011-01-04
When logged in with the Nvidia driver working and Compiz disabled, check if hardware acceleration is enabled:
```
sudo apt-get install mesa-utils
glxinfo |grep rendering
```
If this returns "direct rendering: Yes", acceleration is working.

You may also check
```
glxgears
```
If hw-accel isn't working, please attach /var/log/Xorg.0.log.

---

### Post by jtkiv on 2011-01-04
"direct rendering: Yes" was returned, however "glxgears" froze my comp after about 2 secs of spinning.

if you open the zip i posted, "xorg.conf.nvidia" returns a blacked out spring, "xorg.conf.10.04" returns a frozen (but visible!) spring.

my new user account doesn't work.  same buggy graphics as before, so that leads me to believe compiz is at fault.

---

### Post by jtkiv on 2011-01-04
rebooted after a freeze, decided to run glxgears again, got this:

```
6474 frames in 14.3 seconds = 453.338 FPS
12216 frames in 5.0 seconds = 2443.004 FPS
12318 frames in 5.0 seconds = 2463.429 FPS
11135 frames in 13.0 seconds = 856.606 FPS
12273 frames in 5.0 seconds = 2454.460 FPS
3753 frames in 21.6 seconds = 173.372 FPS
1 frames in 11.4 seconds =  0.088 FPS
1614 frames in 9.0 seconds = 179.723 FPS
12225 frames in 5.0 seconds = 2444.826 FPS
68 frames in 11.0 seconds =  6.175 FPS
2006 frames in 16.8 seconds = 119.094 FPS
8826 frames in 13.2 seconds = 670.256 FPS
1811 frames in 9.0 seconds = 200.957 FPS
12251 frames in 5.0 seconds = 2450.101 FPS
8031 frames in 23.4 seconds = 342.565 FPS
1 frames in 15.6 seconds =  0.064 FPS
9958 frames in 20.0 seconds = 498.055 FPS
131 frames in 13.0 seconds = 10.078 FPS
4618 frames in 23.8 seconds = 193.971 FPS
1 frames in 18.2 seconds =  0.055 FPS
12222 frames in 5.0 seconds = 2444.392 FPS
5718 frames in 15.0 seconds = 381.385 FPS
6974 frames in 23.0 seconds = 303.186 FPS
1 frames in 20.0 seconds =  0.050 FPS
12201 frames in 5.0 seconds = 2440.082 FPS
909 frames in 15.0 seconds = 60.636 FPS

```every period less than the ~2400FPS was a pause in the gears.  so sporadic performance at best... 

attached xorg.0.log

sounds like hardware to me though.  perhaps a partial failure occurred coincidentally at the same time of an upgrade?  suppose time will tell on that one.

---

### Post by Krytarik on 2011-01-04
1.) According to the Xorg.0.log the drivers gets loaded without error.

2.) The only real difference between the two xorg.conf's is the "Monitor"-section.
You did update the specs in your local version of the xorg.conf.nvidia, right?
Try removing the "DPMS"-option.

3.) If it stays like this, there is either an error in the driver or your video card.
You may try the Ubuntu-X-Swat drivers then:
[https://launchpad.net/~ubuntu-x-swat/+archive/x-updates]("https://launchpad.net/%7Eubuntu-x-swat/+archive/x-updates")
```
sudo add-apt-repository ppa:ubuntu-x-swat/x-updates
sudo apt-get update
sudo apt-get upgrade
```

---

