---
title: "twinview config: how to set two different size screen in same level?"
date: 2006-05-07
forum: General Help
---

### Post by newpants2003 on 2006-05-07
what shuold i do with the xorg.conf? is there any thing simalar like "RigtOf" to make the it think one screen is higher than the phycal way? 
im using 15 inch and 19 inch monitor. 
thanx for help.

---

### Post by Parkotron on 2006-05-08
See my post [here]("http://ubuntuforums.org/showthread.php?p=739513#post739513").

Basically, you can manually position your screens however you want, ignoring the "RightOf", "LeftOf", etc. properties.
[LIST=1]
[*]Set the resolution for your first monitor.
[*]Set the resolution for your second monitor.
[*]Set position of the top lefthand corner of the second screen relative to the top lefthand corner of the first screen. (Positive x is left and positive y is down.)
[*]The final result should look like WIDTH1xHEIGHT1,WIDTH2xHEIGHT2±HORIZONTALOFFSET±VERTICALOFFSET
[/LIST]
You can do some pretty funky stuff with this too, like defining parts of the screen to overlap like```
|-----------------|
|                 |
|                 |
|                 |
|        |--------+--------|
|        |        |        |
|        |        |        |
|--------+--------|        |
         |                 |
         |                 |
         |                 |
         |-----------------|
```Just playing around, I once set two monitors on top of one another and had them overlap by a little bit. I had the same panel shown on both monitors, at the bottom of one and at the top of the other.

Hope that helped.

---

### Post by newpants2003 on 2006-05-08
thanx a lot

---

