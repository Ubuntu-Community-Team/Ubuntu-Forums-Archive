---
title: "How to save changes made to IBM TrackPoint settings?"
date: 2011-03-16
forum: General Help
---

### Post by Rasa1111 on 2011-03-16
Hey my peoples...

 I need to know how *if* I can save recent changes made in terminal, to my IBM TrackPoint settings?
er
 I recently came across this post.. by Brian Spilner,
Showing how to "re-enable" Trackpoint scrolling.
[http://ubuntuforums.org/showpost.php?p=10561062&postcount=104](http://ubuntuforums.org/showpost.php?p=10561062&postcount=104)
(his post quoted with my reply)

Doing this, works great!
But whenever i log out, and back in.. the settings have reverted back,
so that I can no longer use trackpoint, and middle button to scroll, Unless I re-enter the commands. 

Is there a way that I can save these settings so that they stick, whenever i log out/in? 

Instructions are here~
3 commands used in **Bold**
> The TrackPoint is the red nub in the middle of the keyboard and the three buttons right below the keyboard. By default Press-To-Select, the process of pushing down on the TrackPoint to click, is turned off. Also, by default the TrackPoint's middle click performs the Paste function.

In this tutorial I will describe how to adjust these settings activate the middle click scroll and Press-To-Select similar to Windows.

2. Configure TrackPoint Middle Mouse Scroll

I wanted to configure the middle click on the TrackPoint to scroll just like in Windows so I used the following commands to achieve it.

2.1: Find the ID number for the TrackPoint

The first step is to find the xinput id number for the IBM TrackPoint. Run the following command.

xinput list

 

You should receive all the available devices for xinput. One of the devices should say:

"TPPS/2 IBM TrackPoint"    id=9    [XExtensionPointer]
    Type is MOUSE
    Num_buttons is 5
    Num_axes is 2
    Mode is Relative
    Motion_buffer is 256
    Axis 0 :
        Min_value is -1
        Max_value is -1
        Resolution is 1
    Axis 1 :
        Min_value is -1
        Max_value is -1
        Resolution is 1

 

Or something very similar. The "id=#" is the important number we will be using in the following commands. Later it will save the headache of typing that very long device name.

2.2: TrackPoint Middle Mouse Scroll

Next run the following commands to enable the middle mouse scroll.

[B]xinput set-int-prop # "Evdev Wheel Emulation" 8 1
xinput set-int-prop # "Evdev Wheel Emulation Button" 8 2
xinput set-int-prop # "Evdev Wheel Emulation Timeout" 16 200[/B]

*** Replace # with the id number for the TrackPoint from the previous command.

Now you should be able to middle scroll by pressing the middle mouse button for the TrackPoint and moving the TrackPoint up and down.


 Quite simple, and very effective!
I just need to be able to keep the settings,
rather than having to re-enter them on every boot? 

Anyone who can help?

Thanks a lot.
<3

---

### Post by Rasa1111 on 2011-03-16
ashamed.. i bump... lol

 Anyone have any ideas today? 

I just need to know how to "save" settings made in terminal?

---

### Post by Rasa1111 on 2011-03-17
dang..

 even more ashamed now..
i bump one last time.. :(  

anyone?

---

### Post by Rasa1111 on 2011-03-22
SOLVED FInally! (with no help from you guys!) lol  :P

Was actually quite simple...

 I created a file with Gedit called ".trackscroll-startup.sh"
and inside the file i put 
```
#!/bin/bash
xinput set-int-prop 11 "Evdev Wheel Emulation" 8 1
xinput set-int-prop 11 "Evdev Wheel Emulation Button" 8 2
xinput set-int-prop 11 "Evdev Wheel Emulation Timeout" 16 200
```

 then i went to startup applications,
added a new entry called "trackscroll", 
and used the name of the file as the "command" (.trackscroll-startup.sh)

and it works prefectly!
even works on resume from suspend (which ive read otherwise)
[http://www.thinkwiki.org/wiki/How_to_configure_the_TrackPoint](http://www.thinkwiki.org/wiki/How_to_configure_the_TrackPoint)

Anyway, Solved, and Happy! :)

 You guys are lucky you're soo helpful most other times..
or i'd be mad at you for leaving me hangin like this... lol :lol: :P

<3

---

### Post by Kanehekili on 2011-10-06
> **Rasa1111 said:**
> SOLVED FInally! (with no help from you guys!) lol  :P

Was actually quite simple...

 I created a file with Gedit called ".trackscroll-startup.sh"
and inside the file i put 
```
#!/bin/bash
xinput set-int-prop 11 "Evdev Wheel Emulation" 8 1
xinput set-int-prop 11 "Evdev Wheel Emulation Button" 8 2
xinput set-int-prop 11 "Evdev Wheel Emulation Timeout" 16 200
``` then i went to startup applications,
added a new entry called "trackscroll", 
and used the name of the file as the "command" (.trackscroll-startup.sh)

and it works prefectly!
even works on resume from suspend (which ive read otherwise)
[http://www.thinkwiki.org/wiki/How_to_configure_the_TrackPoint](http://www.thinkwiki.org/wiki/How_to_configure_the_TrackPoint)

Anyway, Solved, and Happy! :)

 You guys are lucky you're soo helpful most other times..
or i'd be mad at you for leaving me hangin like this... lol :lol: :P

<3

There is another way to do it (works in Lucid as well as in Natty):
Create the file 60-thinkpad-trackpoint.conf in "/usr/share/X11/xorg.conf.d/"
( "/usr/lib/X11/xorg.conf.d/" in Lucid)

The file contains the following lines:
```
Section "InputClass"
    Identifier    "ThinkPad TrackPoint"
    MatchProduct    "TPPS/2 IBM TrackPoint"
    MatchDevicePath    "/dev/input/event*"
    Option        "EmulateWheel"        "true"
    Option        "EmulateWheelButton"    "2"
    Option        "XAxisMapping"        "6 7"
    Option        "YAxisMapping"        "4 5"
EndSection
```Thats it. works like charme, after a login

---

### Post by Rasa1111 on 2011-10-06
cool! good to know Thanks. :)

Thankfully..
in ubuntu 11.10..
it all works perfectly right "out of the box"!  :D

---

