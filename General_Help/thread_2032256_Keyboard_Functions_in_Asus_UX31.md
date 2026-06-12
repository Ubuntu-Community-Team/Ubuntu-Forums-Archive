---
title: "Keyboard Functions in Asus UX31"
date: 2012-07-23
forum: General Help
---

### Post by JCM_Pico on 2012-07-23
Hi there

I've have recently installed kubuntu 12.04 in my Asus UX31A.204. Although I've found that it keyboard functions should work properly, they does't... I'm not able to adjust the screen brightness, volume, turn on/off wireless neither adjust the keyboard backlight...

[https://help.ubuntu.com/community/AsusZenbook#Keyboard](https://help.ubuntu.com/community/AsusZenbook#Keyboard)

Is there any thing I can do to know whats wrong... or some way to fix it?

---

### Post by rhysforge on 2012-07-23
I just picked up a Asus X401A-RGN4 two days ago.   I have a similar problem.   I tried scanning the keyboard for the FN button's value, this is has turned out to be troublesome.   It's like the key is just Dead even when in TTY.    The keyboard is not a usb device, so no dice with usbmon and wireshark.    So I'm thinking this is a kernel driver issue, still might be a Xorg config issue.    I'm attempting to figure out the specific keyboard hardware to see if there is a driver that I can modprobe, or go to a newer kernal, etc...  lshw doesn't show what the keyboard is.  dmidecode is a bust too.      

So, Anyone know any other commands to list hardware to find out what the keyboard has in it?     

As far as a work around, for the fn button being dead.   I just remapped the short cuts for the volume up,down, etc  to be the correct f-key + alt.   For the brightness control this is was trickier.  if you look at /sys/class/backlight/[your hardware]/max_brightness
```

`sudo cat /sys/class/backlight/[your hardware]/max_brightness`

```
 you can change your brightness with this,  make sure [value] is less than your max brightness.
```

`sudo echo [value] > /sys/class/backlight/[your hardware]/brightness`

```
 you will have to run the following command to give your user permission to modify the brightness file by taking ownership of it.  ```
`sudo chown  your_username: /sys/class/backlight/[your hardware/brightness`
``` 

Now you can then write your own brightnessup.sh and a brightnessdown.sh bash scripts.    that increment the [value] up and down.  

something like this for brightnessup.sh, just replace [your hardware] with your laptops backlight hardware, just `ls /sys/class/backlight/` to find out.   you will also have to replace [Value up] with how much brightness you want to add to your current brightness.
   
```

#!/bin/sh

MAX_BRIGHT=`cat /sys/class/backlight/[your hardware]/max_brightness`
CUR=`cat /sys/class/backlight/[your hardware]/brightness`
STEP=[value up]
#STEP=1000
#NOTE 1000 is my step.  my asus hardware max is 4296,  my msi's max brightness is 
#8. so you will have to play with it.

##don't modify below this unless you really want to :)

if [ $CUR -lt $MAX_BRIGHT ] 
then
    CUR=`expr $CUR + $STEP`  

    if [ $CUR -gt $MAX_BRIGHT ]
    then
       CUR=$MAX_BRIGHT
    fi
    echo $CUR > /sys/class/backlight/[your hardware]/brightness
fi

```

for brightnessdown.sh, same deal change [your hardware] with your hardware, and [Value Down] with your value you want to subtract from your current brightness. 

```

#!/bin/sh

#MAX_BRIGHT=`cat /sys/class/backlight/[your hardware]/max_brightness`
CUR=`cat /sys/class/backlight/[your hardware]/brightness`
STEP=[value down]
#STEP=1000
#NOTE 1000 is my step.  my asus hardware max is 4296,  my msi's max brightness is 
#8. so you will have to play with it.

##don't modify below this unless you really want too :)

if [ $CUR -gt 0 ] 
then
    CUR=`expr $CUR - $STEP`  
 
    if [ $CUR -le 0 ]
    then
       CUR=0
    fi
    echo $CUR > /sys/class/backlight/[your hardware]/brightness
fi

```


Then move these scripts to /usr/bin/ and then add a custom keyboard short cuts to run /usr/bin/brightnessup.sh and another for /usr/bin/brightnessdown.sh  and your in business.  Well at least until a real fix is found.

---

### Post by JCM_Pico on 2012-07-23
Thank you very much... it work fine :D

Just one thing... 
Instead of 
```
if [ $CUR -gt 0 ] 
then
    $CUR=`expr $CUR - $STEP`  
 
```

I've used 
```
if [ $CUR -gt 0 ] 
then
    CUR=`expr $CUR - $STEP`  
 
```

---

### Post by rhysforge on 2012-07-24
JCM  yeah that was my typo.  $CUR=   would never work.   Thanks for pointing this out.

---

### Post by JCM_Pico on 2012-07-25
I've to run

```
sudo chown  your_username: /sys/class/backlight/[your hardware/brightness
```

Every time I boot up the system in order to this workaround to work... is there any way to make it permanent?

---

