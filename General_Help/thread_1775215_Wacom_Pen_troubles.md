---
title: "Wacom Pen troubles"
date: 2011-06-04
forum: General Help
---

### Post by Awesomebill on 2011-06-04
Hello, I have a wacom bamboo pen tablet that was working great until recently. Now when ever I touch the stylus to the tablet it causes the cursor to freeze and lag behind.  Any help would be appreciated. Running 10.04

---

### Post by Favux on 2011-06-04
Hi Awesomebill,

Welcome to Ubuntu forums!

Let's find out if your Bamboo Pen is using the Wacom drivers.  Enter the following commands in a terminal and post the outputs:
```
xinput list
and
xsetwacom list
```

---

### Post by Awesomebill on 2011-06-04
xinput list gives me

&#9121; Virtual core pointer                        id=2    [master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer                  id=4    [slave  pointer  (2)]
&#9116;   &#8627; Wacom Bamboo 4x5 Pen                        id=8    [slave  pointer  (2)]
&#9116;   &#8627; Wacom Bamboo 4x5 Finger                     id=9    [slave  pointer  (2)]
&#9116;   &#8627; Microsoft Comfort Optical Mouse 1000        id=10    [slave  pointer  (2)]
&#9116;   &#8627; Macintosh mouse button emulation            id=12    [slave  pointer  (2)]
&#9123; Virtual core keyboard                       id=3    [master keyboard (2)]
    &#8627; Virtual core XTEST keyboard                 id=5    [slave  keyboard (3)]
    &#8627; Power Button                                id=6    [slave  keyboard (3)]
    &#8627; Power Button                                id=7    [slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard                id=11    [slave  keyboard (3)]

and xsetwacom list doesn't output anything

---

### Post by Favux on 2011-06-04
Alright, the lack of output with xsetwacom list and the fact you are only seeing two Wacom devices, Pen and Finger, without the other two devices and stylus and touch appended to them indicate you are not on the Wacom X driver.

Let's check your 10-wacom.conf first.  Look in /usr/lib/X11/xorg.conf.d for it.  If it is there post the contents.

---

### Post by Awesomebill on 2011-06-04
I dont see a 10-wacom.conf file in there

---

### Post by Favux on 2011-06-04
Let's manually install one.  Use the example one in part III. of the [Bamboo P&T HOW TO]("http://ubuntuforums.org/showthread.php?t=1515562") with the Lucid edit line.  After saving and closing the new wacom.conf restart.  That should fix it.

Also please consider posting on this Launchpad bug report so this problem gets some attention:  [https://bugs.edge.launchpad.net/ubuntu/+bug/770082](https://bugs.edge.launchpad.net/ubuntu/+bug/770082)

---

### Post by Awesomebill on 2011-06-04
That did it! Thanks for the help Favux. Now I wish i knew what caused it mess up in the first place.

---

### Post by Favux on 2011-06-04
Good!  :)

I think Ubuntu did it with a change/bug in the packaging somewhere.  There have been updates in the last couple of months now that make the 10-wacom.conf disappear or maybe have the wrong permissions.  That's why I want you to post on the bug report.

---

