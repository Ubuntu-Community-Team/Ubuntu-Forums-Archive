---
title: "Desktop wallpaper changer"
date: 2010-05-08
forum: General Help
---

### Post by rmcellig on 2010-05-08
What Desktop wallpaper changer would you recommend for Ubuntu 10.04?

---

### Post by -humanaut- on 2010-05-08
What do you mean? I just use System - > Preferences - > Appearance

---

### Post by WorMzy on 2010-05-08
Right clicking on the desktop and choosing "Change Desktop Background" always works for me. ;D

---

### Post by bigsmitty64 on 2010-05-08
I just open a pic and set as background. If you have Compiz installed there is a wallpaper setting in that.

---

### Post by jerrrys on 2010-05-08
these are located in synaptic package manager

[ATTACH]156110[/ATTACH]

---

### Post by rmcellig on 2010-05-08
I was just wondering which changer would work best with 10.04. I just want something that will rotate pictures on my desktop.

---

### Post by TheNerdAL on 2010-05-08
> **rmcellig said:**
> I was just wondering which changer would work best with 10.04. I just want something that will rotate pictures on my desktop.

Drapes is good. 

[http://freshmeat.net/projects/drapes/](http://freshmeat.net/projects/drapes/)

Wallpapoz also. 

[http://wallpapoz.akbarhome.com/](http://wallpapoz.akbarhome.com/)

---

### Post by WorMzy on 2010-05-08
If you want an automatic rotating background, then I recommend that you make use of the standard wallpaper rotator. Create an XML file with the following content:

```
<background>
  <starttime>
    <year>2009</year>
    <month>08</month>
    <day>04</day>
    <hour>00</hour>
    <minute>00</minute>
    <second>00</second>
  </starttime>
<!-- This animation will start at midnight. -->
  <static>
    <duration>1795.0</duration>
    <file>/home/wormzy/Pictures/208-1920x1200.jpg</file>
  </static>
  <transition>
    <duration>5.0</duration>
    <from>/home/wormzy/Pictures/208-1920x1200.jpg</from>
    <to>/home/wormzy/Pictures/Background.jpg</to>
  </transition>
  <static>
    <duration>1795.0</duration>
    <file>/home/wormzy/Pictures/Background.jpg</file>
  </static>
  <transition>
    <duration>5.0</duration>
    <from>/home/wormzy/Pictures/Background.jpg</from>
    <to>/home/wormzy/Pictures/208-1920x1200.jpg</to>
  </transition>
</background>
```

Obviously change the images to whatever you want, and alter the transition duration, and add more image/transitions as you see fit. Then add the xml file as a background using the wallpaper management window that me and humanaut directed you to.

---

### Post by Ordes on 2010-05-08
Before Lucid i was using wallpaper-tray and was very happy with it.

Since Lucid i use wally. And it seems pretty solid...

---

### Post by false_chicken on 2010-05-08
I second wallpaper-tray

---

### Post by vikas153 on 2011-08-09
thanks a lot ....fo r a long time i was trying to find out how do we create group of wall papers......:guitar:

---

