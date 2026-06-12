---
title: "Tecra m7 stylus directions after screen rotation"
date: 2010-10-21
forum: General Help
---

### Post by ReguPL on 2010-10-21
Hello Everyone!
I have a slight problem with setting of a stylus in my Tecra m7. It works fine when screen is in default position, but when I rotate the screen to vertical (left/CCW) touchpad and stylus input does not change so when I move it up it it goes right ^^'

xinput goes like this:
```
&#9121; Virtual core pointer                        id=2    [master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer                  id=4    [slave  pointer  (2)]
&#9116;   &#8627; PS/2 Mouse                                  id=10    [slave  pointer  (2)]
&#9116;   &#8627; AlpsPS/2 ALPS GlidePoint                    id=11    [slave  pointer  (2)]
&#9116;   &#8627; Serial Wacom Tablet eraser                  id=12    [slave  pointer  (2)]
&#9116;   &#8627; Serial Wacom Tablet stylus                  id=13    [slave  pointer  (2)]
&#9123; Virtual core keyboard                       id=3    [master keyboard (2)]
    &#8627; Virtual core XTEST keyboard                 id=5    [slave  keyboard (3)]
    &#8627; Power Button                                id=6    [slave  keyboard (3)]
    &#8627; Video Bus                                   id=7    [slave  keyboard (3)]
    &#8627; Power Button                                id=8    [slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard                id=9    [slave  keyboard (3)]
    &#8627; Toshiba input device                        id=14    [slave  keyboard (3)]

```

I already tried few .sh's from this forum archives but it didn't seem to work. I disabled driver for graphic card, because recommended version showed only violet screen when starting system and older version does not support rotation.

I use Ubuntu 10.10 with Gnome. Thank you in advance for any help you can give, cause I spent whole yesterday looking for answers... ](*,)

---

### Post by Favux on 2010-10-21
Hi ReguPL,

Welcome to Ubuntu forums!

> I disabled driver for graphic card, because recommended version showed only violet screen when starting system and older version does not support rotation.
What video chipset do you have?
```
lspci -nn | grep VGA
```
As long as it supports rotation getting your wacom devices to rotate shouldn't be too hard.

---

### Post by ReguPL on 2010-10-21
Hi Favux!

Thanks for welcome. Output goes like this:

```
01:00.0 VGA compatible controller [0300]: nVidia Corporation G72M [Quadro NVS 110M] [10de:01da] (rev a1)

```

---

### Post by Favux on 2010-10-21
OK, so you're saying that Hardware Drivers (Jockey) offers you a proprietary Nvidia driver but it doesn't work with your G72M when you use it?

What does your xorg.conf currently look like?  Do you have one?:
```
gedit /etc/X11/xorg.conf
```

On the [Rotation HOW TO]("http://ubuntuforums.org/showpost.php?p=6274392&postcount=1") method 1 or 3 should work for you once we get video straightened out.

---

### Post by ReguPL on 2010-10-21
Hmm... it looks like I don't have one :)

---

### Post by Favux on 2010-10-21
Alright, then you're on the Open Source Xorg nvidia driver.  I think it handles rotation.

Are you using a script to rotate?  Can I see it?

---

### Post by ReguPL on 2010-10-21
I tried several of them:

```
#!/bin/sh

if [ $1 = 'normal' ]
then
    xrandr -o normal
    xsetwacom set stylus rotate 0
elif [ $1 = 'left' ]
then
    xrandr -o left
    xsetwacom set stylus rotate 2
elif [ $1 = 'right' ]
then
    xrandr -o right
    xsetwacom set stylus rotate 1
elif [ $1 = 'inverted' ]
then
    xrandr -o inverted
    xsetwacom set stylus rotate 3
fi

```with stating direction ekhm... directly ;)
```

if [ -f /tmp/rotated ]; then
        xrandr -o normal
        xsetwacom set "Serial Wacom Tablet eraser" Rotate none
        xsetwacom set "Serial Wacom Tablet stylus" Rotate none
        rm -f /tmp/rotated && exit 0
else
        xrandr -o left
        xsetwacom set "Serial Wacom Tablet stylus" Rotate left
        xsetwacom set "Serial Wacom Tablet eraser" Rotate left
        echo 1 > /tmp/rotated && exit 0
fi
```Also one changed for tecra:
```
#!/bin/sh

#Author: Patrick Coke & Tim Pope

#modified for ToshibaTecraM7

# by Alexandru Romanescu
# Modified again by Justin Emmanuel

while xset q >/dev/null 2>&1; do

sleep 2 # Polling Interval, 2 seconds

lid="`cat /proc/acpi/button/lid/LID/state|awk '{print $2}'`"

# Looks to see if what orientation the screen is in (Normal or Left)

# and puts the orientation into the $orientation variable

orientation="`xrandr --query --verbose | /bin/grep '(normal left inverted rig' | /usr/bin/awk '{print $5}'`"

dpms="`xset q|grep 'Monitor is'|awk '{print $3}'`"

if [ "$orientation" = "normal" -a "$lid" = "closed" ]; then

xrandr -o inverted
xsetwacom set "stylus" Rotate 3
xsetwacom set "cursor" Rotate 3
xsetwacom set "eraser" Rotate 3
orientation="inverted"

elif [ "$orientation" = "inverted" -a "$lid" = "open" ]; then

xrandr -o normal
xsetwacom set "stylus" Rotate NONE
xsetwacom set "cursor" Rotate NONE
xsetwacom set "eraser" Rotate NONE
orientation="normal"

fi
```... and also I just tried method nr 1 from howto that you linked above. Sorry, no luck. I copy it, save as new file .sh, set as executable and run after rotating the screen. Maybe I just do something wrong? :confused:

---

### Post by Favux on 2010-10-21
The script rotates the screen for you.  After making it executablet double click on it an chose Run.  You can place it in a laucher.  And then if you drag the launcher into the top panel it only needs a single click.

You may be using the wrong syntax.  Can you show me your version of the method 1 script?

---

### Post by ReguPL on 2010-10-21
I found half-way to do so:
[https://launchpad.net/magick-rotation/+download](https://launchpad.net/magick-rotation/+download)

it contains a script that rotates all like it should, but goes 90 degrees in one direction, then I have to run it three times more to get to previous state. But at least it works ;)

---

### Post by Favux on 2010-10-21
Hi ReguPL,

That's the xrotate.py script in the Magick Rotation package.  At least it shows we can get rotation working correctly for you using method 1.  Magick Rotation is for HP tablets.  Your swivel hinge switch, if you have one, won't send a signal to hp-wmi, which Magick uses.  Which is why it won't work for you.

---

### Post by ReguPL on 2010-10-21
> **Favux said:**
> The script rotates the screen for you.  After making it executablet double click on it an chose Run.  You can place it in a laucher.  And then if you drag the launcher into the top panel it only needs a single click.

You may be using the wrong syntax.  Can you show me your version of the method 1 script?

Already did the above, thanks. I don;t understand what do you mean with "your version of script" - am I suppose to change it in some way? The syntax looks like this:

```

#!/bin/sh 

# Find the line in "xrandr -q --verbose" output that contains current screen orientation and "strip" out current orientation. 

rotation="$(xrandr -q --verbose | grep 'connected' | egrep -o  '\) (normal|left|inverted|right) \(' | egrep -o '(normal|left|inverted|right)')" 

# Using current screen orientation proceed to rotate screen and input tools. 

case "$rotation" in 
    normal) 
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

---

### Post by Favux on 2010-10-21
Yes.  You have to change the "Device names" (stylus and eraser) in the commands with the ones you get from 'xinput --list'.  Like so:
```
#!/bin/sh 

# Find the line in "xrandr -q --verbose" output that contains current screen orientation and "strip" out current orientation. 

rotation="$(xrandr -q --verbose | grep 'connected' | egrep -o  '\) (normal|left|inverted|right) \(' | egrep -o '(normal|left|inverted|right)')" 

# Using current screen orientation proceed to rotate screen and input tools. 

case "$rotation" in 
    normal) 
#    -rotate to the right 
    xrandr -o right 
    xsetwacom set "Serial Wacom Tablet stylus" rotate CW 
    xsetwacom set "Serial Wacom Tablet eraser" rotate CW  
    ;; 
    right) 
#    -rotate to normal 
    xrandr -o normal 
    xsetwacom set "Serial Wacom Tablet stylus" rotate NONE 
    xsetwacom set "Serial Wacom Tablet eraser" rotate NONE 
    ;; 
esac
```
And of course you remove the touch lines because you don't have touch.

---

### Post by ReguPL on 2010-10-21
No effect, but thanks for your support. It works good enough for me ;)

---

### Post by Favux on 2010-10-21
I'm sorry.  What do you mean?  Do you mean the script in post #12 doesn't work?  It should.  Did you remember to make it executable?

---

### Post by ReguPL on 2010-10-21
> **Favux said:**
> I'm sorry.  What do you mean?  Do you mean the script in post #12 doesn't work?  It should.  Did you remember to make it executable?

It did previously (at least tried), now it's not - no changes done. No idea what's going on, but nevermind that ;)

---

