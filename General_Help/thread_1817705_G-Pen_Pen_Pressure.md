---
title: "G-Pen Pen Pressure"
date: 2011-08-03
forum: General Help
---

### Post by ale.junuzovic on 2011-08-03
Hello everyone, i managed to install Photoshop over Wine nd it s working like a charm. Installing the Tablet was even more easy, just used Wizardpen (reconized) nd WORKS! 

But the Pen Pressure aint working, can someone tell me what can i do, because this is the last thing i need for a new life as an Ubuntu user. 

My tablet is Genius G-Pen M712X nd Ubuntu 11.04.

---

### Post by Favux on 2011-08-03
Hi ale.junuzovic,

Are you asking about pressure in Wine or pressure generally with the WizardPen X driver?

Since HAL was deprecated starting with Lucid .fdi files are no longer used to configure things.  Currently xorg.conf.d and .conf files are used.  In your case it would be the 70-wizardpen.conf file in /usr/share/X11/xorg.conf.d.

What is the output of *xinput list* in a terminal and the tablet line in the output of *lsusb*?

---

### Post by ale.junuzovic on 2011-08-04
Favux bud, i don t know what s for it s needed. I mean i need it to work in photoshop (which run with wine). Well i m complete new to unix systems, an idiot, so i don t realy know how do some stuff. 

I found the directory in X11 but there is 50-wizardpen.conf, not 70... 

**Screenshot of the folder:**
[IMG]http://i56.tinypic.com/21cdtnl.png[/IMG]

**Here is xinput list**
```
ale@ubuntustar:~$ xinput list
&#9121; Virtual core pointer                    	id=2	[master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer              	id=4	[slave  pointer  (2)]
&#9116;   &#8627; MosArt Optical Mouse                    	id=8	[slave  pointer  (2)]
&#9116;   &#8627; WALTOP International Corp. Media Tablet 	id=9	[slave  pointer  (2)]
&#9123; Virtual core keyboard                   	id=3	[master keyboard (2)]
    &#8627; Virtual core XTEST keyboard             	id=5	[slave  keyboard (3)]
    &#8627; Power Button                            	id=6	[slave  keyboard (3)]
    &#8627; Power Button                            	id=7	[slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard            	id=12	[slave  keyboard (3)]
    &#8627; WALTOP International Corp. Media Tablet 	id=10	[slave  keyboard (3)]
    &#8627; WALTOP International Corp. Media Tablet 	id=11	[slave  keyboard (3)]

```

_Here the Id=9 waltop query:_
```

ale@ubuntustar:~$ xinput query-state 9
2 classes :
ButtonClass
	button[1]=up
	button[2]=up
	button[3]=up
	button[4]=up
	button[5]=up
	button[6]=up
	button[7]=up
ValuatorClass Mode=Absolute Proximity=In
	valuator[0]=840
	valuator[1]=525
	valuator[2]=0

```

**nd lsusb**
```
ale@ubuntustar:~$ lsusb
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 004: ID 172f:0500 Waltop International Corp. 
Bus 006 Device 002: ID 062a:0003 Creative Labs 
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 0cf3:9271 Atheros Communications, Inc. AR9271 802.11n
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```

---

### Post by Favux on 2011-08-04
Alright you have a Waltop tablet in Natty.  Do you have it on the Wacom X driver?
```
xinput list-props 9
```
If not see the [Waltop HOW TO]("http://ubuntuforums.org/showthread.php?t=1595648").

Are you using Unity or Classic Mode?

---

### Post by ale.junuzovic on 2011-08-04
```
ale@ubuntustar:~$ xinput list-props 12 [COLOR=Red](listed as id 12)[/COLOR]
Device 'WALTOP International Corp. Media Tablet':
    Device Enabled (132):    1
    Coordinate Transformation Matrix (134):    1.000000, 0.000000, 0.000000, 0.000000, 1.000000, 0.000000, 0.000000, 0.000000, 1.000000
    Device Accel Profile (253):    0
    Device Accel Constant Deceleration (254):    1.000000
    Device Accel Adaptive Deceleration (255):    1.000000
    Device Accel Velocity Scaling (256):    10.000000
    Evdev Axis Inversion (257):    0, 0
    Evdev Axis Calibration (258):    <no items>
    Evdev Axes Swap (259):    0
    Axis Labels (260):    "Abs X" (508), "Abs Y" (509), "Abs Pressure" (510)
    Button Labels (261):    "Button Unknown" (252), "Button Unknown" (252), "Button Unknown" (252), "Button Wheel Up" (138), "Button Wheel Down" (139), "Button Horiz Wheel Left" (140), "Button Horiz Wheel Right" (141)
    Evdev Middle Button Emulation (262):    0
    Evdev Middle Button Timeout (263):    50
    Evdev Wheel Emulation (264):    0
    Evdev Wheel Emulation Axes (265):    0, 0, 4, 5
    Evdev Wheel Emulation Inertia (266):    10
    Evdev Wheel Emulation Timeout (267):    200
    Evdev Wheel Emulation Button (268):    4
    Evdev Drag Lock Buttons (269):    0

```

I m using the classic mode.

---

### Post by Favux on 2011-08-04
As you can see my guess was correct and your Waltop tablet is on the evdev driver.  So the first thing you want to do is get it on the Wacom driver.  Follow my link in the previous post to the Waltop HOW TO.

---

### Post by ale.junuzovic on 2011-08-04
> **Favux said:**
> As you can see my guess was correct and your Waltop tablet is on the evdev driver.  So the first thing you want to do is get it on the Wacom driver.  Follow my link in the previous post to the Waltop HOW TO.

Ok seems i need to have root access do some stuff, i reply when i do ave the driver.

---

### Post by ale.junuzovic on 2011-08-04
> **Favux said:**
> As you can see my guess was correct and your Waltop tablet is on the evdev driver.  So the first thing you want to do is get it on the Wacom driver.  Follow my link in the previous post to the Waltop HOW TO.

Done. 

```
ale@ubuntustar:~$ xinput list-props 9
Device 'WALTOP International Corp. Media Tablet stylus':
    Device Enabled (132):    1
    Coordinate Transformation Matrix (134):    1.000000, 0.000000, 0.000000, 0.000000, 1.000000, 0.000000, 0.000000, 0.000000, 1.000000
    Device Accel Profile (253):    0
    Device Accel Constant Deceleration (254):    1.000000
    Device Accel Adaptive Deceleration (255):    1.000000
    Device Accel Velocity Scaling (256):    10.000000
    Wacom Tablet Area (277):    0, 0, 16383, 16383
    Wacom Rotation (278):    0
    Wacom Pressurecurve (279):    0, 0, 100, 100
    Wacom Serial IDs (280):    1280, 0, 2, 0
    Wacom Capacity (281):    -1
    Wacom Pressure Threshold (282):    27
    Wacom Sample and Suppress (283):    2, 4
    Wacom Enable Touch (284):    0
    Wacom Hover Click (285):    0
    Wacom Enable Touch Gesture (286):    0
    Wacom Touch Gesture Parameters (287):    50, 20, 250
    Wacom Tool Type (288):    "STYLUS" (270)
    Wacom Button Actions (289):    "None" (0), "None" (0), "None" (0), "None" (0), "None" (0), "None" (0), "None" (0), "None" (0), "None" (0), "None" (0), "None" (0), "None" (0), "None" (0), "None" (0), "None" (0), "None" (0)
    Wacom Debug Levels (290):    0, 0

```

Pre Pressure is not working, but Photoshop has reconized it. There is no warning box look here: 
[IMG]http://i55.tinypic.com/9rinnc.jpg[/IMG]

The triangle goes after 10 - 15 seconds nd the 2) brush outline gets the pen pressure shape. Still the lines arent like it, there is no pen pressure on them.

---

### Post by Favux on 2011-08-04
Nice job.

With the Waltop tablet on the Wacom X driver you now should have pressure available in Gimp, Mypaint, etc.

At least Photoshop now recognizes you have pressure.  Your pressure curve is currently set to the default linear pressure:
> Wacom Pressurecurve (279):    0, 0, 100, 100

You can modify it if you want to:  [http://sourceforge.net/apps/mediawiki/linuxwacom/index.php?title=Xsetwacom#PressureCurve](http://sourceforge.net/apps/mediawiki/linuxwacom/index.php?title=Xsetwacom#PressureCurve)

Which version of Photo Shop are you using?
Which version of Wine?  Where did you get Wine?

Are you saying you see pressure in the text box but not in the regular drawing area?  What triangle?  Is it a yellow warning one?

---

### Post by ale.junuzovic on 2011-08-04
Just tryed Pen Pressure in GIMP nd doesn t work. **UPDATE:** Works with GIMP now, needed to change the input device settings to "screen" in GIMP intself.

Will try now to play with values in the driver. 

I m using Photoshop CS5 with Wine 1.3

---

### Post by Favux on 2011-08-04
Did you get the Wine 1.3 from the Natty repository?

That's version 1.3.15.  Version 1.3.25 was just released.  But I don't know if it makes a difference.

---

### Post by 23dornot23d on 2011-08-04
Try Mypaint too .... pressure works for me in that ,,,, and by doing screenshots or saving
the files you can the put them where you want them ... 

[_***Link to a Quick Screenshot .... ***_]("http://img814.imageshack.us/img814/2456/82588753.jpg")

---

### Post by ale.junuzovic on 2011-08-04
> **Favux said:**
> Did you get the Wine 1.3 from the Natty repository?

That's version 1.3.15.  Version 1.3.25 was just released.  But I don't know if it makes a difference.

Well from Software Center, the Version is: 1.3.15-0ubuntu5 (wine1.3)

Will take a look for the new version now. 

Just some more info from GIMP & Mypaint, the Pen Pressure works now but not correct. I mean it affected only the Opaicity. Look in the screenshot there is no change in the brush size. 

[IMG]http://i53.tinypic.com/vq1x55.jpg[/IMG]

---

### Post by Favux on 2011-08-04
New version is here:  [http://www.winehq.org/](http://www.winehq.org/)  in Downloads.

With brush size you have to select another size.

---

### Post by ale.junuzovic on 2011-08-04
> **Favux said:**
> New version is here:  [http://www.winehq.org/](http://www.winehq.org/)  in Downloads.

With brush size you have to select another size.

Here an screen from the repos. 
[IMG]http://i53.tinypic.com/op0lcg.jpg[/IMG]


I know bout brush size :) sorry i didn t said it clear enough, i mean the fade in-out size, look at this line, look on the ends of it they "smaller" nd now look at mine line it s the same size without changes, only bout opacity. 
[IMG]http://media.smashingmagazine.com/wp-content/uploads/images/photoshop-brushes/control-pen-pressure.gif[/IMG]

I m now installing the newest version of wine.

---

### Post by Favux on 2011-08-04
OK, I see what you're asking.  In the tool palette when you've selected the brush or whatever click on the little black triangle in front of Brush Dynamics and for Pressure check the Size box.

---

### Post by ale.junuzovic on 2011-08-04
> **Favux said:**
> OK, I see what you're asking.  In the tool palette when you've selected the brush or whatever click on the little black triangle in front of Brush Dynamics and for Pressure check the Size box.

thnx bud, gimp works perfectly. 

But i m a digital painter i need photoshop, and the pen pressure is the most important part of it to me. 

btw installed newest wine, no changes. Pen pressure (no yellow triangle under dynamics brush settings) in Photoshop still doesnt work.

---

### Post by 23dornot23d on 2011-08-04
It might be worth taking a look here [**LINK**]("http://code.google.com/p/mypaintatelier/downloads/list")

Tutorial for setting up the brushes ...... [first one]("http://code.google.com/p/mypaintatelier/downloads/detail?name=brushes%20in%20mypaint%201.wmv&can=2&q=") videos and different brushes for My Paint ...... 

its 60 meg download ..... so no small download ... and is in English ...

______________________________________

I hear what you are saying - you are probably used to the package you have ....

But it is worth checking this out ..... too ...... as it runs natively so it should be more responsive to use ;)

---

### Post by Favux on 2011-08-04
23dornot23d beat me to the punch.  I was going to say there are a bazillion brushes etc. for MyPaint and you can edit them or better make a custom one if needed.

I haven't seen a simple instruction to set up Pressure in PhotoShop 5 with Wine yet.  So here are some instructional links:
[http://wiki.winehq.org/TabletSupport](http://wiki.winehq.org/TabletSupport)
[http://www.winehq.org/documentation](http://www.winehq.org/documentation)
[http://www.youtube.com/watch?v=1ZnCcJuQLwY](http://www.youtube.com/watch?v=1ZnCcJuQLwY)

Doing a search on the WineHQ bugzilla page:
[http://bugs.winehq.org/](http://bugs.winehq.org/)
brings up:
[http://bugs.winehq.org/buglist.cgi?quicksearch=pressure](http://bugs.winehq.org/buglist.cgi?quicksearch=pressure)
[http://bugs.winehq.org/show_bug.cgi?id=23947](http://bugs.winehq.org/show_bug.cgi?id=23947)

I don't know if CodeWeavers CrossOver (the paid version of Wine) has pressure for tablets or not.

---

### Post by ale.junuzovic on 2011-08-05
Favux, will it change something if i say that "MacroKey Manager" is used on Windows to make the Pen Pressure work. 

Yes myPaint is looking good, but without this Feature in photoshop im forced to use Windows. Still, will try to find something till i decide such stupid step.

---

### Post by ale.junuzovic on 2011-08-05
UPDATE: Pen Presure **works** in Photoshop CS2 with Wine!

@Faver So this is a clear Photoshop CS5 software issue right? I using the Installer (350 MB) from this youtube Video (link under descb.) [http://www.youtube.com/watch?v=1ZnCcJuQLwY](http://www.youtube.com/watch?v=1ZnCcJuQLwY)

I also tryed to "copy" Photoshop but didnt worked, so i have to use this. Strange i feel that i could work.

---

### Post by CGwebprog on 2011-12-18
I was very glad to find this thread and forum.  I'm not completely new to linux (or ubuntu), but I'm having trouble getting my pentablet to function correctly.  It's working, for the most part, with GIMP, MyPaint, and InkScape.  The only problem is that when using it in GIMP, I get these weird "fly-out" lines that radiate outward in one direction, beginning from where I place the pen tip on the "canvas" and go to the end of the canvas.  I'm not sure if has something to do with a setting in the device properties, or what.  I touch the canvas, and a line flies across the canvas.  Any help would be appreciated.  And thanks for the help already given...:D

---

### Post by Favux on 2011-12-18
Hi CGwebprog,

Welcome to Ubuntu forums!

I'm going to guess you are using Oneiric (11.10).  That has a known bug that affects Gimp, or at least is most obvious in Gimp because of Gimp's history buffer.  See this Launchpad bug report:  [https://bugs.launchpad.net/ubuntu/+source/gimp/+bug/863154](https://bugs.launchpad.net/ubuntu/+source/gimp/+bug/863154)  Feel free to post on it or at least register that you're affected.

The work around is to use Alexia's patch applied to the default Gimp, i.e. use this PPA:  [https://launchpad.net/~aapo-rantalainen/+archive/gimp26-noghostline](https://launchpad.net/~aapo-rantalainen/+archive/gimp26-noghostline)  That should do the trick for you.

---

### Post by CGwebprog on 2011-12-18
Hey Favux.  Thanks for the help.  I used Fedora for about a semester in undergrad, and I haven't used Linux much since then (about 4 years ago).  But, I just get more and more irritated with Windows that I'm entertaining a full change over to Ubuntu Studio (since I'm an artist and web developer...that's where the handle comes from...CGwebprog="Coast Guard web programmer").  I was so freakin' happy when I finally got my pen tablet to work that I got a little irritated when I saw that bug.  I'm glad someone else has identified it though.  I'll check out the patches and see how it works out.  Thanks for the help again.  I'm sure I'll see you all around.

---

