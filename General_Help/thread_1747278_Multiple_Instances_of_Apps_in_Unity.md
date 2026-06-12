---
title: "Multiple Instances of Apps in Unity"
date: 2011-05-02
forum: General Help
---

### Post by daz4126 on 2011-05-02
Using more than one instance of the same app is a real pita in Unity.

If I have 3 (or more) pdf documents open in evince then there isn't a way to shift from one to the other using the mouse. Previously I had the windows on the taskbar and could click on the one I wanted. In Unity clicking on the evince icon on the launcher just brings ALL the instances of evince to the top - I still then have to shuffle the windows around to get the one I want.

I've been trying to get used to Unity over the last few days, so maybe I am just doing it wrong, but if not then maybe I should file a bug report?

cheers,

DAZ

---

### Post by zvacet on 2011-05-02
Try with super key +W and see if it works.

---

### Post by Peter09 on 2011-05-02
Using the mouse - double click on the icon in the launcher.

---

### Post by daz4126 on 2011-05-03
Thanks for the tips guys, but neither of them work.

Double clicking on the launcher icon does nothing.

Holding down super + W just puts numbers on the icons in the launcher.

This is a real problem with Unity - especially since it classes gmail as 'Chromium' and groups them together under the Chromium icon (even though I launched gmail using a different icon on the launcher)

Shall I report the bug?

DAZ

---

### Post by Peter09 on 2011-05-03
Sounds like a bug. Try firefox as an experiment, create several instances using super+shift+number.

See what happens with double click/Super+W

---

### Post by techunit on 2011-05-03
> **zvacet said:**
> Try with super key +W and see if it works.
It isn't super-W anymore it is super-S

try that now.

Hope this helps. This was one the problems I had with Unity but really the hotkeys make a bit more sense.

---

### Post by daz4126 on 2011-05-03
Thanks techunit.

Super s also does nothing. I think I might have changed some compiz settings that manage this - any idea how to get them back to the default install settings?

Also - what am I actually expecting to happen?

cheers,

DAZ

---

### Post by Peter09 on 2011-05-03
try doing (in a terminal)

```
unity --reset
```

---

### Post by daz4126 on 2011-05-03
@Peter09 - Thanks, that command is really useful. It would be good if the Unity config was kept separate from the compiz config.

It's all working now ... and I have to say that I like what happens when I double-click on an icon I am using. Just to note that super+S changes the workspace, super+W changes ALL windows, double clicking on an icon only shows windows for that app.

This makes Unity so much nicer for me.

I have one more related issue if anybody on here can help - [http://ubuntuforums.org/showthread.php?p=10763825#post10763825](http://ubuntuforums.org/showthread.php?p=10763825#post10763825)

Thanks again,

DAZ

---

