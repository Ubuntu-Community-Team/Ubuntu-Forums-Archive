---
title: "Dynamic MultiMontior Help"
date: 2012-04-05
forum: General Help
---

### Post by b9red on 2012-04-05
Hi,

I'm running Ubuntu 11.10 on my laptop with the standard setup that comes out of the box (I actually like unity haha) and its on a laptop which has a docking station which hooks up to two 1600x900 monitors (DP-1 & DP-2). The only problem I'm facing right now is that I can't seem to get my multimonitors to be dynamic like in windows where if I drop my laptop into the dock it will switch to the two monitors and if I remove it, it goes right back to my laptop screen. I'm not sure if there is a tool, or some sort of script I can write or someone can help me write that can do this but some help would be greatly appreciated. Whenever I change to the two monitors through the gnome display tool I just lose all my screens and have to restart my laptop. Its a Dell Latitude E6410 which does not support 3 monitors at once so it has to turn off my laptop screen (eDP-1) before switching to my two monitors. I'd greatly appreciate some assistance and thank you to anyone who tries to help.

---

### Post by josephmills on 2012-04-05
Hello there and welcome to Ubuntu Forums 
I also like unity :) 

there is a tool under system settings --> display's 

but could we take a look at you vga card ? 
open your terminal (ctrl+alt+t)and enter
```
lspci -nn | grep VGA 
``` 
then paste it here thanks

---

### Post by b9red on 2012-04-05
> **josephmills said:**
> Hello there and welcome to Ubuntu Forums 
I also like unity :) 

there is a tool under system settings --> display's 

but could we take a look at you vga card ? 
open your terminal (ctrl+alt+t)and enter
```
lspci -nn | grep VGA 
```then paste it here thanks

```
01:00.0 VGA compatible controller [0300]: nVidia Corporation GT218 [NVS 3100M] [10de:0a6c] (rev a2)
```I believe I'm using the nouveau drivers.

and if it helps 
```
eDP-1 connected 1440x900+0+0 (normal left inverted right x axis y axis) 304mm x 190mm
   1440x900       60.0*+   40.0  
   1152x864       60.0  
   1024x768       59.9  
   800x600        59.9  
VGA-1 disconnected (normal left inverted right x axis y axis)
DP-1 connected (normal left inverted right x axis y axis)
   1600x900       60.0 +
   1280x800       59.8  
   1152x864       75.0  
   1280x720       60.0  
   1024x768       75.1     70.1     60.0  
   832x624        74.6  
   800x600        72.2     75.0     60.3     56.2  
   640x480        72.8     75.0     66.7     60.0  
   720x400        70.1  
DP-2 connected (normal left inverted right x axis y axis)
   1600x900       60.0 +
   1280x1024      75.0     60.0  
   1152x864       75.0  
   1024x768       75.1     60.0  
   800x600        75.0     60.3  
   640x480        75.0     60.0  
   720x400        70.1
```

thats my connection when I'm docked.

---

### Post by b9red on 2012-04-05
If it helps I have been looking around for some solutions and this article seems to be of some help. I just could use some advice on changing up certain things.

[https://help.ubuntu.com/community/DynamicMultiMonitor](https://help.ubuntu.com/community/DynamicMultiMonitor)

This is what I've rehashed it into
```
#!/bin/sh

# Sets the secondary display to the proper resolution if attached.

LAPTOP="eDP-1"
HAVE_MON1="`xrandr | grep 'DP-1 connected' | wc -l`"
HAVE_MON2="`xrandr | grep 'DP-2 connected' | wc -l`"

if [ $HAVE_MON1 = "1" ] ; then
    EXTERNAL_OUTPUT="DP-1"
elif [ $HAVE_MON2 = "1" ] ; then
    EXTERNAL_OUTPUT="DP-2"
else
    EXTERNAL_OUTPUT=""
fi

AT_OFFICE1="`ip -o addr show dev eth0 | grep 'inet 192.168.1.' | wc -l`"
AT_HOME="`ip -o addr show dev eth0 | grep 'inet 192.168.30.' | wc -l`"

xrandr --output $LAPTOP --preferred

if [ ! -x $EXTERNAL_OUTPUT ] ; then
    if [ $AT_OFFICE2 = "1" ] ; then
        xrandr --output $EXTERNAL_OUTPUT --mode "1600x900" --pos 1600x0 --primary #--output $LAPTOP --mode "1400x900" --pos 0x500
    fi

    if [ $AT_HOME = "1" ] ; then
        #xrandr --output $LAPTOP --preferred
        xrandr --output $EXTERNAL_OUTPUT --mode "1600x900" --pos 1600x0 --primary --output $LAPTOP --mode "1400x900" --pos 0x500
    fi
fi

```I'm just not sure what to do with the whole at work IP thing, I guess change it to only switch when DP-1 & DP-2 are connected? I wouldn't know what to throw in there though. Plus unlike his setup I can't have my laptop monitor on with my two monitors, so I'm not sure what to do about that.

---

### Post by b9red on 2012-04-05
Its easier to just have a keystroke for autorandr to switch configurations.
[http://unix.stackexchange.com/questions/4489/a-tool-for-automatically-applying-randr-configuration-when-external-display-is-p/13917#13917](http://unix.stackexchange.com/questions/4489/a-tool-for-automatically-applying-randr-configuration-when-external-display-is-p/13917#13917)

There is also a pretty decent script in that thread which you can rehash to what I wanted.

---

