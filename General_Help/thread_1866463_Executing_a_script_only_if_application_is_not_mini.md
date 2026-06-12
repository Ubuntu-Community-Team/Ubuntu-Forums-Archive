---
title: "Executing a script only if application is not minimized"
date: 2011-10-21
forum: General Help
---

### Post by Vikrohan on 2011-10-21
Hi,

 In the power saving options I have set my display to dim after an idle time of 1 min. The downside of this is, while watching movies on vlc or youtube you have to move the mouse after a minute. This is especially irksome while watching late night movies !
 Something similar to this webcomic :- [http://xkcd.com/196/](http://xkcd.com/196/).

 I wrote a small script which checks whether vlc or opera(my preferred browser) is running, and jiggles the pointer after 45 sec. It works perfectly, however I want to extend its functionality.

 I now want the script to execute, only if vlc or opera is not minimized. I have tried using 'wmctrl', however there is no option in it to determine whether a window is minimized or not. Can you suggest anything which can be used to determine the status of the window (i.e. whether it is minimized,maximized etc) ?

---

### Post by hwttdz on 2011-10-21
I'm not 100% on this, but I think that minimized windows occur first in the list from "wmctrl -l", so perhaps if you were to check which line it occurred on and which line say your panel occurred on, if it occurs after your panel, it's maximized, before it's minimized?

---

### Post by erind on 2011-10-21
> **hwttdz said:**
> i'm not 100% on this, but i think that minimized windows occur first in the list from "wmctrl -l", so perhaps if you were to check which line it occurred on and which line say your panel occurred on, if it occurs after your panel, it's maximized, before it's minimized?
+1

> **vikrohan said:**
> i now want the script to execute, only if vlc or opera is not minimized. I have tried using 'wmctrl', however there is no option in it to determine whether a window is minimized or not. Can you suggest anything which can be used to determine the status of the window (i.e. Whether it is minimized,maximized etc) ?

Another possible way would be using **xwininfo**, where the important line is "**Map State:**". An example with firefox:

```
**# Firefox is maximized**

$ xwininfo -name "Ubuntu Start Page - Mozilla Firefox"

xwininfo: Window id: 0x4e000c4 "Ubuntu Start Page - Mozilla Firefox"

  Absolute upper-left X:  0
  Absolute upper-left Y:  53
  ...
  Save Under State: no
  [COLOR=Red]**Map State: IsViewable**[/COLOR]
  Override Redirect State: no
  Corners:  +0+53  -0+53  -0-24  +0-24
  -geometry 1280x723+0-24


**# Firefox is minimized**

$ xwininfo -name "Ubuntu Start Page - Mozilla Firefox"

xwininfo: Window id: 0x4e000c4 "Ubuntu Start Page - Mozilla Firefox"

  Absolute upper-left X:  0
  Absolute upper-left Y:  53
  ...
  Save Under State: no
  [COLOR=Red]**Map State: IsUnMapped**[/COLOR]
  Override Redirect State: no
  Corners:  +0+53  -0+53  -0-24  +0-24
  -geometry 1280x723+0-24

$ xwininfo -name "Ubuntu Start Page - Mozilla Firefox" | grep "Map State:"
  [COLOR=Red]Map State: IsUnMapped[/COLOR]
```You can find ** xdotool **very useful too.

[http://www.semicomplete.com/projects/xdotool/xdotool](http://www.semicomplete.com/projects/xdotool/xdotool)

---

### Post by Vikrohan on 2011-10-22
@erind

Thank you so much! xwininfo works perfectly !! :o:o

---

### Post by dcstar on 2011-10-22
> **Vikrohan said:**
> @erind

Thank you so much! xwininfo works perfectly !! :o:o

Then mark the thread as Solved.

---

