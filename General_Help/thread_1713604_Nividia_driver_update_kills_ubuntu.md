---
title: "Nividia driver update kills ubuntu"
date: 2011-03-24
forum: General Help
---

### Post by stanley82 on 2011-03-24
I got a new lcd wide screed and updated the driver to my nivdia 7800gt card.  First with the driver checked by ubuntu but that only did vga and cga modes.  Next I went to nividia and pulled over their driver after that and it changing the kernel, Horror, it will not boot nor boot the recover from grub.  When I try to reinstall 10.04 it starts ok and sort of stops.  alt cont F1 does nothing live boot or from the 500g hard drive.  I also have an 80g drive with 8.04 and when I boot from that it gives me my login screen less any icons names etc.  I can feel my way through the login and again no icons.  alt cont F1 gives me a big unix type terminal.  I've also tried with the video card removed using the default video on the motherboard, different but similar.  I've also re-flashed bios, I'd refreshed it previously so this bios was working.  Any ideas greatly appreciated.  Ian

---

### Post by stanley82 on 2011-03-25
Me again.  What I've done is to remove the Nvida card from the PCIEX and put an ATI Rage 2c into a PCI slot.  That got me going in low graphics mode.  system preferences monitors still gave me the Nivida picture.  After a couple of re-boots I made low graphics mode the default and junked the Nvida from the packet manager.  Once I regain my cool I'll try the Nvidia again.  Maybe I should invest in a Ubuntu supported card.  Any suggestions?  Also I do not understand how PnP works.  If I put the Nvida back will it plug and play or garbage once booted in place of asking for password?  Strange stuff Ian.

---

### Post by realzippy on 2011-03-25
Step by step please...

Was your 7800 GT running fine with the nvidia-driver before you changed your monitor?
What model was the old one and which is the new one?

---

### Post by stanley82 on 2011-03-25
Yes, my Nvidia 7800gt was fine using an antique 19" 4:3 colour thing that I could just lift.  It was fine on the new acer 20" 1600 by 800 wide screen and I hoped that the new driver would use the full monitor resolution.  I seem to remember getting a one-size-fits-all driver from Nvidia (not able to find the install files) and that was what I was using for a couple of years.  System admin hardware-driver auto installed an Ubuntu approved driver but that seemed to be worse than what I had so I went to Nvidia and dug out NVIDIA-Linux-x86_64-260.19.44.run and oh-dear when I re-booted the screen was an interesting green mess looking like an amebia on the point of division.  Doing anything was difficult since when I got to the log-in screen all was not clear though cnt alt F1 got the tty1 terminal.
My antique ATI card well at first system preferences monitors tells me (and still does) " It appears that your graphics driver does not support the necessary extensions to use this tool.  Do you want to use your graphics driver vendor's tool instead? " But when I clicked yes I have the option to go from 800 x 600 (3/4) to 1360 x 768 (16/9) so it's not too bad right now.  Also to note after I had installed the ATI card I used the package manager to junk the Nvidia driver.  System preferences monitors was still Nvidia and telling me to run something to activate an x server which failed to activate so that was no use to me.

---

### Post by stanley82 on 2011-03-25
Stranger and stranger System Preference Monitors now gives me the Nvidia x server setting window and I also have a Nvidia tab in System Preferences.  It does not seem stable.
No not correct, if I go YES I get the Nvidia server window NO gives me a monitor resolution so that's better.  Maybe I should have used NO with the Nvidia card but when I had the Nvidia fitted all I could see was lots of x-server stuff that I do not understand.

Also I have top left on my screen a pink box with Unknown inside.
Looking in the package manager I still have 9 Nvidia files and I'm not keen on removing them as they look as though they are needed to identify the video card that's installed.
I also have a similar set for ATI.

---

### Post by realzippy on 2011-03-27
You have a xorg.conf file?Post the output..

```
gedit /etc/X11/xorg.conf
```

---

### Post by stanley82 on 2011-03-27
It looks to be not there.  Here is the contents of the directory
====================================
stan@stan:/etc/X11$ ls -l
total 88
drwxr-xr-x 2 root root  4096 2010-04-29 08:43 app-defaults
drwxr-xr-x 2 root root  4096 2010-04-29 08:43 cursors
-rw-r--r-- 1 root root    14 2010-04-29 08:44 default-display-manager
drwxr-xr-x 6 root root  4096 2010-04-29 08:39 fonts
-rw-r--r-- 1 root root 17394 2009-12-03 05:56 rgb.txt
lrwxrwxrwx 1 root root    13 2010-05-24 20:27 X -> /usr/bin/Xorg
drwxr-xr-x 3 root root  4096 2010-04-29 08:43 xinit
drwxr-xr-x 2 root root  4096 2010-04-15 08:12 xkb
-rw-r--r-- 1 root root   216 2011-03-22 20:15 xorg.conf-backup-110322201447
-rw-r--r-- 1 root root  1339 2011-03-24 16:31 xorg.conf-backup-110324163046
-rw-r--r-- 1 root root  1339 2011-03-25 05:46 xorg.conf-backup-110325054405
-rw-r--r-- 1 root root   269 2011-03-25 05:44 xorg.conf.failsafe
-rwxr-xr-x 1 root root   709 2010-04-01 07:19 Xreset
drwxr-xr-x 2 root root  4096 2010-04-29 08:24 Xreset.d
drwxr-xr-x 2 root root  4096 2010-04-29 08:24 Xresources
-rwxr-xr-x 1 root root  3730 2010-04-01 07:07 Xsession
drwxr-xr-x 2 root root  4096 2011-01-19 07:39 Xsession.d
-rw-r--r-- 1 root root   265 2008-07-01 13:41 Xsession.options
-rw------- 1 root root   601 2010-04-29 08:24 Xwrapper.config
stan@stan:/etc/X11$ ^C
stan@stan:/etc/X11$ 
and her is the contents of xorg.conf-backup-110325054405
=============================================
# nvidia-xconfig: X configuration file generated by nvidia-xconfig
# nvidia-xconfig:  version 260.19.44  (buildmeister@swio-display-x86-rhel47-08.nvidia.com)  Sun Feb 27 22:59:57 PST 2011

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
================================
I hope that this can help you and thanks for helping me.  Regards Ian.

---

### Post by realzippy on 2011-03-27
If you have the nvidia card plugged in,run

```
sudo nvidia-xconfig
```

post error output or restart X server

---

### Post by stanley82 on 2011-03-28
After removing the ATI card and inserting the Nvidia it gets as far as grub then the video signal is lost.  I have failed to log in blind using cnt alt F1 though the log in music could be heard.  Using the ATI card this is what I'm getting
stan@stan:~$ sudo nvidia-xconfig
sudo: nvidia-xconfig: command not found
stan@stan:~$ 
Regards Ian.

---

### Post by stanley82 on 2011-03-28
I did 
sudo apt-get purge nvidia*
sudo apt-get purge jokey
sudo apt-get jockey-gtk
sudo apt-get nvidia-current.
sudo nvidia-xconfig
stan@stan:/etc/X11$ sudo nvidia-xconfig

Using X configuration file: "/etc/X11/xorg.conf".
Backed up file '/etc/X11/xorg.conf' as '/etc/X11/xorg.conf.backup'
New X configuration file written to '/etc/X11/xorg.conf'

Then changed the ATI card to Nvidia.
Rebooted gurb okay login okay then the monitor reported format not supported.  So I re-booted in recover mode and got into low graphics mode and system/preference/monitors
It appears that your graphics driver does not support the necessary extensions to use this tool.  Do you want to use your graphics driver vendor's tool instead?
Yes
You do not appear to be using the NVIDIA X driver.  Please edit your X configuration file (just run `nvidia-xconfig` as root), and restart the X server.
and I did it again. no joy.
No
and I'm stuck with 800 by 600 3:4.
I rebooted no change after all this effort I'm still in low res graphics.

---

### Post by realzippy on 2011-03-29
I suggest to :

Plug in nvidia-card and the old 19" VGA monitor and reinstalling the nvidia driver.If the driver works (again),we can edit the xorg.conf to the needs of your new LCD monitor (model?)...

---

### Post by stanley82 on 2011-03-29
I've got it going, this is what I did:-
I plugged in the ATI card without nvidia then
sudo apt-get purge nvidia*
sudo apt-get purge jokey
sudo apt-get install jockeyk-gtk
suso apt-get install nvidia-current
Then powered down and put the nvidia card back after removing the ATI card.  I had to reboot a couple of times using restore then system/Preferences/monitor
NO I could only get 800 by 600 (3:4) max
YES use vendors tool gave me a limited nvidia settings window that I never really understood or made any used to advantage.
     Any way this is where I got mixed when I originally started the monitor upgrade and became lost originally I think.
     I then did
sudo apt-get install nvidia-settings
x display configuration and got a better nvidia settings window and selected the 1600 by 900 (16:9) and it's great.  This should be what you get from X server settings tab in the nvidia settings if you click in the good spots.  Many thanks for all the help Ian.

---

### Post by realzippy on 2011-03-30
...so you have plugged in the new monitor and everything is as it should be?

---

