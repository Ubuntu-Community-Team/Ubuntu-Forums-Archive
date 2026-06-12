---
title: "I cannot see the minimize - restore - close icons on top"
date: 2010-09-18
forum: General Help
---

### Post by navinbht13 on 2010-09-18
Hi:
I firstly installed compiz packages for the effects. After installation my minimize,restore and close icon has lost.
Then I removed if by typing  _*compiz --remove*_ . I got my lost icon. But again when I tried to use the visual effect Extra  the minimize, maximize and close icon got lost . If I don't use Extra visual effect the icons are restored. Now how can I use the Extra Visual effect and compiz without the removable of minimize, maximize and close icon.
Thanks

---

### Post by 3dgard on 2010-09-19
Try this after you enable compiz and visual extra effects:

Press Alt+F2 and enter: 

```
gconf-editor
```

Navigate to apps/metacity/general and double click on "button_layout" and enter thin on the window that pops up:

```
menu:minimize,maximize,close
```

Press ok and hopefully it fixes your problem.

---

### Post by garvinrick4 on 2010-09-19
You know a while back I used to get that problem and I think I would just System/Preferences to Appearance to visual effects tab and switch it back and forth a 
couple of times and then it would say looking for driver or something close and then buttons would
be back to normal. I did not get into it anymore because problem with compiz and button layout seem to have gone away a version or two back for me.
The Configuration Manager has got to be the way to go but it just brought back a silly little fix that worked for me.

---

### Post by navinbht13 on 2010-09-19
> **3dgard said:**
> Try this after you enable compiz and visual extra effects:

Press Alt+F2 and enter: 

```
gconf-editor
```

Navigate to apps/metacity/general and double click on "button_layout" and enter thin on the window that pops up:

```
menu:minimize,maximize,close
```

Press ok and hopefully it fixes your problem.
gconf-editor doesn't work to restore the minimize, maximize and close icon.

---

### Post by navinbht13 on 2010-09-19
> **navinbht13 said:**
> gconf-editor doesn't work to restore the minimize, maximize and close icon.
I did it after enabling compiz and visual effect but didn't came.
My Appearance Preferences dialog stopped working it doesn' t closed when I used extra visual effect

---

