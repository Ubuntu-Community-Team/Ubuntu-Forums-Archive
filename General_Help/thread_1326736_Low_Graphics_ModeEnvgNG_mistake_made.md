---
title: "Low Graphics Mode/EnvgNG mistake made"
date: 2009-11-14
forum: General Help
---

### Post by Pontebantam on 2009-11-14
Dear all,

used EnvyNG and made a rather silly cock up trying to install updated drivers for my 9200 PRO card.  In hindsight should just use the drivers already available in Ubuntu.

Now I get the 'Low Graphics Mode' issue so could someone just remind me how I revert back to the default drivers ?

Have uninstalled EnvyNG already, so now need to bring the old ones back.

All help appreciated!


Vinny

---

### Post by Mark Phelps on 2009-11-14
Follow the directions in the link below to remove the restricted drivers and replace them with the open source drivers:

[https://help.ubuntu.com/community/RadeonDriver]("https://help.ubuntu.com/community/RadeonDriver")

---

### Post by Pontebantam on 2009-11-14
> **Mark Phelps said:**
> Follow the directions in the link below to remove the restricted drivers and replace them with the open source drivers:

[https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver)


Just done that - however I am a newbie....i've done I think what was correct but when rebooting the system I got an (EE) Error parsing the config file message and back to asking me if I want to run in low graphics mode

xconfig file looks liks this :

Section "Device"
        Identifier      "Radeon 9600PRO"
        Driver          "ati"
        BusID           "PCI:1:0:0"
        Option          "AccelMethod"    "XAA"
        Option          "XAANoOffscreenPixmaps"
        Option        "BusType" "PCI"
        Option         "AGPMode" "1"
EndSection

Section "Monitor"
        Identifier      "Generic Monitor"
        Option          "DPMS"
        HorizSync       28-72
        VertRefresh     43-60
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Device          "Radeon 9600"
        Monitor         "Generic Monitor"
        DefaultDepth    24
        SubSection "Display"
                Depth           24
                Modes           "1440x900" "1024x768"
        EndSubSection
EndSection
Section "DRI"
        Mode 0666
EndSection

Section "Extensions"
        Option "Composite" "Enable"
EndSection

Section "ServerLayout"
        Identifier      "Default Layout"
        Screen          "Default Screen"
        InputDevice     "Generic Keyboard"
        InputDevice     "Configured Mouse"
EndSection


Stumped as really no idea what I'm doing !

Vinny

---

### Post by Pontebantam on 2009-11-15
Realised I made a mistake (I created a new xorg.config file in home dir when I should have edited the xorg.conf in etc/X11) - have now edited the xorg.conf file in /etc/X11 to look like this:

Section "Device"
        Identifier      "Radeon 9600PRO"
        Driver          "ati"
        BusID           "PCI:1:0:0"
        Option          "AccelMethod"    "XAA"
        Option        "BusType" "PCI"
        Option         "AGPMode" "1"
EndSection

Section "Monitor"
        Identifier      "Generic Monitor"
        HorizSync       28-72
        VertRefresh     43-60
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Device          "Radeon 9600PRO"
        Monitor         "Generic Monitor"
        DefaultDepth    24
        SubSection "Display"
                Depth           24
Modes           "1440x900" "1024x768"
        EndSubSection
EndSection

Section "DRI"
        Mode 0666
EndSection

Section "Extensions"
        Option "Composite" "Enable"
EndSection

Section "ServerLayout"
        Identifier      "Default Layout"
        Screen          "Default Screen"
        InputDevice     "Generic Keyboard"
        InputDevice     "Configured Mouse"
EndSection


However when it asks me to restart the Xserver using the following :

sudo /etc/init.d/gdm restart

I get the error message that instead of running init scrips within /etc i should use the service command.

Help please - i'm still getting the (EE) error parsing the config file and I still haven't quite sussed out what i'm doing !

lspci gives me 

01:00.0 VGA compatible controller: ATI Technologies Inc RV280 [Radeon 9200 PRO] (rev 01)
01:00.1 Display controller: ATI Technologies Inc RV280 [Radeon 9200 PRO] (Secondary) (rev 01)
01:08.0 Ethernet controller: Intel Corporation 82562EZ 10/100 Ethernet Controller (rev 02)

glxinfo | grep vendor  gives me

server glx vendor string: SGI
client glx vendor string: SGI
OpenGL vendor string: Mesa Project



Vinny

---

### Post by Pontebantam on 2009-11-19
Afternoon all - still getting following problem on boot up:

(EE) Error parsing config file
(EE) Unable to parse config file

After accepting this, then goes again to option where i can start ubuntu in low graphics mode

No obvious difference when i log in at that point,all looks as it did before, however when i go to System > Administration > Nvidia X Server settings I get the following :

You do not appear to be using the NVIDIA X driver. Please edit your X configuration file (just run `nvidia-xconfig` as root), and restart the X server. 

Can anyone adive how to do this/really want to get rid of the problems (see previous comments made!)

Vinny

---

### Post by Pontebantam on 2009-11-19
Reread the original article suggested and did a 

lspci -nn | grep VGA

which gave me

01:00.0 VGA compatible controller [0300]: ATI Technologies Inc RV280 [Radeon 9200 PRO] [1002:5960] (rev 01)

Spot the mistake....

Have amended xorg.config based on this will see what happens now.....

---

### Post by Pontebantam on 2009-11-19
> **Pontebantam said:**
> Reread the original article suggested and did a 

lspci -nn | grep VGA

which gave me

01:00.0 VGA compatible controller [0300]: ATI Technologies Inc RV280 [Radeon 9200 PRO] [1002:5960] (rev 01)

Spot the mistake....

Have amended xorg.config based on this will see what happens now.....


The answer is bugger all - still got same problem! ARGH !

---

### Post by Pontebantam on 2009-11-19
> **Pontebantam said:**
> The answer is bugger all - still got same problem! ARGH !

just deleted xorg.conf and the messages went away

not sure if this is the best option......

---

