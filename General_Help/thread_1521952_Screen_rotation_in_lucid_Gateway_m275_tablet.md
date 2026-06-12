---
title: "Screen rotation in lucid? Gateway m275 tablet"
date: 2010-07-01
forum: General Help
---

### Post by jadi929 on 2010-07-01
Recently installed ubuntu on my gateway m275 tablet alongside windows xp tablet. Everything, including the stylus/pen without any poking around. However, I'm having trouble getting the screen orientation to rotate.

If I go to system-preferences-monitors, the only option for rotation is "normal".

Here is my xorg.conf:

```

Section "Device"
    Identifier    "Configured Video Device"
    Driver        "vesa"
EndSection

Section "Monitor"
    Identifier    "Configured Monitor"
EndSection

Section "Screen"
    Identifier    "Default Screen"
    Monitor        "Configured Monitor"
    Device        "Configured Video Device"
EndSection


```

---

### Post by Favux on 2010-07-01
Hi jadi929,

I believe it has a serial Wacom digitizer.  So you need a Wacom rotation script.  See the [Rotation HOW TO]("http://ubuntuforums.org/showpost.php?p=6274392&postcount=1").

---

### Post by jadi929 on 2010-07-01
I've taken a look at the how to, it seems quite complicated. Dont know where to start. So I have to generate a script shell, and run it every time rotation is needed?

---

### Post by Favux on 2010-07-01
Short answer is yes.  But it's not that complicated.  Just skim through it and then go back step by step.  Method 1 should work.

---

### Post by jadi929 on 2010-07-01
Ok so I was able to install xf86-input-wacom and xserver-xorg-xinput-wacom was already installed.

Now about this script. I understand i'm supposed to replace a few terms in the given scripts, with those i get from command "xinput --list", but could u kindly clarify what exactly I need to change in the following script?

```
#!/bin/sh 

# Find the line in "xrandr -q --verbose" output that contains current screen orientation and "strip" out current orientation. 

rotation="$(xrandr -q --verbose | grep 'connected' | egrep -o  '\) (normal|left|inverted|right) \(' | egrep -o '(normal|left|inverted|right)')" 

# Using current screen orientation proceed to rotate screen and input tools. 

case "$rotation" in 
    normal) 
#    -rotate to the left 
    xrandr -o left 
    xsetwacom set stylus rotate CCW 
    xsetwacom set touch rotate CCW 
    xsetwacom set eraser rotate CCW 
    ;; 
    left) 
#    -rotate to inverted 
    xrandr -o inverted 
    xsetwacom set stylus rotate HALF 
    xsetwacom set touch rotate HALF 
    xsetwacom set eraser rotate HALF 
    ;; 
    inverted) 
#    -rotate to the right 
    xrandr -o right 
    xsetwacom set stylus rotate  CW 
    xsetwacom set touch rotate CW 
    xsetwacom set eraser rotate CW  
    ;; 
    right) 
#    -rotate to normal 
    xrandr -o normal 
    xsetwacom set stylus rotate NONE 
    xsetwacom set touch rotate NONE 
    xsetwacom set eraser rotate NONE 
    ;; 
esac
```

Also, what exactly do I do with the script? I'm guessing save it as a file on desktop. But i need help with the script.

---

### Post by Favux on 2010-07-02
Right, save it somewhere in the home directory:  /home/username is fine.

The "Device names"  convention has changed with Lucid.  xinput tells you what stylus, eraser, and pen are called so you can change them in the script's xsetwacom commands.

---

### Post by jadi929 on 2010-07-02
Ok, so its supposed to look something like this correct?

```

case "$rotation" in 
    normal) 
#    -rotate to the left 
    xrandr -o left 
    xsetwacom set Serial Wacom Tablet rotate CCW 
    xsetwacom set touch rotate CCW 
    xsetwacom set Serial Wacom Tablet eraser rotate CCW 
    ;; 

```

I didn't have anything for touch so just left it like that.

---

### Post by jadi929 on 2010-07-02
Ok i got everything, but when i try to run the launcher, it says "there was an error in launching the application" and below that says permission denied

---

### Post by Favux on 2010-07-02
You want to include the quotes and remove touch, since you don't have it:
```
case "$rotation" in 
    normal) 
#    -rotate to the left 
    xrandr -o left 
    xsetwacom set "Serial Wacom Tablet" rotate CCW 
    xsetwacom set "Serial Wacom Tablet eraser" rotate CCW 
    ;;
```
You have to make the script executable.  Either using chmod or right click on it and in Properties go to the Permission tab and click the box Execute as Program.

---

### Post by jadi929 on 2010-07-02
i went back and included the quotes, "execute as program" was already checked.

Another thing, not sure if it has anything to do with this. In terminal, I tried the command "xrandr -o left" and i get this:

X Error of failed request:  BadMatch (invalid parameter attributes)
  Major opcode of failed request:  149 (RANDR)
  Minor opcode of failed request:  2 (RRSetScreenConfig)
  Serial number of failed request:  14
  Current serial number in output stream:  14

---

### Post by Favux on 2010-07-02
What's your video chipset?
```
lspci | grep VGA
```

---

### Post by jadi929 on 2010-07-02
its intel.

```
00:02.0 VGA compatible controller: Intel Corporation 82852/855GM Integrated Graphics Device (rev 02)
```

---

### Post by Favux on 2010-07-02
Ouch, the Intel 855.  Just went through some of that with majedaly at:  [http://ubuntuforums.org/showpost.php?p=9506432&postcount=1081](http://ubuntuforums.org/showpost.php?p=9506432&postcount=1081)  I gave him some links a few posts earlier.

I don't think the Intel, once it's set up correctly, needs:
```
	Option		"RandRRotation"  "on"
```
in the xorg.conf, or something similar, like Nvidia does.

---

### Post by jadi929 on 2010-07-02
Ok so i got rid of the randrotation option in my xorg. Also, in regards to the intel 855, i first, upon installation of lucid got the black screen on start up so i went to recovery to and selected graphics failsafe mode.


After that, everytime on startup i get a weird colored strips on the botttom of the screen for a couple of seconds, then ubuntu starts up fine

---

### Post by Favux on 2010-07-02
It sounds like you might be running the VESA video driver.  I don't think it does rotation.  That's why I directed you to majedaly's solution with uxa and memory.

---

### Post by jadi929 on 2010-07-03
I'm currently trying these workarounds listed here:

[https://wiki.ubuntu.com/X/Bugs/Lucidi8xxFreezes](https://wiki.ubuntu.com/X/Bugs/Lucidi8xxFreezes)

---

### Post by jadi929 on 2010-07-03
update: i just got the graphics working from one the those workarounds. Now atleast I can go into system-prefs-monitors and rotate the screen that way.

Will also try the script when i get time

---

### Post by Favux on 2010-07-03
Sweet!  Nice work.

---

### Post by jadi929 on 2010-07-03
sucess! i got the script to rotate the screen. stylus also seems to work. now i just have to get the bezel button (for rotating) working

strange how i dont have an xorg.conf anymore, i have 2 xorgbackups and an xorg failsafe which says its using the fbdev driver

---

### Post by Favux on 2010-07-03
Outstanding!  Hopefully it will give a signal when you use xev.

---

### Post by jadi929 on 2010-07-03
unfortunately not, when i use xev, and press the rotation button, i get no response. But the brightness key seems to work.


Is it possible that I set up a keyboard shortcut to rotate the screen?

---

### Post by jadi929 on 2010-07-03
nevermind that, i figured out the keyboard shortcuts. I just linked to run the shell script.

So now i have everything running on Ubuntu. And now to get rid of windows!  wowhooo

now is there anyway I can reinstall ubuntu (while also removing windows) and keep this same configuration? So i don't have to go through poking around with the graphics drivers and all. Perhaps some kind of restore CD?

---

### Post by Favux on 2010-07-03
Doing that would probably take more work then making some notes and copying some key files you changed.

---

