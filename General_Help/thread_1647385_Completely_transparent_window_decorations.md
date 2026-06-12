---
title: "Completely transparent window decorations"
date: 2010-12-17
forum: General Help
---

### Post by hawthornso23 on 2010-12-17
My fglrx driver wasn't working right - crashing out wine and stopping doom3 from loading. So I completely wiped it and installed the latest version from ATI, and indeed that seems to have fixed my issues. However an annoying problem has arisen as a result.

In compiz my window decorations are now completely transparent - as in totally absolutely invisible! Note that the decorations are not missing, just invisible. I can grab the invisible top bar and drag the window around with it. I can maximise or minimise or close the window by clicking the completely invisible buttons (I have to guess where they are). But I can't see anything.

[LIST]
[*]Playing around with the settings in configuration editor ( apps > gwd ) makes no difference.
[*]Unselecting/reselecting window decorations in compiz control panel doesn't fix it.
[*]Nor does playing with  the settings for window decorations in compiz conrtol panel.
[*]window decorator is ```
 gtk-window-decorator --replace
```
[*]In metacity the decorations are just fine.
[*]Restarting compiz doesn't help.
[*]changing theme doesn't help.
[/LIST]
I could probably fix it by reverting the change to fglrx - although that may bring back the problems that made me want to update. It might be easier just to live with the problem. Does anyone have any suggestions?

---

### Post by 3Miro on 2010-12-17
Press Alt + F2 and then type:
```
 gconf-editor 
```

This gives you more detailed settings fro Gnome. You should find the options for the decorator from there and adjust the transparency. It was in app -> something, but I don't remember the exact name of the option.

---

### Post by hawthornso23 on 2010-12-17
Thanks for that, but I already played with those settings to no avail. It turned out to be some kind of bizarre bug with the compiz reflections plugin. Disabling that plugin fixed the issue instantly.

---

