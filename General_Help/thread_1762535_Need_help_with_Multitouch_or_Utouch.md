---
title: "Need help with Multitouch or Utouch"
date: 2011-05-19
forum: General Help
---

### Post by lumix on 2011-05-19
I've installed utouch through apt-get, but am having a hard time figuring out how to use it.  My screen basically only seems to use single-touch input, that acts pretty much just a like a one button mouse.

So how do I get multitouch to work in 11.04?  It doesn't have to be through utouch as as far as I'm concerned.  I don't even need the fanciness of pinch gestures, just being able to scroll without using the scrollbar would be great.

Thanks.

---

### Post by Gator809 on 2011-05-21
I have the same question/problem. My current PC is a Lenovo x201T. I believe when I tried kubuntu natty alpha it worked fine. Like the author stated it acts like a mouse.  I look at my hand but I see a finger, not a mouse. In win7 it says okay this is a finger. If it drags with two fingers I scroll. Otherwise I select text. If finger in whitespace I'll scroll. Unlike the mouse our fingers don't have wheels. :confused: Pinch to zoom doesn't work either. 
Goodnews is Pressure Sensitivity works under Xournal(a journaling software). 

I will gladly help in testing out new tablet / touch / inking / sketching features on this wonderful OS. These are features where market penetration would be most greatly affected. You know MS is working very hard on windows 8 to make it happen. Bill Gates was a heavy Tablet PC advocate and  created xp tablet pc edition. His dreams are coming to fruit now. There's no competition right now (x86,amd64). Ipads and Android tablets are for kids.
ubuntu
Imagine the increased productivity of a properly implemented touch OS for more powerful personal computers? Playing games such as wak a mole, time crisis, house of the dead. Increased efficiency in programming. Office suites. I know the ribbon is MS office's thing, but it provides a useful touch experience. Music productions is more intuitive. Imagine a virtual drum machine with a mouse. Schematic designs and CADing will be so much quicker. it's very annoying clicking here and there. It is also painfully slow because of the wrist movement vs shoulder movement. Ask any calligrapher, who's dexterity are usually above average. Everything to make it happen is hidden in different parts of ubuntu already also windows but that's another story. 
 My programming is poor because of inexperience, but I'd like to contribute with ideas, suggestions and testing.   What was the deal with the big unity utouch push anyways (pre Natty Final)?

---

### Post by lumix on 2011-05-23
Bump.

---

### Post by Favux on 2011-05-23
Hi lumix,

You haven't told us what touchscreen you have (the manufacturer) and whether it supports more than one finger touch (1FGT).  Nor the driver you are using.  See the [Ubuntu multi-touch wiki]("https://wiki.ubuntu.com/Multitouch/") for Hardware Support.  If you have a single touch eGalax touchscreen for example you won't be able to get multi-touch.  If it does support more than one finger then it depends on the driver.  For example a multi-finger touchscreen on the evdev X driver can use ginn (installed by default) and its wishes.xml for multi-touch.  The wiki will show you how.


Hi Gator809,

Your tablet PC should be running on the xf86-input-wacom driver, which is the Wacom X driver.  Gestures should be turned on by default and supplied through the Wacom driver.  Enter in a terminal:
```
xinput list
```
and
```
xsetwacom list
```
and post the outputs.  It would also help if you mentioned what release of Ubuntu you are using.  Natty also?

---

### Post by lumix on 2011-05-25
Sorry, I've posted about 18 other places on the web so I guess I'd run short on steam by the time I got to this one.

It is an eGalax screen, and does indeed support multi-touch.  The Multitouch wiki makes my eyes bleed, and I don't actually see any instructions or howto's in it.

As for the driver...what are my options?  How would I know what I'm using?

I apologize for the newbie-ness, I'm a mere IT professional of 20 years with only a comp-sci degree...so this stuff is all very confusing for me.

---

### Post by Favux on 2011-05-26
> As for the driver...what are my options? How would I know what I'm using?
Well if the touchscreen is supported by the kernel it should be showing up in *xinput list*.  Find the "device name" and using quotes enter in a terminal:
```
xinput list-props "device name"
```
That should list any X driver the device is on.
> I'm a mere IT professional of 20 years with only a comp-sci degree...
Great!  You should be able to figure this out better than me then.
> It is an eGalax screen, and does indeed support multi-touch. The Multitouch wiki makes my eyes bleed, and I don't actually see any instructions or howto's in it.
Ok, it might be good to run report.py in this Launchpad bug report:  [https://bugs.launchpad.net/utouch/+bug/736752](https://bugs.launchpad.net/utouch/+bug/736752)  to get some baseline information.

You might want to install mtview and see if however many fingers the screen supports are being picked up:  [http://ubuntuforums.org/showpost.php?p=10860815&postcount=119](http://ubuntuforums.org/showpost.php?p=10860815&postcount=119)

More Ubuntu multi-touch stuff, especially code, available here:  [https://launchpad.net/canonical-multitouch](https://launchpad.net/canonical-multitouch)

And the ENAC site has useful information:  [http://lii-enac.fr/en/projects/shareit/](http://lii-enac.fr/en/projects/shareit/)

---

### Post by lumix on 2011-05-29
mtdev-test shows all kinds of data, but once again...is there any documentation to actually interpret it?  Silly question...I digress

mtview, on the other hand, tells me that /dev/input/event7 (yes, checked for eGalax mapping to this) is unsupported.  But I'm not buying that this is simply a dead end.  It also says it can't "grab" /dev/input/mouse0 (also the eGalax).  So I need to check the documentation to see what that means.  Oh wait, I can't...

In any case, I appreciate your help with this.

---

