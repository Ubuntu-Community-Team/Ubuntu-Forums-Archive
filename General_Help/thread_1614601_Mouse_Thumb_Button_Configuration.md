---
title: "Mouse Thumb Button Configuration"
date: 2010-11-05
forum: General Help
---

### Post by jfeist1 on 2010-11-05
Hey guys, Running Ubuntu Studio 10.04 with an MS wireless notebook optical mouse 4000. By default, my thumb button is acting as a "Forward" button, but I want it to be my "Back" button. 

  I have not installed anything like imwheel, nor do I want to, especially because the button support is obviously already there, it just needs to be configured to a new command.

 My xorg.conf looks like this (at least the parts of it that I think are relevant, please let me know if you need to see the rest of it):

```
...
Section "ServerLayout"
    Identifier     "Layout0"
    Screen      0  "Screen0" 0 0
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
    Option         "Xinerama" "0"
EndSection

Section "Files"
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

Section "InputDevice"
    # generated from default
    Identifier     "Keyboard0"
    Driver         "kbd"
EndSection
...
```

I have tried messing with Emulate3Buttons and the ZAxisMappings, but there were no changes. Please tell me if I am in the right place? Or is there another program or something running already that is controlling my mouse. 

Thank you all for all of your support and great ideas.

---

### Post by thehipho on 2010-11-05
Have you tried adding this already?

 Option         "ZAxisMapping" "4 5 6 7 8 9"

---

### Post by jfeist1 on 2010-11-05
Thanks thehipho,

   Yeah, tried it again now just in case, but nothing appears to be different. The thumb button still operates as "Forward" instead of "Back".

  I am still pretty new to it all, any idea what I should expect to happen if I mixed up the numbers? Maybe: 

Option "ZaxisMapping" "4 5 7 6 8 9"

I am a little scared to just 'test' it out and go for it. 

Thanks again,

---

### Post by jfeist1 on 2010-11-06
I have tried remapping the keys using the theory and methods described [HERE]("http://www.mythtv.org/wiki/Remapping_remote_control_key_codes_greater_than_255"), but again nothing changes.

Is xorg.conf even in control of my mouse? Is there an unknown (to me) imwheel-type program running in Ubuntu Studio 10.04? Should I just install 10.10?

As always, any help would be greatly appreciated!

---

### Post by tredegar on 2010-11-06
This link might help you: [http://www.linuxquestions.org/questions/ubuntu-63/need-optical-mouse-with-side-buttons-that-works-out-of-the-box-with-lucid-814150/page3.html#post4021660](http://www.linuxquestions.org/questions/ubuntu-63/need-optical-mouse-with-side-buttons-that-works-out-of-the-box-with-lucid-814150/page3.html#post4021660)

Obviously, cabman's mouse problem is different from yours, but if you read the whole thread ( and there's quite a bit of "noise" ), you'll get a better understanding, I hope.

Bottom line: **xmodmap** is your friend ;)

---

### Post by jfeist1 on 2010-11-21
```
xmodmap -e "pointer = 1 2 3 4 5 6 7 9 8"
```

Thank you so much tredegar, your simple line above solved everything. Took a little while to figure out which buttons to change around, but in the end this is the right one for this mouse.

---

### Post by tredegar on 2010-11-21
Pleased you got it fixed. Hope you have worked out how to make this change apply every time your PC boots.

Please make a note somewhere, of exactly what you did to fix this problem, because you'll probably meet it again when you install a newer "linux". Saves time and frustration.

And thanks for the "thanks". I appreciate constructive feedback :)

Have fun.

---

