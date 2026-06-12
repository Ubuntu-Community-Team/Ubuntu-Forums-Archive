---
title: "Problem with wacom/bamboo tablets and Xorg"
date: 2011-01-31
forum: General Help
---

### Post by iu34 on 2011-01-31
A few weeks ago, I was configuring my wacom tablet with the Wacom Control Panel by QB89Dragon, and suddenly xorg crashed. I remember specifically that I was modifying the pressure curve of the pen when it crashed. The screen went black, but the computer stayed on. Since then, every time I start up ubuntu normally, it would show the splash screen, but would then drop me to a black screen. But if I boot up under recovery mode, failsafeX, and generate a new x configuration, and restart X, it will work fine until I restart. 

I've tried looking for an xorg.conf, but since I'm running 10.04, I guess it doesn't use an xorg.conf anymore. I tried uninstalling the program I used to configure it, but no go. I tried generating a new configuration with the tablet unplugged, with the tablet plugged in, even with a different tablet. And, since nothing is ever that simple when I do something wrong, nothing so far has worked.

So does anyone have any ideas how I can go about fixing this, and have ubuntu start up normally again?

---

### Post by Favux on 2011-01-31
Hi iu34,

It would be good to know where the Wacom Control Panel by QB89Dragon stores its configuration settings.

But since you broke X and are using Lucid I'm going to guess it's using the 10-wacom.conf in /usr/lib/X11/xorg.conf.d/.  You could try editing it and seeing if that's right from the command line with:
```
sudo nano /usr/lib/X11/xorg.conf.d/10-wacom.conf
```
For comparison a standard 10-wacom.conf would look something like this:
```
Section "InputClass"
	Identifier "Wacom class"
# WALTOP needs a patched kernel driver, that isn't in mainline lk yet,
# so for now just let it fall through and be picked up by evdev instead.
#	MatchProduct "Wacom|WALTOP|WACOM"
	MatchProduct "Wacom|WACOM"
	MatchDevicePath "/dev/input/event*"
	Driver "wacom"
EndSection

Section "InputClass"
	Identifier "Wacom serial class"
	MatchProduct "Serial Wacom Tablet"
	Driver "wacom"
	Option "ForceDevice" "ISDV4"
EndSection

Section "InputClass"
        Identifier "Wacom serial class identifiers"
        MatchProduct "WACf|FUJ02e5|FUJ02e7"
        Driver "wacom"
EndSection


# N-Trig Duosense Electromagnetic Digitizer
Section "InputClass"
	Identifier "Wacom N-Trig class"
	MatchProduct "HID 1b96:0001|N-Trig Pen"
	MatchDevicePath "/dev/input/event*"
	Driver "wacom"
	Option "Button2" "3"
EndSection
```
And since you have a Bamboo of some sort it is usb and the extra entries would be in the usb snippet:
```
Section "InputClass"
	Identifier "Wacom class"
# WALTOP needs a patched kernel driver, that isn't in mainline lk yet,
# so for now just let it fall through and be picked up by evdev instead.
#	MatchProduct "Wacom|WALTOP|WACOM"
	MatchProduct "Wacom|WACOM"
	MatchDevicePath "/dev/input/event*"
	Driver "wacom"
EndSection
```
Just comment them out (#) if they are there and reboot.

---

### Post by iu34 on 2011-01-31
Thank for the speedy reply! 
Unfortunatly, the command didn't work, so I started looking around in /usr/lib/X11...and apparently, I don't even have a file or folder named xorg.conf.d. But I have to have on somewhere, right? If not, would that explain why I have to generate a new configuration every time I restart the computer?

---

### Post by Favux on 2011-01-31
> I don't even have a file or folder named xorg.conf.d. But I have to have on somewhere, right? If not, would that explain why I have to generate a new configuration every time I restart the computer? 
Wow, that sure could be the problem.  The /usr/lib/X11/xorg.conf.d/ is a non-standard location.  See the Xserver 1.7 for Lucid (10.04) isn't really 1.7.  Debian and Ubuntu backported some of the early 1.8 into their 1.7 so they could get rid of HAL & its .fdi files and get to xorg.conf.d and the .conf files quicker.  Everybody else with Xserver 1.7 is still using HAL.

The standard location for Xserver 1.8 and up is /usr/share/X11/xorg.conf.d/.  And where they tell you to put custom .conf files (so they don't get overwritten with updates) is /etc/X11/xorg.conf.d.

But because the Ubuntu Xserver for Lucid is a non-standard or hybrid 1.7 if Wacom Control Panel tried to save settings to /etc/X11/xorg.conf.d that would definitely break X in Lucid.  You can't use that location in Lucid.  So check and see if you have that directory and files in it.  What are the files?  If it's some wacom.conf you have to remove it and the xorg.conf.d directory too.

---

