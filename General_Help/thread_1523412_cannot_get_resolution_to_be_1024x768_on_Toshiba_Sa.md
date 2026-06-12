---
title: "cannot get resolution to be 1024x768 on Toshiba Satellite Laptop"
date: 2010-07-03
forum: General Help
---

### Post by Spyler25 on 2010-07-03
I have recently installed Ubuntu on my Toshiba Satellite A25-S207 Laptop.  Everything runs great except that the resolution will not go above 800x600.  

I had this problem before on the same laptop and was able to fix it but cannot find the fix now (I had to wipe my laptop clean in order to remove some pesky Windows partitions and reinstall Ubuntu)

I have found several "fixes" but none work.  I tried the one below as well as it applies almost perfectly to my problem

[COLOR=Navy]"I just installed the latest ubuntu 10.04 on a Toshiba-Tecra having  "Trident Microsystems Cyberblade XP4m32" Monitor. After install  resolution is defaulted to 800x600. I followed a method advised in some  threads (arount xrandr and cvt) to increase the size (my laptop works  with 1024x768 under XP). This was done OK and I obtained the resolution  1024X768 appearing in the drop list resolution options of the Monitor  preferences but when I select the option if fails. Alternatively, when I  execute
$ xrandr --output default --mode 1024x768_60.00
i got the message "xrandr : screen cannot be larger than 800x600  (desired size 1024X768)

I also saw a possible fix proposing to add "HorizSync 31.50-48.00" in  Xorg.conf but I then I DO NOT have such a file in my /etc/x11/ after  ubuntu install (supposing that this will fix my problem !!!)

Thanks to help me to progress
Boot into recovery mode, when you get to the command line type:
sudo Xorg -configurewhich will create a default /etc/X11/xorg.conf file.  Add the lines:
        HorizSync       31.0 - 70.0
        VertRefresh     40.0 - 75.0to the Monitor section then reboot."[/COLOR]  

However when I entered the "sudo Xorg -configure" line my computer spit back saying that "sudo" is not an acceptable command

How can I fix this?   It's very annoying.  

Thanks

---

### Post by mr clark25 on 2010-07-03
i would re-install, simply because you can't use sudo.

if you can't sudo, that will really limit you...



there is a alternative to sudo: su root
if you really dont want to re-install, try running these:
```

su root
Xorg -configure

```

---

### Post by roger_1960 on 2010-07-03
Hi

I think that in recovery mode, you dont need sudo as you are root already?

The right solution is to create an xorg.conf file.  I have had to do this to get a Trident Cyberblade (not your model) to run a resolution higher than 800x600.

You can create the xorg.conf file in a normal session by using > gksu gedit /etc/X11/xorg.conf

This will create an empty file for you to edit.

---

### Post by Spyler25 on 2010-07-03
I tried doing the "gksu gedit/etc.X11/xorg.conf" in the terminal and it would open a tab that said "starting administr..." but then it closes and nothings seems to have happened.  

Should I be doing this at the command line?

---

### Post by realzippy on 2010-07-03
Thread exists and seems to be solved...

[http://ubuntuforums.org/showthread.php?t=1054304](http://ubuntuforums.org/showthread.php?t=1054304)

I would suggest to test that xorg.conf...

---

### Post by Spyler25 on 2010-07-03
the problem seems to be that I don't have a "xorg.conf" file in the etc/x11 folder and can't seem to get one there

---

### Post by realzippy on 2010-07-03
Backup your existing xorg.conf file and try that suggested one:

```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf-backup
```

```
gksudo gedit /etc/X11/xorg.conf
```

Delete everything in the monitor section and paste in:

[I]Section "Monitor"
Identifier "Configured Monitor"
Option "DPMS" "true"
HorizSync 30.0-60.0
VertRefresh 50.0-70.0
EndSection

Section "Screen"
Identifier "Default Screen"
Monitor "Configured Monitor"
Device "Configured Video Device"
DefaultDepth 24
SubSection "Display"
Depth 24
Modes "1024x768" "800x600"
EndSubSection

EndSection

[/I]

Save and close and log out/in to restart X server....


BTW.mind that is X11 and not x11 !!

If it should not be enough to have the monitor section,try :

[I]Section "Monitor"
Identifier "Configured Monitor"
Option "DPMS" "true"
HorizSync 30.0-60.0
VertRefresh 50.0-70.0
EndSection

Section "Screen"
Identifier "Default Screen"
Monitor "Configured Monitor"
Device "Configured Video Device"
DefaultDepth 24
SubSection "Display"
Depth 24
Modes "1024x768" "800x600"
EndSubSection
EndSection

Section "InputDevice"
Identifier "Generic Keyboard"
Driver "kbd"
Option "CoreKeyboard"
Option "XkbRules" "xorg"
Option "XkbModel" "pc105"
Option "XkbLayout" "es"
EndSection

Section "InputDevice"
Identifier "Configured Mouse"
Driver "mouse"
Option "CorePointer"
Option "Device" "/dev/input/mice"
Option "Protocol" "ExplorerPS/2"
Option "ZAxisMapping" "4 5"
Option "Emulate3Buttons" "true"
EndSection

Section "InputDevice"
Identifier "Synaptics Touchpad"
Driver "synaptics"
Option "SendCoreEvents" "true"
Option "Device" "/dev/psaux"
Option "Protocol" "auto-dev"
Option "HorizScrollDelta" "0"
EndSection

Section "Device"
Identifier "Trident Microsystems CyberBlade XPAi1"
Driver "trident"
BusID "PCI:1:0:0"
EndSection



[/I]

---

### Post by Spyler25 on 2010-07-03
THANKS REALZIPPY that last bit worked like a charm.  after I rebooted I just went into "Monitor" and changed it to "1024x768" and PERFECT.  

Thanks to everyone that helped me on this.  You're all great!

---

### Post by realzippy on 2010-07-04
That's fine.Please mark thread as solved (threadtools) then...

---

### Post by malatesta on 2010-09-21
> **realzippy said:**
> Backup your existing xorg.conf file and try that suggested one:

```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf-backup
```

```
gksudo gedit /etc/X11/xorg.conf
```

Delete everything in the monitor section and paste in:

[I]Section "Monitor"
Identifier "Configured Monitor"
Option "DPMS" "true"
HorizSync 30.0-60.0
VertRefresh 50.0-70.0
EndSection

Section "Screen"
Identifier "Default Screen"
Monitor "Configured Monitor"
Device "Configured Video Device"
DefaultDepth 24
SubSection "Display"
Depth 24
Modes "1024x768" "800x600"
EndSubSection

EndSection

[/I]

Save and close and log out/in to restart X server....


BTW.mind that is X11 and not x11 !!




[/I]

:guitar: Works wonderful for me at toshiba satellite pro 6400 laptop with lubuntu 10.04 !!! 
Thank you  very much realzippy and spyler.

xyz@xyz-laptop:~$ xrandr
Screen 0: minimum 320 x 240, current 1024 x 768, maximum 1024 x 768
default connected 1024x768+0+0 0mm x 0mm
   1024x768       70.0*    60.0  
   800x600        60.0     56.0  
   720x450        60.0  
   640x480        60.0  
   680x384        60.0  
   576x432        60.0  
   512x384        70.0     60.0  
   400x300        60.0     56.0  
   320x240        60.0  
xyz@xyz-laptop:~$ lshw -class display
WARNING: you should run this program as super-user.
  *-display UNCLAIMED     
       description: VGA compatible controller
       product: CyberBlade/XP
       vendor: Trident Microsystems
       physical id: 0
       bus info: pci@0000:01:00.0
       version: 63
       width: 32 bits
       clock: 66MHz
       capabilities: bus_master cap_list
       configuration: latency=8

Salud y anarquía!!! 8)

---

### Post by Mark Schnitzer on 2010-11-21
Alas, similar solutions have eluded me...

I really would be very grateful for a resolution to the display problem I have with my Toshiba Tecra M1 with a Trident CyberBlade XP4m32 (rev 91), VGA compatible controller.

With or without any version of xorg.conf, I see only color stripes of varying width.

The output to an external monitor is perfect (with or without xorg.conf).

I hope there is help for me too...

MSS

---

