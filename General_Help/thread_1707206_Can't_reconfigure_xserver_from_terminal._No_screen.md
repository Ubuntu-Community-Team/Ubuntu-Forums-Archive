---
title: "Can't reconfigure xserver from terminal. No screens."
date: 2011-03-15
forum: General Help
---

### Post by Rubicon421 on 2011-03-15
I was getting an error when trying to enable desktop effects that said something about Composite extension not available. I tried a different nvidia driver that was found with the additional drivers option and restarted.   Then I started getting an error saying there are no screens available and I couldn't log into the GUI/desktop. I just get stuck at a terminal.   I tried several commands to reconfigure, uninstall/reinstall, and edit xorg.conf and xserver.org but I keep getting errors saying it's not found or unable to locate package.   Now when I restart, I get a terminal asking me to log in. once I log in I get FATAL SERVER ERROR: NO SCREENS FOUND  I've tried to find a solution but no luck.

---

### Post by -dean- on 2011-03-18
My situation is similar.
I am running 10.10, 2.6.35-27-generic
I have an Nvidia 6200 and am running a 2.53-GHz P4 older Gateway 700xl w/1Gb rdram.  I don't remember doing anything special and have been running this setup for a long time through updates and upgrades with never a glitch like this.
 When I boot up the system goes to the start up tune but there is no gui and when I try to re-boot with my keyboard shortcut I get nothing.  I can access the command line consoles with Ctrl-Alt F1 thru F6.  I executed "apt-get update" and "apt-get upgrade" this morning in hopes that a new kernel would fix things but though Google Chrome updated the kernel did not.  When I restart the computer in recovery mode and try Failsafex I am ultimately taken to a message "[COLOR="Red"]Fatal server error[/COLOR]:  no screens found".  This machine does have a redundant Ubuntu 10.10 and I am able to access and manipulate files on the broken installation and I have a copy of Xorg.failsafe.log.

Any reply would be appreciated.

---

### Post by WorMzy on 2011-03-18
Have you tried uninstalling the nvidia drivers?

```
sudo apt-get purge nvidia-current
```

If you don't have nvidia-current installed, check what you *do* have installed with
```
dpkg -l '*nvidia*' | less
```

Exit less with ```
q
```

Then amend the apt-get command.

Then restart/reconfigure X.

---

### Post by -dean- on 2011-03-18
Anything is worth a shot.
Thanks.
I'll post how it works out.
What do you mean "Then amend the apt-get command"?
    restart/reconfigure X?  Is this a command line entry?

I am not much of a command line cowboy, but I'm not afraid to mount up.

---

### Post by WorMzy on 2011-03-18
By amend, I mean change the "apt-get purge" command, if you didn't have nvidia-current installed. Change it to ```
sudo apt-get purge nvidia-173
``` or whatever dpkg showed as being installed.

By reconfigure X, I mean run

```
sudo dpkg-reconfigure xserver-xorg
```

If that doesn't help, then deleting /etc/X11/xorg.conf should be fine if you're using the more recent versions of Ubuntu (10.04, 10.10, or the upcoming 11.04)

```
sudo rm /etc/X11/xorg.conf
```

---

### Post by -dean- on 2011-03-18
Thanks for replying.  Since you are in England and I am on the U.S. west coast I figured some delay.
I ran the dpkg -l command.
Since I don't know how to print from the command line I was overwhelmed with the information listed as  "Name" - "Version" - and "something else".  Probably what you suggest is listed in the "something else" category.  I did hand copy the beginning information of the output, i.e.:

Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst?Conf-files/Unpacked/ha1F-conf/Half-inst/trig-aWait/trig-pend
| Err?=(none)/reinst-required (Status, Err: uppercase=bad)

I don't comprehend any of this.

If I were to purge nvidia could I not reboot and hope for an open source driver to at least provide a gui?  Or is that what sudo dpkg-reconfigure xserver-xorg will give me?

---

### Post by WorMzy on 2011-03-18
That dpkg command should give you a list of installed packages, with some reference to nvidia in their names. For example, here's mine:

```
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Conf-files/Unpacked/halF-conf/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name                                 Version                                           Description
+++-====================================-=================================================-==========================================================================
ii  nvidia-173-modaliases                173.14.28-0ubuntu1                                Modaliases for the NVIDIA binary X.Org driver
ii  nvidia-96-modaliases                 96.43.18-0ubuntu1                                 Modaliases for the NVIDIA binary X.Org driver
ii  nvidia-common                        0.2.24                                            Find obsolete NVIDIA drivers
**ii  nvidia-current                       260.19.06-0ubuntu1                                NVIDIA binary Xorg driver, kernel module and VDPAU library**
ii  nvidia-current-modaliases            260.19.06-0ubuntu1                                Modaliases for the NVIDIA binary X.Org driver
un  nvidia-glx                           <none>                                            (no description available)
ii  nvidia-settings                      260.19.06-0ubuntu1                                Tool of configuring the NVIDIA graphics driver

```

You can ignore the header. I'm sure it's useful to someone, but mostly, it's just unnecessary clutter.

As you can see in my output, nvidia-current is installed, and provides the binary driver, as well as the kernel module. If, when you tried to uninstall nvidia-current, you got an error message (something like "E: unable to find package nvidia-current"), then you need to check dpkg's output to see which version of the driver you actually have installed, and then change the apt-get command to remove that package instead.

When you purge the nvidia driver, I /think/ nouveau (the open source community's attempt at creating an nvidia driver) should be loaded instead at boot up. Ubuntu's pretty good at autodetecting which modules you need.

---

### Post by -dean- on 2011-03-19
#7
WorMzy I think you have nailed it for me.  I haven't gone through your steps yet but I have been scrambling around in my own (gui) way.  
In the troublesome 10.10 installation I found that the Nvidia referenced is "/usr/src/nvidia-current-260.19.06". 
In the working 10.10 installation I find that the Nvidia installation is /usr/src/nvidia-current-173-173.14.28.

From what you have told me I presume the first thing I have to do is "sudo apt-get purge nvidia-current",then restart, then "sudo dpkg-reconfigure xserver-xorg" in a command console.  Could you confirm please.  And thanks a bunch!!

---

### Post by -dean- on 2011-03-19
Still no screen WorMzy.
I ran "sudo apt-get purge nvidia-current" and rebooted.
I ran "sudo dpkg-reconfigure xserver-xorg" and "startx".  Nothing in the gui console.  Rebooted.  When I reboot the end result is a readout, the last item is "*Starting TiMidity** Alsa midi emulation..." followed by a blinking cursor.
I ran "sudo rm /etc/X11/xorg.conf" and "startx".  Nothing but a note that suggested I remove /etc/.X0-lock, which I did. Rebooted.  No gui console on reboot.

On checking /usr/src/ in the offending 10.10 installation there is no nvidia folder at this time.  

Is it possible to do an "apt-get install nvidia-173"?

---

### Post by WorMzy on 2011-03-19
Sure, it's possible. I'm not sure that using an older driver would help though.

Something else you can try is using nvidia's script to generate an xorg.conf file instead of dpkg-reconfigure.

After installing nvidia driver (any version), first make sure that there isn't an xorg.conf file by running:
```
sudo rm /etc/X11/xorg.cong
```
then run the nvidia script to generate a new one:
```
sudo nvidia-xconfig
```

---

### Post by -dean- on 2011-03-19
Thanks for your help WorMzy.

I ran everything you gave me plus, I found a blog: http:/blog.matinsladek.com/2010/07/linux-nvidia-legacy-geforce2-96.html, that contained all of the commands that you suggested, plus a few more.  Still no luck.  No gnome desktop...no desktop at all.  I really hate to give up.  I have no doubt that there is a command or two in the ubuntu/linux lineup that will get my desktop back.  Any more suggestion?

---

### Post by WorMzy on 2011-03-20
I'm afraid that all I can suggest now is manually editing xorg.conf and seeing if you can fix the problem that way. This may help with that: [http://www.linux.com/news/software/applications/8201-editing-basics-for-the-xorgconf-file](http://www.linux.com/news/software/applications/8201-editing-basics-for-the-xorgconf-file)

Here's mine, for comparison:
```
# nvidia-settings: X configuration file generated by nvidia-settings
# nvidia-settings:  version 260.19.29  (buildmeister@swio-display-x86-rhel47-04.nvidia.com)  Wed Dec  8 12:27:27 PST 2010

# nvidia-xconfig: X configuration file generated by nvidia-xconfig
# nvidia-xconfig:  version 1.0  (buildmeister@builder58)  Fri Mar 12 02:12:40 PST 2010

Section "ServerLayout"
    Identifier     "Layout0"
    Screen      0  "Screen0" 0 0
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
    Option         "Xinerama" "0"
EndSection

Section "Files"
EndSection

Section "ServerFlags"
    Option         "AutoAddDevices" "False"
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
    Option         "XkbLayout" "gb"
    Option         "XkbVariant" ""
EndSection

Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "LG Electronics M227WDP"
    HorizSync       30.0 - 83.0
    VertRefresh     56.0 - 75.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 8800 GTX"
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "TwinView" "0"
    Option         "metamodes" "1920x1080_60 +0+0"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection

```


If you still can't get it working, it may be easiest to back up all your work, and reinstall Ubuntu.

---

### Post by Rubicon421 on 2011-03-20
Sorry about the delay in responding- I ended up doing a reinstall to fix the issue so I don't know which one of the above fixes would have worked in my case. I see there are a few other people with a similar issue who are finding help here so I'm not going to mark is as solved yet. 

I was able to figure out that part of the issue (if not all) was due to choosing 'separate X screens' instead of 'twinview' in the nVidia settings manager. I wanted my second monitor to be an extension of the first so I could drag windows from one to the other. I thought twinview was the same as cloning the screens so I chose separate x screens. After some reading I saw that twinview could do what I was looking for so after the restore I used twinview and haven't had a problem.

---

### Post by -dean- on 2011-03-20
Thanks again WorMzy.
I will check the xorg.conf files.  As I have indicated before, I have a redundant Ubuntu installation on a different drive on the same disk.  I will make a comparison between yours, my broken Ubuntu, and my working setup.

All this turmoil is good exercise for an aging brain.  And I hope that I can reinstall Ubuntu and use the same /home directory with limited problems if all else fails.

---

