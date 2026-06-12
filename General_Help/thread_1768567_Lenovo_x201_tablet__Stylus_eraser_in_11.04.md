---
title: "Lenovo x201 tablet : Stylus eraser in 11.04"
date: 2011-05-27
forum: General Help
---

### Post by psychetician on 2011-05-27
Heya folks,

I'm sure I'm missing something obvious, but I can't get my stylus eraser to work, and I haven't been able to find something on the forums yet that lead me to the solution.

I *have* found, however, some cool ways of getting information that might help us getting my eraser working.

For instance,

```
:~$ xsetwacom list
Serial Wacom Tablet stylus      	id: 13	type: STYLUS    
Serial Wacom Tablet eraser      	id: 14	type: ERASER 
```

They also tried looking at what buttons do what :
```
:~$ xsetwacom get "Serial Wacom Tablet eraser" Button2
Parameter 'Button2' is no longer in use. It was replaced with 'Button'.
```

Going further down this rabbit hole : 
```
:~$ xsetwacom get "Serial Wacom Tablet eraser" Button
'Button' requires exactly 1 value(s).
```

These are things that other people looked at when fixing their erasers.  They also looked at some config file : 

```
:~$ gksudo gedit /usr/share/X11/xorg.conf.d/50-wacom.conf
```

Which I did too, to find something like : 

```
Section "InputClass"
	Identifier "Wacom class"
# WALTOP needs a patched kernel driver, that isn't in mainline lk yet,
# so for now just let it fall through and be picked up by evdev instead.
#	MatchProduct "Wacom|WALTOP|WACOM"
	MatchProduct "Wacom|WACOM|Hanwang"
	MatchDevicePath "/dev/input/event*"
	Driver "wacom"
EndSection

Section "InputClass"
	Identifier "Wacom serial class"
	MatchProduct "Serial Wacom Tablet"
	Driver "wacom"
EndSection

Section "InputClass"
        Identifier "Wacom serial class identifiers"
        MatchProduct "WACf|FUJ02e5|FUJ02e7|FUJ02e9"
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


I've tried monkeying around by putting in the line 
```
Option "Button3" "2"
```

in various places and restarting (like other people did), but to no avail.

How did others get their eraser working on natty on their Lenovo x201 tablet?

If you know the answer to that question, can you also tell me how to get the side button working?

Thanks!

---

### Post by Favux on 2011-05-27
Hi psychetician,

The xsetwacom button Parameter has change, you now need to add a space before the number.  So Button1 becomes Button 1.

By default the eraser would be set *Button 1 1*.  And you don't want to change that.

The eraser only works in programs that support it like Gimp, Inkscape, and Xournal.  You need to configure them so they recognize the eraser.  Gimp and Inkscape require you setting the extended input device for the eraser.  See the screen shots near the bottom of the [Wacom wiki]("https://help.ubuntu.com/community/Wacom").

---

### Post by psychetician on 2011-06-02
Brilliant!  I was being silly, and you're right, I just had to change some settings in the programs I was using.  Tho the eraser doesn't work yet in cell writer.  But that's something I can deal with.

---

