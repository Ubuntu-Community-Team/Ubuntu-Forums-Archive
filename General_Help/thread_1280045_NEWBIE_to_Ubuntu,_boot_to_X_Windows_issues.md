---
title: "NEWBIE to Ubuntu, boot to X Windows issues"
date: 2009-10-01
forum: General Help
---

### Post by minigts on 2009-10-01
I mean, I don't even know if it's still called X Windows or not.  Everything was working fine until I decided to see if my computer running Ubuntu 9.04 would support SLI.  I searched a few places and found a string to run in the console, so I run it.  Now my computer will not boot to a GUI and I can't seem to figure out how to either configure it to boot to a GUI or get the "windows" to load.  Every time I try to get it to load, I get an error about it not being to find the monitor or something to that effect.  Below is the xorg.conf file.

> Section "Device"
	Identifier	"Configured Video Device"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
EndSection

Currently I'm booted onto the CD, but I have no idea how to fix the conf file. I removed all versions of it thinking it would create a default similar to the one used when I first got the machine up and running.  I think there is supposed to be more to this file, but I can't find ANY files that resemble the older config files I've modified before, like identifying the mouse, resolution, etc.

Any suggestions?  Can I copy the xorg.conf file from the CD and put it in the etc/X11/ folder?

I'm not too established on the machine, so reinstalling is an option, but I'd like to learn how this works, so any help would be appreciated.

Cheers!

---

### Post by scragar on 2009-10-01
Can you find the command you ran in:
```
/home/**username**/.bash_history
```
And paste it here?

---

### Post by minigts on 2009-10-01
> **scragar said:**
> Can you find the command you ran in:
```
/home/**username**/.bash_history
```
And paste it here?

As I'm running from the CD, I am not sure how to unlock or access the files that are on the HDD.  I can view them and get to them, but any attempt to access them results in the system telling me I don't have access to open the file.  I have tried the sudo -s command to gain root access, but I'm not sure how to adjust permissions in the GUI. :$  Pathetic I know, but I can SEE the file. :D

---

### Post by scragar on 2009-10-01
```
sudo gedit **/mount/point/**home/**username**/.bash_history
```

---

### Post by pythonscript on 2009-10-01
Something we all need to watch and not recommend!

```
sudo gedit /mount/point/home/username/.bash_history
```Don't use this!

*It should be*:

```
*gksudo *gedit /mount/point/home/username/.bash_history
```

---

### Post by minigts on 2009-10-01
> **pythonscript said:**
> 
```
sudo gedit /mount/point/home/username/.bash_history
```

```
*gksudo *gedit /mount/point/home/username/.bash_history
```

Here is what I have. I was able to do it, yay.  I'm posting everything, but the first entry is what I added.  I didn't think it would keep me from getting into the GUI part of the OS.  The rest of the entries are where I tried to get something going on it! :p

> sudo nvidia-xconfig --sli=auto
exit
startx
start
start x
exit
ls
startx 
ls
cd ..
ls
cd ..
ls
cd boot/
ls
cd grub/
ls
vi stage1
ls
vi menu.lst
ls
cd ..
ls
cd ..
ls
cd home/
ls
cd ..
cd root/
ls
cd ..
ls
cd selinux/
ls
cd ..
cd dev/
ls
cd ..
ls
cd etc/
ls
ls -p
ls -s
ls
find *.conf
man conf
ls
vi fstab 
ls
clear
cd ..
ls
cd boot/
ls
vi config-2.6.28-15
ls
vi config-2.6.28-11
ls
clear
ls
vi vmlinuz-2.6.28-15
ls
vi vmlinuz-2.6.28-15-generic 
ls
vi config-2.6.28-15-generic 
ls
vi initrd.img-2.6.28-15-generic 
ls
vi initrd.img-2.6.28-11-generic 
ls
vi vmlinuz-2.6.28-11-generic 
ls
vi vmcoreinfo-2.6.28-11-generic 
ls
vi abi-2.6.28-11-generic
ls
cd grub/
ls
vi default 
ls
vi installed-version 
ls
vi e2fs_stage1_5 
clear
ls
vi menu.lst~
ls
vi menu.lst
ls
vi xfs_stage1_5 
ls
vi default 
ls
clear
ls
vi jfs_stage1_5 
ls
vi device.map 
ls
vi reiserfs_stage1_5 
ls
vi stage2
ls
cd ..
ls
vi abi-2.6.28-1
vi abi-2.6.28-15-generic 
reboot
sudo -s
ls
cd ..
ls
cd etc/
ls
cd X11/
ls
vi xorg.conf
ls
cd xinit/
ls
ls xin
vi xinitrc 
cd ..
ls
vi Xsession
ls
vi Xsession.options 
ls
cd Xsession.d/
ls
vi 50x11-common_determine-startup 
Xsession
start Xsession
startx
cd ..
ls
cd var/
cd log/
vi Xorg.0.log
cd ../etc/X11
cd /etc/X11/
vi xorg.conf
ls
remove-xorg.conf
rm xorg.conf
rm xorg.conf.20091001150057 
rm xorg.conf.20091001150126 
rm xorg.conf.backup 
rm xorg.conf.failsafe 
ls
vi Xwrapper.config
ls
vi XvMCConfig 
ls
clear
ls
vi default-display-manager 
ls
./Xsession
cd Xsession.d/
ls
vi 99x11-common_start
reboot 
restart
reboot 
sudo -s
cd /etc/X11/
ls
vi xorg.conf
reboot 
startx
sudo -s

---

### Post by scragar on 2009-10-01
```
nvidia-xconfig --sli=Auto
```
Try it again with a capital A, if that fails try each of these till one works:
```
nvidia-xconfig --sli=AFR
nvidia-xconfig --sli=SFR
nvidia-xconfig --sli=SLIAA
nvidia-xconfig --sli=off
```

---

### Post by minigts on 2009-10-01
> **scragar said:**
> ```
nvidia-xconfig --sli=Auto
```
Try it again with a capital A, if that fails try each of these till one works:
```
nvidia-xconfig --sli=AFR
nvidia-xconfig --sli=SFR
nvidia-xconfig --sli=SLIAA
nvidia-xconfig --sli=off
```

Well I tried that and it didn't do anything.  Should my conf file above have more information or is Ubuntu different in some way?

---

### Post by minigts on 2009-10-01
Ok, well I made the change, rebooted and still nothing.  However, I looked to see if I could find a conf file that looks like what I normally have and viewed the xorg.conf file and this is what I have now for the etc/X11/xorg.conf file.

> # nvidia-xconfig: X configuration file generated by nvidia-xconfig
# nvidia-xconfig:  version 1.0  (buildmeister@builder62)  Tue Mar 24 06:15:32 PST 2009

Section "ServerLayout"
    Identifier     "Layout0"
    Screen      0  "Screen0"
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
EndSection

Section "Files"
EndSection

Section "Module"
    Load           "dbe"
    Load           "extmod"
    Load           "type1"
    Load           "freetype"
    Load           "glx"
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
    Option         "SLI" "Auto"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection


---

### Post by minigts on 2009-10-01
I have another question.  Are there some files I can remove that will allow the OS to load some default drivers or config files?  I mean, can I remove the nvidia drivers through the command line?  I keep getting an error about not being able to find the monitor.  Sorry, just trying to get this working and I don't know the best way to trouble shoot this issue.  Been on Windows for so long. :$

---

### Post by scragar on 2009-10-02
vesa is a generic driver that should work, although quality varies.

If none of those worked you can try letting Xorg get reconfigured, should restore a few defaults.
```
sudo dpkg-reconfigure xserver-xorg 
```

---

