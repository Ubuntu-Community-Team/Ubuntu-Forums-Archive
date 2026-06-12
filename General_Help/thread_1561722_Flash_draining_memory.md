---
title: "Flash draining memory"
date: 2010-08-26
forum: General Help
---

### Post by pablito420 on 2010-08-26
hi guys

ok here goes

im prtty much a newbie here and with ubuntu.  i have 2 problems neither  of which can  ifind a resolution to.

1) i cant follow links from my email (Evolution) error message is:

Failed to execute child process "/usr/lib/chromium-browser/chromium-browser" (No such file or directory)

more importantly i have an issue with flash - i see that i am not alone but i cant find anyone with the same issue, namely that if i run say for example person.com or youtube etc the more cams or videos i open the slower it gets - to the point where the comp is whirring away and all the memory is used up crashing firefox.

i can rectify this by closing all firefox windows and going to the system monitor and ending the following processes

firefox-bin
plugin container

it seems that the more flash requests i make it loads up with these items but doesnt close them when i close the flash windows creating a massive memory drain

no idea how to move forward - any ideas?

cheers

ps its ubuntu 10.04 and the latest flash plugin downloaded as per ubuntu instructions

---

### Post by lovinglinux on 2010-08-26
Unfortunately, is the nature of the beast. Flash uses too much CPU in Linux.

You can try a few things from [Flash Optimization](http://firefox-tutorials.blogspot.com/2010/05/flash-optimization.html). Also make sure you have the latest flash version from adobe and not gnash or swfdec.

Get [FLASH-AID](https://addons.mozilla.org/en-US/firefox/addon/161939/), an extension to remove conflicting flash plugins and install the proper version according to your browser architecture.

For YouTube I recommend my extension [FlashVideoReplacer]("https://addons.mozilla.org/en-US/firefox/addon/161869/").

They are both developed by me.

---

### Post by no2498 on 2010-08-26
write down your settings so if this does not help you can set them back
this is if loveing linux did not help

5.1.&#8195;The video is sluggish/has a slow response. What can I do?


      You may have set "ximagesink" ("X Window System (No Xv)") as video-output.
      This means, that your cpu is doing all the work. Change it to "xvimagesink"
      ("X Window System (X11/XShm/Xv)") in order to let your graphics card do the work.
    


      To change the settings, run "gstreamer-properties", click the Video tab
      and change the appropriate settings.

---

### Post by lovinglinux on 2010-08-26
> **no2498 said:**
> write down your settings so if this does not help you can set them back
this is if loveing linux did not help

5.1.&#8195;The video is sluggish/has a slow response. What can I do?


      You may have set "ximagesink" ("X Window System (No Xv)") as video-output.
      This means, that your cpu is doing all the work. Change it to "xvimagesink"
      ("X Window System (X11/XShm/Xv)") in order to let your graphics card do the work.
    


      To change the settings, run "gstreamer-properties", click the Video tab
      and change the appropriate settings.

Flash doesn't use xv, that's why it uses too much CPU.

---

### Post by no2498 on 2010-08-27
it works for me is the best i can tell you
if i dont set like that i cant play any video's in totem
im on 804 had to get grease monkey for fire fox
i look in htop an see fire fox uses operas settings

---

