---
title: "Need urgent help"
date: 2010-08-12
forum: General Help
---

### Post by Nightwalker993 on 2010-08-12
Well I was messing with xorg.conf trying to get my wacom tablet to work. I restarted and it brings be everytime to a terminal. I can log in but that is about it. When I type startx it says xorg.conf is messed up bad. I already tried:
sudo dpkg-reconfigure -phigh xserver-xorg
sudo dpkg-reconfigure xserver-xorg
now half the time it hang on spalsh screen... I am running 10.04
In  /usr/lib/X11/xorg.conf.d/10-wacom.conf  this is what I did 
Section "InputClass"
        Identifier "Wacom class"
        MatchProduct "Wacom|WACOM"
        MatchDevicePath "/dev/input/event*"
        Driver "wacom"
        #Option "Button2" "2"
        #Option "Button3" "3"
        Option "KeepShape" "on"
EndSection

Section "InputClass"
        Identifier "Wacom serial class"
        MatchProduct "Serial Wacom Tablet"
        Driver "wacom"
        Option "ForceDevice" "ISDV4"
EndSection

# N-Trig Duosense Electromagnetic Digitizer
Section "InputClass"
        Identifier "Wacom N-Trig class"
        MatchProduct "HID 1b96:0001"
        MatchDevicePath "/dev/input/event*"
        Driver "wacom"
EndSection\
along with adding some other options.
Thanks for the help.

---

### Post by Wisp558 on 2010-08-12
Try removing xorg.conf.
Half the time X can run without one. Just make sure you move it to say xorg.conf.bak, rather than deleting it.

You can also try X -configure.
If I recall correctly.

---

### Post by Nightwalker993 on 2010-08-13
what are the exact commands? anything else? I still get the black terminal on start up.

---

### Post by Noz3001 on 2010-08-13
Disregard. 

```
sudo Xorg -configure
```

---

### Post by Nightwalker993 on 2010-08-13
okay now I am just freezing on the purple splash screen... the orange bar is not moving.
Edit: I back to terminal run what you said. 
Parse error on line 9 of section InputClass in file /usr/lib/X11/xorg.conf.d/10-wacom.conf
(EE) problem parsing the config file
ddxSigGiveUp: closing log
Edit: says the same thing when I startx

---

### Post by Nightwalker993 on 2010-08-13
bump... really need help on this

---

### Post by ASchweitzer on 2010-08-13
well, it's hanging up on

"Parse error on line 9 of section InputClass in file /usr/lib/X11/xorg.conf.d/10-wacom.conf"

Try moving 10-wacom.conf out of that folder. Hold on to it in case that's not the problem though.

---

### Post by Favux on 2010-08-13
Hi Nightwalker993,

Not clear where you're hanging.  It looks like you have a usb tablet pc.  It seems like it might be:
```
Option "ForceDevice" "ISDV4"
```
That got deprecated by about xf86-input-wacom 0.10.7.  But if you have the default Lucid 0.10.5 or don't have a serial tablet not clear why it would hang.  Try commenting it out anyway.

What other options did you add?

---

### Post by Nightwalker993 on 2010-08-13
now I am hanging on the boot screen. Purple background orange bar. Nothing works. Any way I can retrieve my data and start over? its a standard compaq laptop not a tablet.

---

### Post by Favux on 2010-08-13
Fine, usb tablet.  Leave it unplugged.

You can hang with a .conf file in xorg.conf.d as easily as xorg.conf.  I'm still not sure you've shown us the whole 10-wacom.conf (because you mentioned other options), which is where you are apparently hanging.

Usually you see this kind of hang due to a video driver problem in xorg.conf.

---

### Post by linux18 on 2010-08-13
sudo mv /etc/X11/xorg.conf.failsafe /etc/X11/xorg.conf

---

### Post by Nightwalker993 on 2010-08-13
well how do I fix it?

---

### Post by Favux on 2010-08-13
```
sudo mv /etc/X11/xorg.conf.failsafe /etc/X11/xorg.conf
```
That's the original back up and should work if it's the video drivers.

Example would be Nvidia where you installed the proprietary drivers and then messed up the xorg.conf.
```
lspci | grep VGA
```
Or if you have a backup of the working xorg.conf you were using.  Always a good idea.

---

### Post by Nightwalker993 on 2010-08-13
Did not work. However problem is solved. I managed to go in through pico and edit the file.Startx then work but no background so I deleted /usr/lib/X11/xorg.conf.d/10-wacom.conf and everything is fine now. Thanks guys.

---

### Post by Favux on 2010-08-13
Good work!  Still curious about what you had in the 10-wacom.conf though.  Oh well.

---

### Post by Nightwalker993 on 2010-08-14
I had put some command options from man wacom in there.
I think it was number 9 that did it.

---

