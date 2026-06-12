---
title: "Need help with WineHQ please =/"
date: 2011-04-16
forum: General Help
---

### Post by TheOmnipotentPilot on 2011-04-16
So I installed wine and upon starting it the first time, I configured the settings, but when I opened wine, the virtual window of windows was too big for the actual window in ubuntu. (that probably makes no sense, please just see the picture below)

[IMG]http://img710.imageshack.us/img710/2043/wine.png[/IMG]

(Url, in case the image doesn't show: [http://img710.imageshack.us/i/wine.png/](http://img710.imageshack.us/i/wine.png/))

This made it impossible to do anything. I can't find out how to change the settings (lower the resolution?) so it will fit in the window... I'm also an ubuntu noob, so I can't find the folder that has all my settings in it... I need help! This is driving me crazy! 

Thanks!

---

### Post by Keypel on 2011-04-16
Can you get to Applications->Wine->Configure Wine and get to the graphics tab and uncheck "Emulate a virtual desktop?"

If you need help moving the window due to it's large size, "right click" the top border of the window you wish to move and select "move". Then use the arrow keys on your keyboard to move the window around and hit enter to finish your move.

Also, installing the restricted graphics driver might help, I can see from your screenshot that it is not installed. In the far upper right hand corner, in the notificaton area, click the icon of the pci card with the lock symbol over it.

---

### Post by earthpigg on 2011-04-16
i don't mess around with wine often, but if you want to simply restore the defautl settings and try fiddling with it over again from scratch:

```
rm -r ~/.wine
```

type yes and hit enter

wine is now restored to 'factory' defaults.

---

### Post by TheOmnipotentPilot on 2011-04-18
Ok, thanks guys! Problem solved :)

---

