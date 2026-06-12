---
title: "Trust tablet tb4200 problems!!"
date: 2010-09-15
forum: General Help
---

### Post by nicotrial on 2010-09-15
hi):P im on ubuntu 10.04 and have a Trust tb 4200 tablet.. and having problems with my trust tablet runing on ubuntu.. i pluged in the tablet and to my amaze it started working right away until i pressed the pen on the tablet.. i cant seem to move the mouse curser anymore unless i touch the pen on the tablet. (wich acts as a click) so i thought that i may be missing the drivers.. i checked thes forum and there was a post to install the aptek drivers which i did (but still worked the same) and i found out thet there was no 10-aiptek.fdi (in "/etc/hal/fdi/policy/") so i created one and copied one from a post.. in [http://ubuntuforums.org/showpost.php?p=7604483&postcount=50](http://ubuntuforums.org/showpost.php?p=7604483&postcount=50) but still cant move the courser without touching.. its like if it did no diference at all.. i also changed the values in the 10-aiptek.fdi with no changes.. the size of the tablet is just the size of the screen so i am using the full tablet.. and no buttons work...

i think the drivers are not workin.. in the synaptic it shows as intalled...

```

I: Bus=0003 Vendor=08ca Product=0010 Version=0105
N: Name="Aiptek"
P: Phys=usb-0000:00:1d.0-1/input0
S: Sysfs=/devices/pci0000:00/0000:00:1d.0/usb4/4-1/4-1:1.0/input/input8
U: Uniq=
H: Handlers=kbd mouse2 event8 
B: EV=1f
B: KEY=1cdf 0 70000 0 7 ff800000 ff 0 180001f f8000000 3
B: REL=103
B: ABS=100 d000103
B: MSC=1

``````
Bus 004 Device 002: ID 08ca:0010 Aiptek International, Inc. Tablet

```thanks!!!

---

### Post by Favux on 2010-09-15
Hi nicotrial,

Welcome to Ubuntu forums!

With Lucid and it's hybrid Xserver 1.7 HAL/.fdi is no more.  Instead you now use .conf files in xorg.conf.d.

So remove the aiptek.fdi file and see if you have a aiptek.conf file at /usr/lib/X11/xorg.conf.d/.  In other words did the Aiptek driver package install one?  If so we need to look at the contents, there may be a problem with the match line.

---

### Post by nicotrial on 2010-09-15
hi thanks for the help no the install did not creat one should i creat one manualy?? do i put in the same code as before??

this is what is in the folder
```

05-evdev.conf  10-synaptics.conf  10-vmmouse.conf  10-wacom.conf

```

---

### Post by Favux on 2010-09-15
Let's look at the output in a terminal of:
```
xinput --list
```
to check.  But this will probably work:
```
Section "InputClass"
    Identifier "Aiptek class"
    MatchProduct "Aiptek"
    MatchDevicePath "/dev/input/event*"
    Driver "aiptek"
    Option "USB" "on"
    Option "Mode" "absolute"
    Option "zMin" "0"
    Option "zMax" "511"
EndSection
```
Install it with:
```
gksudo gedit /usr/lib/X11/xorg.conf.d/20-aiptek.conf
```

---

### Post by nicotrial on 2010-09-15
ok fixed !!!! wujuuu i dont know if the pressure tip works but its perfect... butons and everything!!

here is the rest if anyone stumbles to this thread!!!

[https://help.ubuntu.com/community/AiptekTablet+aiptek.conf&cd=2&hl=en&ct=clnk&client=ubuntu](https://help.ubuntu.com/community/AiptekTablet+aiptek.conf&cd=2&hl=en&ct=clnk&client=ubuntu)

just had to change the zmax to 1025 and workd perfect...

is the zmax the higher the value the higher i can lift the pen??? if so i would like to double this value.. how much can i go??:popcorn:

---

### Post by Favux on 2010-09-15
No, the zmax is the maximum pressure level.  If instead of 512 your tablet has 1024 pressure levels the number you should use is is 1023 rather than 511.  Have you confirmed pressure works?

---

### Post by nicotrial on 2010-09-15
ok the pressure also works in gimp THANK YOU!! i just needed that litle oriantation hehe):P

---

### Post by Favux on 2010-09-15
Could you show me the output of 'xinput --list'?  I want to see if "Option "Type" "stylus"" is doing anything.  And "Option "SendCoreEvents" "true"" shouldn't be needed with Lucid's Xserver 1.7.

---

### Post by nicotrial on 2010-09-15
is this what you are asking for???

```
$ xinput --list
&#9121; Virtual core pointer                        id=2    [master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer                  id=4    [slave  pointer  (2)]
&#9116;   &#8627; Aiptek                                      id=9    [slave  pointer  (2)]
&#9116;   &#8627; SynPS/2 Synaptics TouchPad                  id=11    [slave  pointer  (2)]
&#9116;   &#8627; Macintosh mouse button emulation            id=12    [slave  pointer  (2)]
&#9123; Virtual core keyboard                       id=3    [master keyboard (2)]
    &#8627; Virtual core XTEST keyboard                 id=5    [slave  keyboard (3)]
    &#8627; Power Button                                id=6    [slave  keyboard (3)]
    &#8627; Video Bus                                   id=7    [slave  keyboard (3)]
    &#8627; Sleep Button                                id=8    [slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard 
```


```
xinput --list Aiptek
Aiptek                                      id=9    [slave  pointer  (2)]
    Reporting 6 classes:
        Class originated from: 9
        Buttons supported: 5
        Button labels: Button Left Button Middle Button Right Button Wheel Up Button Wheel Down
        Button state:
        Class originated from: 9
        Detail for Valuator 0:
          Label: Abs X
          Range: 0.000000 - 5999.000000
          Resolution: 14763 units/m
          Mode: relative
        Class originated from: 9
        Detail for Valuator 1:
          Label: Abs Y
          Range: 0.000000 - 4499.000000
          Resolution: 14763 units/m
          Mode: relative
        Class originated from: 9
        Detail for Valuator 2:
          Label: Abs Pressure
          Range: 0.000000 - 511.000000
          Resolution: 512 units/m
          Mode: relative
        Class originated from: 9
        Detail for Valuator 3:
          Label: Abs Tilt X
          Range: -128.000000 - 127.000000
          Resolution: 256 units/m
          Mode: relative
        Class originated from: 9
        Detail for Valuator 4:
          Label: Abs Tilt Y
          Range: -128.000000 - 127.000000
          Resolution: 256 units/m
          Mode: relative

```

---

### Post by Favux on 2010-09-15
Yes, thank you.  It's looking like the stylus Option isn't doing anything.  You could try removing it along with the "SendCoreEvents" line and see if it makes any difference.  Two other Options you could check are:
```
    Option "ZThreshold" "5"

and/or

    Option "Pressure" "linear"

```
if you're having trouble with pressure.

And the reason to use:
```
    Identifier "Aiptek class"
```
is if you're looking at say Xorg.0.log to check out your tablet's initialization it's unambiguous what's being referred to.

---

### Post by nicotrial on 2010-09-15
one more questtion it there any way i can pass pressure sensor to a virtualbox with windows Xp to use photoshop?? this will just solve 100% all my problems!!

---

### Post by nicotrial on 2010-09-16
ok by putting in these two options and removing the stylus the pad compleatly stoped working!!;) looks likt the stylus option realy does somthing...

---

### Post by nicotrial on 2010-09-16
its not even listed

```
$ xinput --list
&#9121; Virtual core pointer                        id=2    [master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer                  id=4    [slave  pointer  (2)]
&#9116;   &#8627; SynPS/2 Synaptics TouchPad                  id=10    [slave  pointer  (2)]
&#9116;   &#8627; Macintosh mouse button emulation            id=11    [slave  pointer  (2)]
&#9123; Virtual core keyboard                       id=3    [master keyboard (2)]
    &#8627; Virtual core XTEST keyboard                 id=5    [slave  keyboard (3)]
    &#8627; Power Button                                id=6    [slave  keyboard (3)]
    &#8627; Video Bus                                   id=7    [slave  keyboard (3)]
    &#8627; Sleep Button                                id=8    [slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard                id=9    [slave  keyboard (3)]

```

---

### Post by Favux on 2010-09-16
Right, that's suggestive, but you did add the other two options.  Does adding stylus back in, leaving the two new options alone, get it working again?

---

