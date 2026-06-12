---
title: "Five buttom mouse issue"
date: 2006-03-17
forum: General Help
---

### Post by dc2447 on 2006-03-17
I am havig problems gvetting my fice button mouse to work under Kubuntu, specifically the side buttons don't work

here is my xorg.conf - anyone assist?

> Section "InputDevice"
    Identifier "Configured Mouse"
    Driver "mouse"
    Option "CorePointer"
    Option "Protocol"        "IMPS/2"
    Option "Device"          "/dev/input/mice"
    Option "SendCoreEvents"  "true"
    Option "Buttons"         "5"
    Option "ZAxisMapping"    "4 5"
EndSection


---

### Post by frodon on 2006-03-17
This guide may help you : [http://doc.gwos.org/index.php/5ButtonMouse](http://doc.gwos.org/index.php/5ButtonMouse)

---

### Post by dc2447 on 2006-03-17
I have tried these instructions

Whe I try and execute:


> exec xmodmap -e "pointer = 1 2 3 6 7 4 5 8 9" &
exec imwheel -k -b "67" &
exec $REALSTARTUP

I get

> xmodmap:  commandline:1:  bad number of buttons, must have 5 instead of 9
xmodmap:  1 error encountered, aborting.


If I change the above to

> exec xmodmap -e "pointer = 1 2 3 4 5 " &
exec imwheel -k -b "67" &
exec $REALSTARTUP


The side buttons don't work at all

Thanks

---

### Post by PFD27 on 2006-03-18
"exec imwheel -k -b "67" &"

try changing the 67 to 45

---

### Post by Harleen on 2006-03-18
Change this:```
 Option "Buttons" "5"
```to that:```
 Option "Buttons" "7"
```

Because additionally to the three default buttons, the mouse wheel takes button 4 & 5, which is set here:
```
  Option "ZAxisMapping" "4 5"
```

So the next two buttons are number 6 and 7. That's at least how it's working for me. I didn't need to fiddle around with IMWheel.

---

