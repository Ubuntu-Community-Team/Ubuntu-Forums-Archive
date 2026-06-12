---
title: "Unity not working"
date: 2011-06-10
forum: General Help
---

### Post by jgeralnik on 2011-06-10
I installed 11.04 a couple of weeks ago and everything worked fine. Yesterday I rebooted and got an error that my graphics card was not supported with unity (even though it was working fine before hand). I got a blank desktop with my desktop icons but no gnome panels or unity of any kind. I tried running unity from the terminal (which I was able to open using the keyboard shortcut) and got an error that gnome-panel was not found. I installed gnome panel and now when I login I get the classic gnome interface (even though the default "ubuntu" is selected on the logon screen).

How do I fix unity?

---

### Post by JoeCregeen on 2011-06-10
I have a very similar problem. I have also been running 11.04 since launch, and today as I log in I get a "Hardware unable to support Unity" message, despite it running perfectly up until now, so now running classic. If anyone could help I would very much appreciate it!

---

### Post by DinoT1985 on 2011-06-10
do you see Unity if you log out and login again using Ubuntu session?

---

### Post by Frogs Hair on 2011-06-10
Did you receive a kernel update ? If so you may want to attempt reinstalling the proprietary graphics driver and then try to boot Unity. The hardware message has been driver related for many people.

---

### Post by JoeCregeen on 2011-06-10
> **Frogs Hair said:**
> Did you receive a kernel update ? If so you may want to attempt reinstalling the proprietary graphics driver and then try to boot Unity. The hardware message has been driver related for many people.

That sounds like it could be it, how would I go about doing that? Sorry, bit of a beginner here!

---

### Post by DinoT1985 on 2011-06-10
> **JoeCregeen said:**
> That sounds like it could be it, how would I go about doing that? Sorry, bit of a beginner here!


try this

[http://ubuntuforums.org/showpost.php?p=10924090&postcount=3](http://ubuntuforums.org/showpost.php?p=10924090&postcount=3)

---

### Post by sikander3786 on 2011-06-10
First of all, the simplest thing to try would be to remove and re-install your graphics drivers. If that doesn't work either, take a look here. Specially, make sure that all the packages are installed and none of them got removed accidentally or due to some upgrades etc.

[http://ubuntu4beginners.blogspot.com/2011/04/missing-top-and-side-panels-in-unity.html](http://ubuntu4beginners.blogspot.com/2011/04/missing-top-and-side-panels-in-unity.html)

And if that doesn't work either, you can try force starting Unity.

[http://ubuntu4beginners.blogspot.com/2011/05/force-unity-compiz-to-run-natty-narwhal.html](http://ubuntu4beginners.blogspot.com/2011/05/force-unity-compiz-to-run-natty-narwhal.html)

---

### Post by JoeCregeen on 2011-06-10
Tried everything here, and nothing has worked, but I think I've identified the problem. I noticed "NVIDIA X Server Settings" new under System- Administration, and when i try to open it i get a message: "You do not appear to be using the NVIDIA X driver.  Please edit your X configuration file (just run `nvidia-xconfig` as root), and restart the X server.". When I do this I get the following: 
WARNING: Unable to locate/open X configuration file.


ERROR: Unable to write to directory '/etc/X11'.

Could this be something to do with it? In which case what can I do to fix it?

Also, thanks for all your help so far.

---

### Post by JoeCregeen on 2011-06-10
Also when I try to run unity --reset I get this:

joe@joe-laptop:~$ unity --reset
WARNING: Unity currently default profile, so switching to metacity while resetting the values
unity-panel-service: no process found
Backend     : gconf
Integration : true
Profile     : unity
Adding plugins
Initializing core options...done
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 1
Window created on XQueryTree, map state isViewable? 1
Window created on XQueryTree, map state isViewable? 1
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 1
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 1
Window created on XQueryTree, map state isViewable? 1
Initializing bailer options...done
Initializing detection options...done
Initializing composite options...done
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Compiz (opengl) - Fatal: glXCreateContext failed
Compiz (bailer) - Info: Ensuring a shell for your session
joe@joe-laptop:~$ Cannot register the panel shell: there is already one running.

---

### Post by sikander3786 on 2011-06-10
You would need to run nvidia-xconfig as 'root' thus the command:

```
sudo nvidia-xconfig
```

Removing the old xorg.conf file as mentioned on the page I linked above helps in some cases like these.

---

### Post by JoeCregeen on 2011-06-10
> **sikander3786 said:**
> You would need to run nvidia-xconfig as 'root' thus the command:

```
sudo nvidia-xconfig
```Removing the old xorg.conf file as mentioned on the page I linked above helps in some cases like these.


Just tried that and it still didn't work, got the following: 

WARNING: Unable to locate/open X configuration file.

New X configuration file written to '/etc/X11/xorg.conf'

and I'd already tried that before, got a "no such file exists" error :/

---

### Post by sikander3786 on 2011-06-10
Ok. What is the output of these commands?

```
/usr/lib/nux/unity_support_test -p
lshw -c video
```

---

### Post by JoeCregeen on 2011-06-10
joe@joe-laptop:~$ /usr/lib/nux/unity_support_test -p
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Error: unable to create the OpenGL context
joe@joe-laptop:~$ lshw -c video
WARNING: you should run this program as super-user.
PCI (sysfs)  

  *-display:0             
       description: VGA compatible controller
       product: Mobile GM965/GL960 Integrated Graphics Controller (primary)
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 0c
       width: 64 bits
       clock: 33MHz
       capabilities: vga_controller bus_master cap_list rom
       configuration: driver=i915 latency=0
       resources: irq:45 memory:fea00000-feafffff memory:e0000000-efffffff ioport:eff8(size=8)
  *-display:1 UNCLAIMED
       description: Display controller
       product: Mobile GM965/GL960 Integrated Graphics Controller (secondary)
       vendor: Intel Corporation
       physical id: 2.1
       bus info: pci@0000:00:02.1
       version: 0c
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: latency=0
       resources: memory:feb00000-febfffff
WARNING: output may be incomplete or inaccurate, you should run this program as super-user.

---

### Post by sikander3786 on 2011-06-10
This part of the output is concerning.

```
Xlib: extension "GLX" missing on display ":0.0".
Xlib: extension "GLX" missing on display ":0.0".
Xlib: extension "GLX" missing on display ":0.0".
Error: unable to create the OpenGL context
```

Seems like your card isn't supporting interlaced modes and thus, OpenGL can't run. Post the output of once more command please.

```
cat /etc/X11/xorg.conf
```

Note, capital 'X' for 'X11'.

And also, go to System > Administration > Additional Drivers and see if any drivers are enabled or not.

---

### Post by JoeCregeen on 2011-06-10
# nvidia-xconfig: X configuration file generated by nvidia-xconfig
# nvidia-xconfig:  version 270.41.06  (buildmeister@swio-display-x86-rhel47-07.nvidia.com)  Mon Apr 18 15:15:12 PDT 2011


Section "ServerLayout"
    Identifier     "Layout0"
    Screen      0  "Screen0" 0 0
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
    ModelName      "Unknown"
    HorizSync       28.0 - 33.0
    VertRefresh     43.0 - 72.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
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


The only additional driver is a Broadcom STA wireless driver. What I don't understand is how it was working fine yesterday, and now this?

---

### Post by sikander3786 on 2011-06-10
Well, the thing we should have noticed before is that you've got an Intel Graphics Chip and have been trying to configure nvidia? Why did you install that tool?

> product: Mobile GM965/GL960 Integrated Graphics Controller (primary)
vendor: Intel Corporation
product: Mobile GM965/GL960 Integrated Graphics Controller (secondary)
vendor: Intel Corporation

Now we first need to find which nvidia packages are installed and then we would remove them. Please post the output of this command:

```
dpkg -l | grep nvidia
```

Later, we would reconfigure your xserver and hopefully, Unity would be back to normal.

---

### Post by JoeCregeen on 2011-06-10
I didn't knowingly install it, it has just appeared! Ah well at least you noticed! Here you are:

ii  nvidia-common                                            0.2.30                                                     Find obsolete NVIDIA drivers
ii  nvidia-current                                           270.41.06-0ubuntu1                                         NVIDIA binary Xorg driver, kernel module and VDPAU library
ii  nvidia-settings                                          270.29-0ubuntu1                                            Tool of configuring the NVIDIA graphics driver

---

### Post by mc4man on 2011-06-10
@JoeCregeen - 
I don't have any any newer hardware here or a setup with 2 video solutions so can't help you.
Do you have one of those optimus laptops?

---

### Post by sikander3786 on 2011-06-10
Remove the nvidia packages by:

```
sudo apt-get remove --purge nvidia-current nvidia-common nvidia-settings
```

Remove the old xorg.conf:

```
sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.bad
```

Reconfigure the graphics:

```
sudo dpkg-reconfigure -phigh xserver-xorg
```

Reboot:

```
sudo reboot now
```

---

### Post by JoeCregeen on 2011-06-10
> **mc4man said:**
> @JoeCregeen - 
I don't have any any newer hardware here or a setup with 2 video solutions so can't help you.
Do you have one of those optimus laptops?

Nope, an old Dell Inspiron 1525 that I've dual-booted Vista and Ubuntu on. I honestly have no idea what I've done to it, everything else is absolutely fine except Unity not working.

---

### Post by JoeCregeen on 2011-06-10
@[sikander3786]("http://ubuntuforums.org/member.php?u=806649") 

All back to normal now, can't thank you enough! *buys virtual beer*

People like you are what makes Ubuntu so great, really, thank you.

---

### Post by sikander3786 on 2011-06-10
You are more than Welcome :)

You can now mark this thread Solved using [COLOR="Red"]**Thread Tools**[/COLOR] near the top of this page so other users with the same problem can find your thread.

Happy Ubuntu-ing!

---

