---
title: "Top panel is gone?"
date: 2011-04-26
forum: General Help
---

### Post by The capitan on 2011-04-26
Hello and good morning,

I have strangely had kinda two network applets in my top panel but the one was sometimes kinda hidden. Last night it changed to the "User lock,login,session" applet?? They were side by side, like mirrored. But anyways right click delete/remove/explode.... whatever I did my WHOLE upper panel and everything in it is gone? 

                                                                     Thanks allllll


Edit:

with Ctrl+Alt+Backspace...

killall gnome-panel
Or try Alt + F2 and type in nm-applet and hit enter


[SOLVED]

gconftool --recursive-unset /apps/panelThis worked for me thanks for your time!

---

### Post by TeoBigusGeekus on 2011-04-26
If that was your only panel, then press Alt+F2. Give
```
gnome-panel
```
and press enter.

If, however, you still have your bottom panel, right click it and select add panel. You will have to reconfigure it of course.

---

### Post by Frogs Hair on 2011-04-26
I think you deleted your panel . Right click the top of the screen and select new panel.

Use alt+F2 and enter gnome-terminal in the box and select run. Enter this code to reset panel applets to default.```
gconftool --recursive-unset /apps/panel && killall gnome-panel
```

---

