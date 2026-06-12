---
title: "trying to write a script for screen rotation with xrandr..."
date: 2011-01-25
forum: General Help
---

### Post by ninjaaron on 2011-01-25
So, I want to write a script that toggles my screen rotation between normal and left, but I don't know what I'm doing. I wrote this:
```
#screen rotation script that toggels between left and normal
if [ $Orientation="normal" ]; then
xrandr -o 1;
Orientation="left"
else
xrandr -o 0;
Orientation="normal"
fi
```

Right now, it just changes the screen orientation to left no matter what.

I really have no idea what I'm doing. Be gentle.

---

### Post by ninjaaron on 2011-01-25
found this script with Google, which apparently worked for the guy who wrote it.
```

#!/bin/sh
rotation=`xrandr -q | grep "Current rotation" | cut -d"-" -f2`
if [ $rotation = "normal" ] ;
then
  xrandr -o left
else
  xrandr -o normal
fi
```

When I run it, I get:
```
[: 8: =: unexpected operator
```

Hmm...

---

### Post by pl@yer on 2011-01-25
You can get rid of the semi-colon after if.
What is the result of this command? 
```

xrandr -q | grep "Current rotation" | cut -d"-" -f2

```
and
```

xrandr -q | grep "Current rotation"

```

---

### Post by ninjaaron on 2011-01-25
> **pl@yer said:**
> You can get rid of the semi-colon after if.
What is the result of this command? 
```

xrandr -q | grep "Current rotation" | cut -d"-" -f2

```
and
```

xrandr -q | grep "Current rotation"

```
The output was nothing and nothing (new prompt for both without even an error message)

As you might expect, after taking out the semicolon, the script did: ...

That's right, nothing.

*edit:*
I ran "xrandr -q" by itself, and I got this:
```
Screen 0: minimum 320 x 200, current 1366 x 768, maximum 4096 x 4096
VGA1 disconnected (normal left inverted right x axis y axis)
LVDS1 connected 1366x768+0+0 (normal left inverted right x axis y axis) 223mm x 125mm
   1366x768       60.0*+
   1360x768       59.8     60.0  
   1024x768       60.0  
   800x600        60.3     56.2  
   640x480        59.9  
```
If I change the orientation to 'left', then the x and y resolution values switch, but that seems to be the only change.

on the other hand, if I run 'xrandr -q --verbose', I get a lot more (This isn't all of it, just the section that seemed most relevant):
```
LVDS1 connected 1366x768+0+0 (0x43) normal (normal left inverted right x axis y axis) 223mm x 125mm
	Identifier: 0x42
	Timestamp:  10982190
	Subpixel:   horizontal rgb
	Gamma:      1.0:1.0:1.0
	Brightness: 1.0
	Clones:    
	CRTC:       1
	CRTCs:      1
	Transform:  1.000000 0.000000 0.000000
	            0.000000 1.000000 0.000000
	            0.000000 0.000000 1.000000
	           filter: 
	EDID:
		00ffffffffffff0030e4bb0200000000
		0014010490160d780a296599574f9927
		1e505400000001010101010101010101
		010101010101bc1b5684500016303020
		3500df7d0000001bbc1b56d35100c830
		30203500df7d0000001b000000fe0034
		3659334d803130315748310a00000000
		00004133940100000001010a2020007e
	BACKLIGHT: 15 (0x0000000f)	range:  (0,15)
	Backlight: 15 (0x0000000f)	range:  (0,15)
	scaling mode:	Full aspect

```

---

### Post by ninjaaron on 2011-01-25
Found another pair of more recent scripts that does another kind of rotation that I don't want, but I don't really know how to modify it for my needs. It doesn't seem to work because there is no file at "~/.screen-orientation".
> This is a fix that allows for persistent configuration of tho monitor&#8217;s pivot rotation. You most create two scripts:

screen-rotate

sudo gedit screen-rotate

add following lines save and exit

```
#!/bin/bash
if [ "$1" = "right" ]
then
rotate=&#8221;right&#8221;
else
rotate=&#8221;left&#8221;
fi

if xrandr | grep &#8220;$rotate (&#8220;

then
rotate=&#8221;normal&#8221;
fi
xrandr -o &#8220;$rotate&#8221;

echo $rotate > ~/.screen-orientation
```

screen-rotate-setup

sudo gedit screen-rotate-setup

add following lines save and exit
```
#!/bin/bash
rotate=`cat ~/.screen-orientation`
xrandr -o $rotate
```

save both scripts to /usr/bin and give them execution permissions to everyone (chmod +x)

---

### Post by pl@yer on 2011-01-25
The reason for the error, is that you are testing if $rotation variable contains string "normal". Since it contains nothing the test fails.
```

[ $rotation = "normal" ]

```

---

### Post by ninjaaron on 2011-01-25
> **pl@yer said:**
> The reason for the error, is that you are testing if $rotation variable contains string "normal". Since it contains nothing the test fails.
```

[ $rotation = "normal" ]

```

makes sense, but I still have no idea what to do :P

---

### Post by pl@yer on 2011-01-25
I tried everything in this thread and could not get the screen to rotate using xrandr. 

[http://ubuntu-virginia.ubuntuforums.org/showthread.php?t=682821](http://ubuntu-virginia.ubuntuforums.org/showthread.php?t=682821)

---

### Post by ninjaaron on 2011-01-25
I can get xrandr rotating the screen, no problem. This is the command:
```
$ xrandr -o [normal, inverted, left, right, 0, 1, 2, 3]
```

I actually have the rotation controlled with no problem using two buttons... but want to do it with just one :)

---

### Post by pl@yer on 2011-01-25
If you see "normal" when you run this command.
```

xrandr -q --verbose|grep LVDS1|cut -b37-43

```

then you could use this as the script.
```

#!/bin/sh
rotation=`xrandr -q --verbose|grep LVDS1|cut -b37-43`
if [ $rotation = "normal" ] ;
then
  xrandr -o left
else
  xrandr -o normal
fi


```

If you are not getting exactly "normal" from that command try changing the cut start and stop bytes (37 43). So that you are just getting what you want. You could also use -d delimeter...like this 

```

#!/bin/sh
rotation=`xrandr -q --verbose|grep LVDS1|cut -d ' ' -f5`
if [ $rotation = "normal" ] ;
then
  xrandr -o left
else
  xrandr -o normal
fi

```

---

### Post by ninjaaron on 2011-01-26
> **pl@yer said:**
> If you see "normal" when you run this command.
```

xrandr -q --verbose|grep LVDS1|cut -b37-43

```

then you could use this as the script.
```

#!/bin/sh
rotation=`xrandr -q --verbose|grep LVDS1|cut -b37-43`
if [ $rotation = "normal" ] ;
then
  xrandr -o left
else
  xrandr -o normal
fi


```

If you are not getting exactly "normal" from that command try changing the cut start and stop bytes (37 43). So that you are just getting what you want. You could also use -d delimeter...like this 

```

#!/bin/sh
rotation=`xrandr -q --verbose|grep LVDS1|cut -d ' ' -f5`
if [ $rotation = "normal" ] ;
then
  xrandr -o left
else
  xrandr -o normal
fi

```

The first script worked like a charm! Thanks so much!
*Edit:*
They're eating your script up in the [Dell duo setup thread]("http://ubuntuforums.org/showthread.php?t=1658635&page=20"). Strong work.

---

