---
title: "Panels transparency"
date: 2011-02-24
forum: General Help
---

### Post by cfrancoec on 2011-02-24
[CENTER]Hello people
My problem is this one:

[IMG]http://ff.9.je/?di=0129857942114[/IMG]

If i put a background image on the panel its cutted out, and "Applications" "Places" and "Sytem" The sistray and everything isn't clear doesn't change

I have reseted all the preferences, the colours, compiz, etcetera
But, keeps like that

Also i  edited the gtkrc and reseted settings but, keeps like that :(

Thankyou
cfrancoec
[/CENTER]

---

### Post by Frogs Hair on 2011-02-24
One way to do this open Take Screenshot  and choose and check select area to grab . Take a screensot of the background the width of the screen and about as thick as the panel and save to a folder.

Right click the panel and choose properties > background tab > check the box for background image.
Select the box below and navigate to the folder with  the screenshot and select open.

Now the panel image you made will appear as the panel and your applet icons will look right. 
I just tried this 15 minutes ago.

To get the panel to match on a complex wallpaper the screen shot  needs to be taken from the area it is to be used . You may have to use auto hide to take a screenshot of the very top or bottom.

---

### Post by wiggly81 on 2011-02-24
if you copy your stripy image to the theme directory and give it the same name as your theme has for the file, would be...

sudo cp stripy.png /usr/share/themes/Ambiance/gtk2.0/apps/img/panel.png

if you where using the Ambiance theme.

after doing that reboot and it should fill the pannel..

Hope this gives you help

---

### Post by Krytarik on 2011-02-24
If the panels look right depends on how carefully the used theme is crafted, but even with the best crafted one there may be some items which simply don't follow the rules.

And +1 for the way *wiggly81* described, should bring you near perfection, at least with intransparent backgrounds.

But without reboot, just select another theme and then reselect your one, and backup the original panel-bg before.

---

