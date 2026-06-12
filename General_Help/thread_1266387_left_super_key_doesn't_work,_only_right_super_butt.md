---
title: "left super key doesn't work, only right super button works"
date: 2009-09-14
forum: General Help
---

### Post by jzacsh on 2009-09-14
Hello,

This is really weird and only started today, when I got home from work:

my "super key" on the left side of my keyboard isn't doing anything, but my "super key" on the right side of my keyboard is still reacting.
_eg._
*super+space*  :  **gnome-do**
*super+e * :  **expose**
*super+left-click*  :  **rotate cube**

as you can see ^ its not only compiz stuff, so i figured I'd post it here in general support. I tried rrebooting just now, and it didn't do anything. I feel like its got to be a simple fix (maybe I turned off the left-super? how does one do that??)

**thanks for *any* help** - this is annoying, as I'm realizing I only ever use the left-super . I did try a bunch of searches, but didn't find anything.
--
*oh, i'm running Jaunty Jackalope with the latest updates.*

---

### Post by NoaHall on 2009-09-14
Try running "sudo dpkg-reconfigure -phigh xserver-xorg"

---

### Post by jzacsh on 2009-09-14
> **NoaHall said:**
> Try running "sudo dpkg-reconfigure -phigh xserver-xorg"

NoaHall, thanks for the speedy reply! I thought xserver-xorg has to do with the GUI, x windowing system... no? sorry if I'm asking too much in a forum, I got locked out of a machine recently by fiddling with an xorg package of some kind.

---

### Post by NoaHall on 2009-09-14
And what is the GUI made of ? Icons, being able to click on things, and seeing a mouse move :)

don't worry, it's pretty safe - there's probably a backup there anyway, but you could do this before if you want -

sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.backup

---

### Post by jzacsh on 2009-09-14
> **NoaHall said:**
> And what is the GUI made of ? Icons, being able to click on things, and seeing a mouse move :)

don't worry, it's pretty safe - there's probably a backup there anyway, but you could do this before if you want -

sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.backup

yeah, i did a backup on the last machine - but it won't even get past grub (another story, i might start a diff. post about). anywho, you have a *speedy* response, thanks again. I'm sure its safe, but before I run it - how come my keyboards configuration comes into the picture of my graphical interface? again, sorry - but i just spent all day setting up this machine yesterday and would hate to make the same mistake I seem to have made at work.

---

### Post by NoaHall on 2009-09-14
Look, here's mine - 
```

Section "InputDevice"

    # generated from default
    Identifier     "Keyboard0"
    Driver         "keyboard"
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
```

Use cat /etc/X11/xorg.conf | grep -i Keyboard  if you want to see yours.

Well, it is. It's in charge of the input devices, and the output devices (well, three of them :D)

---

### Post by P4man on 2009-09-14
Not saying that NoaHall's advice is bad (or dangerous) but you can open a terminal and type "xev"

Then you get a little window that shows all keycodes and mouse clicks. Press the super key and see if you get a response. For the left super key, it should be "Super_L"

To answer your question what it has to with the gui.. everything :) The X server that runs your window manager also takes care of mouse and keyboard input. So NoaHall is quite right the problem could be there, resetting to a default xorg.conf eliminates already some possible problems.

---

### Post by jzacsh on 2009-09-14
> **NoaHall said:**
> 
[...]
Use cat /etc/X11/xorg.conf | grep -i Keyboard  if you want to see yours.

Well, it is. It's in charge of the input devices, and the output devices (well, three of them :D)


that's odd, mine doesn't bring up anything when grep for "keyboard". cat of the whole file shows:
**cat /etc/X11/xorg.conf**
*comments ommited*
```
Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
	DefaultDepth	24
	Option	"AddARGBGLXVisuals"	"True"
EndSection

Section "Module"
	Load	"glx"
EndSection

Section "Device"
	Identifier	"Configured Video Device"
	Driver	"nvidia"
	Option	"NoLogo"	"True"
EndSection

```

> **P4man said:**
> Not saying that NoaHall's advice is bad (or dangerous) but you can open a terminal and type "xev"

Then you get a little window that shows all keycodes and mouse clicks. Press the super key and see if you get a response. For the left super key, it should be "Super_L"

To answer your question what it has to with the gui.. everything :) The X server that runs your window manager also takes care of mouse and keyboard input. So NoaHall is quite right the problem could be there, resetting to a default xorg.conf eliminates already some possible problems.

thanks :) I tried xev - very cool! - it showed some very different output between the two supers:

the left side:
```
FocusOut event, serial 35, synthetic NO, window 0x3c00001,
    mode NotifyGrab, detail NotifyAncestor

FocusIn event, serial 35, synthetic NO, window 0x3c00001,
    mode NotifyUngrab, detail NotifyAncestor

KeymapNotify event, serial 35, synthetic NO, window 0x0,
    keys:  2   0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   
           0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   

```

the right side:
```
KeyPress event, serial 35, synthetic NO, window 0x3c00001,
    root 0xc3, subw 0x0, time 3211032, (198,-127), root:(205,739),
    state 0x10, keycode 134 (keysym 0xffec, Super_R), same_screen YES,
    XLookupString gives 0 bytes: 
    XmbLookupString gives 0 bytes: 
    XFilterEvent returns: False

KeyRelease event, serial 35, synthetic NO, window 0x3c00001,
    root 0xc3, subw 0x0, time 3211117, (198,-127), root:(205,739),
    state 0x50, keycode 134 (keysym 0xffec, Super_R), same_screen YES,
    XLookupString gives 0 bytes: 
    XFilterEvent returns: False

```

left side is a lot less eventful, isn't it? and no mention of "Super_L". 

hmmmf... anyways, i'm going to try what NoaHall said in a little bit...

```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.backup
dpkg-reconfigure -phigh xserver-xorg
```

---

### Post by drs305 on 2009-09-14
You can also see the current keycodes with this:
```

xmodmap -pke | grep Super_L

```
If you want to see them all, leave off " | grep Super_L"

On my machine, Super_L is keycode 133.

If it isn't listed or you don't have a listing for 133, you could try adding it with the following. This assigns the key for the current session. Of course, you could assign another keycode as well - just know what key the keycode represented initially.
```

xmodmap -e "keycode 133 = Super_L"

```

---

### Post by jzacsh on 2009-09-14
> **drs305 said:**
> You can also see the current keycodes with this:
```

xmodmap -pke | grep Super_L

```
If you want to see them all, leave off " | grep Super_L"

On my machine, Super_L is keycode 133.

If it isn't listed or you don't have a listing for 133, you could try adding it with the following. This assigns the key for the current session. Of course, you could assign another keycode as well - just know what key the keycode represented initially.
```

xmodmap -e "keycode 133 = Super_L"

```

holy cow, i'm glad I posted about this - these tools are awesome! this is some really cool stuff.
I grep'd for Super_L and got this:
```
$ **xmodmap -pke | grep Super_L**
keycode 133 = Super_L NoSymbol Super_L NoSymbol Super_L
keycode 206 = NoSymbol Super_L NoSymbol Super_L NoSymbol Super_L

```
hmm... i suppose "NoSymbol" probably has something to do with it? :)
your suggestion of **xmodmap -e "keycode 133 = Super_L"** - but should I do something differently since I have **two** keycodes showing up with Super_L?

actually looking at the **Super_R**'s entry, maybe somethings wrong with Super_R too? (though, it seems to be working fine)...
```
keycode 134 = Super_R NoSymbol Super_R NoSymbol Super_R
```

---

### Post by jzacsh on 2009-09-15
```
xmodmap -e "keycode 133 = Super_L"
```
did the job perfectly. I don't know what the "NoSymbol" stuff is in the key 134 for Super_R, but I'll just reset that too in the same manner, if I have any problems.

I learned alot, thanks everyone :)

---

### Post by drs305 on 2009-09-15
> **jzacsh said:**
> ```
xmodmap -e "keycode 133 = Super_L"
```
did the job perfectly. 

The change is not persistent. So you don't have to worry about it each boot, make an entry with the command in System, Preferences, Startup Applications:

---

### Post by jzacsh on 2009-09-15
> **drs305 said:**
> The change is not persistent. So you don't have to worry about it each boot, make an entry with the command in System, Preferences, Startup Applications:
after realizing just that it wasn't persistent last night, and not wanting to make it a start up (*because i feel like that must be just a work around, not a proper solution*), I tried ```
sudo dpkg-reconfigure -phigh xserver-xorg
``` but it didn't make a difference. than I thought, maybe its a config setting that's messed up with Compiz? or gnome-do? so i uninstalled gnome-do... and at least the compiz-settings-manager (though, i think that's *strictly* a manager, and was a useless move).
_after a reinstall of both, i'm still having quirky behavior:_
[LIST]
[*]sometimes the left button works, than i try it again a second later and it doesn't work.
[*]also, the only times it **will work** is when its for gnome-do. compiz is **only** responding to the right super
[/LIST]

you might just say, give up and put the keycode into startup, but i'm getting this quirky behavior even after i reset the keycode.

:| any more ideas, anyone?

---

### Post by sad1sm0 on 2009-11-21
First, this thread is marked as solved, but unless I'm missing something, that doesn't seem to be the case.  I'm having the same problems on my computer running karmic and can't seem to find a solution.  I tried everything above, but nothing seemed to change.  So I saved the output of xmodmap to a file like so
```

  xmodmap -pke > keyboard.map

```

Upon inspection, I realized that their are two keys with Super_L assigned by default.  Key 133 and Key 206.  I rewrote the file to look like this:

```

keycode 133 = Super_L NoSymbol Super_L NoSymbol Super_L
keycode 206 = 

```

I'm assuming here, but it seems like the NoSymbol portion is normal and probably has to do with how the key should respond in different situations.  

Then I fed the file back to xmodmap like so

```

xmodmap - < keyboard.map

```

The changes were reflected when I viewed the new configuration, but Super_L was no more responsive than before.  Then I went into compiz and set some new key combinations using the left super and the ones I changed worked with both the left and right supers while the ones that I left alone still didn't work with the left key.  I then tried to make 133 = Super_R since it seems like super r works all the time.  This didn't fix anything either.  I had this problem with a different keyboard and on 9.04 as well prior to installing 9.10, but like the guy above it just showed up one day and hasn't gone away, and like him, I only ever use the left super key.

As a final note, I'm using Restricted Drivers from NVIDIA and when it installed it rewrote my xorg.conf file.  I don't know if that's when things got hairy or not, but it could play a role I suppose.

Edit: Just now, after changing the Super_L to Super_R immediately after x server was restarted has given me access to the left super key.

---

