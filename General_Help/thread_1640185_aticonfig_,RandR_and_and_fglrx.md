---
title: "aticonfig ,RandR and and fglrx"
date: 2010-12-07
forum: General Help
---

### Post by luka1002 on 2010-12-07
All started a few day ago when i installed Ubuntu Maverick. Using Dual  Monitors Display which in windows i get no problems. So when  installation completed i get mirror display, i sad ok now i will set it  to extended desktop and all ok. I did that but my default monitor is  always small one (left). 

So i read and read on net and i noticed that i need new drivers. 

so i started: Using this guide i did install new drivers and working:

[http://wiki.cchtml.com/index.php/Ubuntu_Maverick_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Maverick_Installation_Guide)

But this still does not fixed "primary monitor problem". So i go further..

I found script that alow to set primary screen: 

[http://www.thetechrepo.com/main-articles/502-how-to-change-the-primary-monitor-in-ubuntu-or-other-linux-distributions](http://www.thetechrepo.com/main-articles/502-how-to-change-the-primary-monitor-in-ubuntu-or-other-linux-distributions)

it goes like this:

 -------------------------------------
#!/bin/bash
# Author: Andrew Martin
# Credit: [http://ubuntuforums.org/showthread.php?t=1309247](http://ubuntuforums.org/showthread.php?t=1309247)
echo "Enter the primary display from the following:"            # prompt for the display
xrandr --prop | grep "[^dis]connected" | cut --delimiter=" " -f1    # query connected monitors
 
read choice                                # read the users's choice of monitor
 
xrandr --output $choice --primary                    # set the primary monitor

-------------------------------------
Fortunately, the [FONT=courier new]xrandr[/FONT]  utility can easily switch which monitor is the primary. Copy and paste  the following script into a text file called monitor-switcher.sh.     
Once saved, make it executable by typing [FONT=courier new]chmod +x monitor-switcher.sh[/FONT] into the terminal. Then, run it by typing [FONT=courier new]./monitor-switcher.sh[/FONT].  The script will then display a list of all detected monitors - type in  the displayed name of the monitor you wish to make primary and hit  enter. The script will then change the primary monitor immediately. 
-------------------------------------

When i save it to monitor-switcher.sh and run it i get this:

./monitor-switcher.sh
Enter the primary display from the following:
Xlib:  extension "RANDR" missing on display ":0.0".
RandR extension missing

So ,start to read again and found that i can use aticonfig or RandR???
U said i have ati installed oi u supposed that i need to use aticonfig.

followed the guide:

[http://wiki.cchtml.com/index.php/Configuring](http://wiki.cchtml.com/index.php/Configuring)

to get only information type:

aticonfig --query-monitor

and i get:

aticonfig --query-monitor
Error: option --query-monitor is not supported when RandR 1.2 is enabled!

Now i am ](*,)... 

Can someone please tell me what i need to do and clarify me what is fglrx ,RandR and Whay is he enabled???  
Using aTI RADEON 3870

here is my xorg.conf:


```

```Section "ServerLayout"
    Identifier     "aticonfig Layout"
    Screen      0  "aticonfig-Screen[0]-0" 0 0
    Screen         "amdcccle-Screen[2]-1" 1366 0
EndSection

Section "ServerFlags"
    Option        "Xinerama" "on"
EndSection

Section "Monitor"
    Identifier   "aticonfig-Monitor[0]-0"
    Option        "VendorName" "ATI Proprietary Driver"
    Option        "ModelName" "Generic Autodetecting Monitor"
    Option        "DPMS" "true"
EndSection

Section "Monitor"
    Identifier   "0-DFP1"
    Option        "VendorName" "ATI Proprietary Driver"
    Option        "ModelName" "Generic Autodetecting Monitor"
    Option        "DPMS" "true"
    Option        "PreferredMode" "1366x768"
    Option        "TargetRefresh" "60"
    Option        "Position" "0 0"
    Option        "Rotate" "normal"
    Option        "Disable" "false"
EndSection

Section "Monitor"
    Identifier   "0-DFP2"
    Option        "VendorName" "ATI Proprietary Driver"
    Option        "ModelName" "Generic Autodetecting Monitor"
    Option        "DPMS" "true"
    Option        "PreferredMode" "1680x1050"
    Option        "TargetRefresh" "60"
    Option        "Position" "0 0"
    Option        "Rotate" "normal"
    Option        "Disable" "false"
EndSection

Section "Device"
    Identifier  "aticonfig-Device[0]-0"
    Driver      "fglrx"
    Option        "UseFastTLS" "1"
    Option        "Monitor-DFP1" "0-DFP1"
    BusID       "PCI:2:0:0"
EndSection

Section "Device"
    Identifier  "amdcccle-Device[2]-1"
    Driver      "fglrx"
    Option        "Monitor-DFP2" "0-DFP2"
    BusID       "PCI:2:0:0"
    Screen      1
EndSection

Section "Screen"
    Identifier "aticonfig-Screen[0]-0"
    Device     "aticonfig-Device[0]-0"
    DefaultDepth     24
    SubSection "Display"
        Viewport   0 0
        Depth     24
    EndSubSection
EndSection

Section "Screen"
    Identifier "amdcccle-Screen[2]-1"
    Device     "amdcccle-Device[2]-1"
    DefaultDepth     24
    SubSection "Display"
        Viewport   0 0
        Depth     24
    EndSubSection
EndSection```

```

---

### Post by realzippy on 2010-12-08
What happens when running

```
sudo aticonfig --initial=dual-head --screen-layout=right
```

restart X or reboot.

fglrx is the proprietary ATI display driver you have installed,aticonfig is it's configuration tool.
..*randr* or *xrandr* is the standard display config tool,you should prefer *aticonfig* unless it does not work.

---

### Post by luka1002 on 2010-12-08
```
sudo aticonfig --initial=dual-head --screen-layout=right
[sudo] password for luka: 
Found fglrx primary device section
Found fglrx secondary device section
Using xorg.conf
Saving back-up to xorg.conf.fglrx-0
```t is the same as before.... i mean main display is still left

```
Section "ServerLayout"
    Identifier     "aticonfig Layout"
    Screen      0  "aticonfig-Screen[0]-0" 0 0
    Screen         "amdcccle-Screen[2]-1" 1366 0
EndSection

Section "ServerFlags"
    Option        "Xinerama" "on"
EndSection

Section "Monitor"
    Identifier   "aticonfig-Monitor[0]-0"
    Option        "VendorName" "ATI Proprietary Driver"
    Option        "ModelName" "Generic Autodetecting Monitor"
    Option        "DPMS" "true"
EndSection

Section "Monitor"
    Identifier   "0-DFP1"
    Option        "VendorName" "ATI Proprietary Driver"
    Option        "ModelName" "Generic Autodetecting Monitor"
    Option        "DPMS" "true"
    Option        "PreferredMode" "1366x768"
    Option        "TargetRefresh" "60"
    Option        "Position" "0 0"
    Option        "Rotate" "normal"
    Option        "Disable" "false"
EndSection

Section "Monitor"
    Identifier   "0-DFP2"
    Option        "VendorName" "ATI Proprietary Driver"
    Option        "ModelName" "Generic Autodetecting Monitor"
    Option        "DPMS" "true"
    Option        "PreferredMode" "1680x1050"
    Option        "TargetRefresh" "60"
    Option        "Position" "0 0"
    Option        "Rotate" "normal"
    Option        "Disable" "false"
EndSection

Section "Device"
    Identifier  "aticonfig-Device[0]-0"
    Driver      "fglrx"
    Option        "UseFastTLS" "1"
    Option        "Monitor-DFP1" "0-DFP1"
    BusID       "PCI:2:0:0"
EndSection

Section "Device"
    Identifier  "amdcccle-Device[2]-1"
    Driver      "fglrx"
    Option        "Monitor-DFP2" "0-DFP2"
    BusID       "PCI:2:0:0"
    Screen      1
EndSection

Section "Screen"
    Identifier "aticonfig-Screen[0]-0"
    Device     "aticonfig-Device[0]-0"
    DefaultDepth     24
    SubSection "Display"
        Viewport   0 0
        Depth     24
    EndSubSection
EndSection

Section "Screen"
    Identifier "amdcccle-Screen[2]-1"
    Device     "amdcccle-Device[2]-1"
    DefaultDepth     24
    SubSection "Display"
        Viewport   0 0
        Depth     24
    EndSubSection
EndSection
```

---

### Post by realzippy on 2010-12-08
?,,,so try:

```
sudo aticonfig --initial=dual-head --screen-layout=left

```

---

### Post by luka1002 on 2010-12-08
> **realzippy said:**
> ?,,,so try:

```
sudo aticonfig --initial=dual-head --screen-layout=left

```


i tried that right after  layout right...but same again... nothing changed..

---

### Post by realzippy on 2010-12-10
Sorry,no idea.Also I never used ati cards in linux,so I am not experienced with the fglrx driver,which seems to be still buggy.
Since there are some "fglrx experts/users" out here in the forum,I highly recommend to open a new thread,titled:

   Problems with dual monitor setup in maverick + fglrx

or similar,important to name *fglrx* in threadtitle to get replies..

Edit:
...you are not alone,e.g.:
[http://ubuntuforums.org/showthread.php?t=1592372](http://ubuntuforums.org/showthread.php?t=1592372)
So what is your output from:

```
xrandr
```

Please run it with

1rst Monitor connected,then  again with both (2nd is left of or right of 1rst?) and post both outputs...

---

### Post by luka1002 on 2010-12-10
> **realzippy said:**
> Sorry,no idea.Also I never used ati cards in linux,so I am not experienced with the fglrx driver,which seems to be still buggy.
Since there are some "fglrx experts/users" out here in the forum,I highly recommend to open a new thread,titled:

   Problems with dual monitor setup in maverick + fglrx

or similar,important to name *fglrx* in threadtitle to get replies..

Edit:
...you are not alone,e.g.:
[http://ubuntuforums.org/showthread.php?t=1592372](http://ubuntuforums.org/showthread.php?t=1592372)
So what is your output from:

```
xrandr
```Please run it with

1rst Monitor connected,then  again with both (2nd is left of or right of 1rst?) and post both outputs...


i run it with only first monitor ,then with both.. Output is same:

```
Xlib:  extension "RANDR" missing on display ":0.0".
RandR extension missing

```My 2nd is right of 1rst

opened new topic:
[http://ubuntuforums.org/showthread.php?p=10223460#post10223460](http://ubuntuforums.org/showthread.php?p=10223460#post10223460)

---

### Post by raucous1 on 2010-12-21
Ya. I am having basically the same problem. 

I can't select which monitor (one dvi, the other HDMI) is primary.

Also, when I connect the HDMI to my monitor (the other is a HDTV), I get weird display issues where the screen is basically 'letter-boxed' with black bars all around.

---

