---
title: "Rotate display 90 degrees counterclockwise?"
date: 2006-03-21
forum: General Help
---

### Post by msg on 2006-03-21
My Dell LCD monitor rotates 90 degrees clockwise along a pivot to allow easy access to the wires at the bottom. However, I think it would be pretty badass to use my monitor in that position. My question is: Is there a relatively simple* way to rotate my display counterclockwise so that the resolution is 1024px wide and 1280 tall? My video card is an Nvidia so it works perfectly with linux, and my native resolution is 1280x1024.

*By relatively simple I mean editing a few configuration files, changing a couple of settings, but not having to recompile the whole operating system.

Thanks :KS

---

### Post by kaffeine on 2006-03-21
-in xorg.conf
--in Section "InputDevice"
add Option "Rotate" "CCW"

if you are using nv driver it should work...

---

### Post by msg on 2006-03-21
Hrm... There were two "InputDevice" sections... I tried it in both, saved and restarted X each time, but it didnt do anything. I looked at it closer and both InputDevice sections only talk about a Mouse and a Keyboard:

```
Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc104"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ImPS/2"
	Option		"Emulate3Buttons"	"true"
	Option		"ZAxisMapping"		"4 5"
EndSection
```

Do I need to make a new section about a Monitor? Sorry I'm sorta a noob at linux, only had it for a few months.

---

### Post by Ramses de Norre on 2006-03-21
Are you sure it should be in the input device section?
I don't have a Nvidia but I'd guess it should be in the device section of your graphics card..

---

### Post by kaffeine on 2006-03-26
ramses is right - i should've mentioned earlier, it goes into the Device Section. but most important, it works only with the 'nv' driver (open) and not with the 'nvidia' driver (nnedless to say, it only works with nvidia graphic cards). you can use the nv driver instead of nvidia without much difference - here's a snippet of my XF86config (or xorg.conf, whichever applies)

 ```
Section "Device"
	Identifier	"Generic Video Card"
	Driver		"nv"
        Option          "Rotate" "CW"
EndSection
```

and here's an image of my CW-rotated desktop. (duh: for counterclockwise, use CCW.)

[IMG]http://imgfly.com/files/260306_093404/rotated.png[/IMG]

---

### Post by mbeach on 2006-04-13
Kaffeine, do you have any issues with the mouse holding on the 'normal' orientation when you do this?  If so how do you deal with it.  If I try this, and move my mouse up, the pointer goes right.  (display was rotated ccw).

---

### Post by az on 2006-04-13
xrandr -o right

---

### Post by zer on 2006-04-20
IIRC it already worked with the closed nvidia-driver :-O. I still want to use XGL now, but i have no chance to get my screen rotated :(.

What's with the EXA-driver?

---

### Post by zer on 2006-04-20
[QUOTE=kaffeine]but most important, it works only with the 'nv' driver (open) and not with the 'nvidia' driver (nnedless to say, it only works with nvidia graphic cards)[/QUOTE]
Hey, that's wrong, i got it working now, (xrandr -o left isn't working):```

######################### Grafikkarte ###############################
Section "Device"
    Identifier     "NVIDIA Corporation NVIDIA Default Card"
    Driver         "nvidia"
    BusID          "PCI:1:0:0"
    Option         "RenderAccel"                "true"
    Option         "AllowGLXWithComposite"      "true"
    Option         "NvAGP"                      "1"
    Option         "MonitorLayout"              "DFP"
    Option         "NoRenderExtension"          "Off"
    Option          "Rotate" "CCW"
EndSection
```

---

### Post by henriquemaia on 2006-04-23
[QUOTE=zer]Hey, that's wrong, i got it working now, (xrandr -o left isn't working):```

######################### Grafikkarte ###############################
Section "Device"
    Identifier     "NVIDIA Corporation NVIDIA Default Card"
    Driver         "nvidia"
    BusID          "PCI:1:0:0"
    Option         "RenderAccel"                "true"
    Option         "AllowGLXWithComposite"      "true"
    Option         "NvAGP"                      "1"
    Option         "MonitorLayout"              "DFP"
    Option         "NoRenderExtension"          "Off"
    Option          "Rotate" "CCW"
EndSection
```[/QUOTE]


You're using Nvidia driver. For that you have to remove 

**Option          "Rotate" "CCW"** (for nv driver)

and add

**Option 	        "RandRRotation" "on"**

Restart your X. Now xrandr will work ok.

ps:  xrandr is used to set the screen size, orientation  and/or  reflection. (quoted from the man page)

---

### Post by cosmoshell on 2006-04-23
[QUOTE=msg]My Dell LCD monitor rotates 90 degrees clockwise along a pivot to allow easy access to the wires at the bottom. However, I think it would be pretty badass to use my monitor in that position. My question is: Is there a relatively simple* way to rotate my display counterclockwise so that the resolution is 1024px wide and 1280 tall? My video card is an Nvidia so it works perfectly with linux, and my native resolution is 1280x1024.

*By relatively simple I mean editing a few configuration files, changing a couple of settings, but not having to recompile the whole operating system.

Thanks :KS[/QUOTE]

I HAVE best soulution of aLL

rotate display how to
step one grab minitor
step two place hands on monitor
step three push at a downword angle on the top corner or top right part of the display now continue intill your mointer is where you want it. 

truble shooting

if the screen dosent turn like a ball would then it probly doent have enuf room
soulution smash everything around it with a sludge hammer *very inportent* also be warned use the instructions at your own risk......

---

### Post by zer on 2006-04-25
[QUOTE=henriquemaia]You're using Nvidia driver. For that you have to remove 

**Option          "Rotate" "CCW"** (for nv driver)

and add

**Option 	        "RandRRotation" "on"**

Restart your X. Now xrandr will work ok.
[/QUOTE]
That's the problem, this solution does ***not*** work. I don't know why. I am happy that it works :). If i remember some time ago...:-?

---

### Post by baxxx on 2006-08-05
sorry - stupid question, but I'm :mrgreen:

I'm using nv driver, have added Option "Rotate" "CCW" and done xrandr -o right. Everything is OK, rotation works. But the question is - how to get back to the normal LCD orientation? :smile: 
xrandr -o left backs error:
Xlib:  extension "RANDR" missing on display ":0.0".

---

### Post by it.henrik on 2006-08-05
I have a dual monitor setup and want to have the desktop rotaded on one of them. I am using twinview. Please help.

---

### Post by fourcylthrill on 2006-08-24
baxxx, try xrandr -o normal


Any luck for the ATI guys? I'm running a Radeon 9200 with the ATI version 8.28.8 drivers. Thanks for any help!

---

### Post by dragonflyseven on 2006-11-04
Hey, this works! I set up shortcuts for "xrandr -o right" and "xrandr -o normal". Now I can have my laptop near my bed an read while laying down! I am lazy, I know. Anyway, it worked for me. Thanks guys.

---

