---
title: "Dash and Unity Behavior in 11.10"
date: 2011-10-14
forum: General Help
---

### Post by rpisharody on 2011-10-14
Hi, 

I upgraded from 11.04 yesterday and found that when my application windows are maximized(say firefox or thunderbird), whenever I hi the Super key, the dash shows up behind the window.

The window controls of the dash can be seen in the title bar, but the dash itself is not being overlaid above the window. 

Also, when I move my pointer to the edge of the screen, the unity bar which previously used to appear on top of all windows now appear behind my application window.

Any idea on how to fix it ?

Thanks

---

### Post by effenberg0x0 on 2011-10-14
There's a workaround. In CompizConfig-Settings-Manager, go to the "Window Rules" plugin. At the line labeled "ABOVE", add this:

```
(Class=launcher | name=launcher | Class=Dash | name=Dash)
```Restart your session.
The Dash and Launcher will always be above other windows from now on.
It will fail eventually, when compiz fails, but most of the time it will work

Regards,
Effenberg

PS:

---

