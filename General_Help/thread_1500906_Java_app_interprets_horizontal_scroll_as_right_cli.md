---
title: "Java app interprets horizontal scroll as right click"
date: 2010-06-03
forum: General Help
---

### Post by m4lte on 2010-06-03
Hi there,
I'm running 10.4 on a Lenovo thinkpad laptop. Usually I can use the right and bottom edge of my touchpad for vertical/horizontal scrolling (e.g. in firefox). However in one java application (Matlab), the horizontal scrolling is interpreted as a right click. In a similar way, when I touch the upper right corner of the touchpad, it's interpreted as a middle mouse button click. This is very annoying.
How can I solve this problem? Is it a problem of Java or a problem of my touchpad driver?
Thanks for any ideas!

---

### Post by kan.izh on 2010-08-09
I have the same problem. Any ideas anybody?

---

### Post by Jasev on 2010-08-15
I'm having the same problem with Matlab (2010a) and Ubuntu 10.10 with an Apple magic mouse. Not even sure where to start the debug, but its driving me insane. Everytime I do a horizontal scroll or a slightly diagonal scroll when vertically scrolling, the right-click menu pops up 

Any help would be appreciated.

Cheers

---

### Post by superdav42 on 2010-08-24
This has been plaguing me too using a might mouse. There are several Java apps I use on a regular basis and horizontal scrolling somehow does right click. Very easy to do and very annoying especially in Netbeans 6.8. I'd be willing just do disable horizontal scrolling. Seems like this is a bug in Java. see
[http://bugs.sun.com/bugdatabase/view_bug.do?bug_id=6440198](http://bugs.sun.com/bugdatabase/view_bug.do?bug_id=6440198)
and
[http://bugs.sun.com/bugdatabase/view_bug.do?bug_id=6315717](http://bugs.sun.com/bugdatabase/view_bug.do?bug_id=6315717)
 

Seems like it used to not work at all now we have some half backed buggy implementation. 

I tried Sun jre and openjdk jre but they both do the same thing. 

Anyone know how to fix this or disable horizontal scrolling per application?

---

### Post by vace117 on 2010-09-15
> Anyone know how to fix this or disable horizontal scrolling per application?
Not exactly what you are looking for, but here is what I did to get this to work on my Lenovo T60. I put together two scripts - one that disables the horizontal scroll and one that enables it. This way when I am working in NetBeans, Oracle Developer, or any other annoying java app, I run *hscroll_disable*. When I need the scrolling back, like when I go back to Eclipse, I run *hscroll_enable*.

*hscroll_disable*:
```

DEVICE_NAME='TPPS/2 IBM TrackPoint'
PROP_NAME='Evdev Wheel Emulation Axes'

xinput set-int-prop "$DEVICE_NAME" "$PROP_NAME" 8 4 5 4 5
if [[ $? -eq 0 ]] ; then
  zenity --info --text "Horizontal Scrolling Disabled"
else
  zenity --error --text "Error disabling horizontal scroll."
fi

```

*hscroll_enable*:
```

DEVICE_NAME='TPPS/2 IBM TrackPoint'
PROP_NAME='Evdev Wheel Emulation Axes'

xinput set-int-prop "$DEVICE_NAME" "$PROP_NAME" 8 6 7 4 5
if [[ $? -eq 0 ]] ; then
  zenity --info --text "Horizontal Scrolling Enabled"
else
  zenity --error --text "Error enabling horizontal scroll."
fi

```

You can find out which device name to use on your system like this:
```

root@thinkpad:/usr/local/bin# xinput list --short
"Virtual core pointer"  id=0    [XPointer]
"Virtual core keyboard" id=1    [XKeyboard]
"ThinkPad Extra Buttons"        id=2    [XExtensionKeyboard]
"AT Translated Set 2 keyboard"  id=3    [XExtensionKeyboard]
"Video Bus"     id=4    [XExtensionKeyboard]
"Macintosh mouse button emulation"      id=5    [XExtensionPointer]
"TPPS/2 IBM TrackPoint" id=6    [XExtensionPointer]

```

And then:
```

root@thinkpad:/usr/local/bin# xinput list-props "TPPS/2 IBM TrackPoint"
Device 'TPPS/2 IBM TrackPoint':
        Device Enabled (93):            1
        Evdev Axis Inversion (230):             0, 0
        Evdev Reopen Attempts (227):            10
        Evdev Axis Calibration (228):           
        Evdev Axes Swap (229):          0
        Evdev Middle Button Emulation (231):            1
        Evdev Middle Button Timeout (232):              50
        Evdev Wheel Emulation (233):            1
        Evdev Wheel Emulation Axes (234):               6, 7, 4, 5
        Evdev Wheel Emulation Inertia (235):            10
        Evdev Wheel Emulation Timeout (236):            200
        Evdev Wheel Emulation Button (237):             2
        Evdev Drag Lock Buttons (238):          0

```

to find out the property name.

---

