---
title: "Samsung syncmaster 2333HD dual screen/resolution problem"
date: 2010-01-22
forum: General Help
---

### Post by Michie4life on 2010-01-22
I have a problem with my two screens, a Medion 17/19 inch and a samsung syncmaster 2333HD. I want my samsung screen to be my main screen but he wont... And the maximum resolution is 1024 an not 1920x1080. anyone got a fix for this:confused:?

---

### Post by efflandt on 2010-01-22
Read [https://wiki.ubuntu.com/X/Config/Resolution](https://wiki.ubuntu.com/X/Config/Resolution) about testing and setting other resolutions.  But not sure how you switch which is primary.

My laptop defaulted to stretched 1024x768 when VGA connected to my HDTV, and the only widescreen mode greatly overscanned.  From that info, info in /var/log/Xor.0.log, and **man xrandr** to write a script for my laptop and put a launcher to the script on the desktop, so when it is connected to my HDTV I can just double click to use HDTV's native resolution and turn off the laptop display.

---

