---
title: "left &lt;ctrl&gt; key stopped working on keyboard"
date: 2009-08-24
forum: General Help
---

### Post by driven1 on 2009-08-24
The left <ctrl> key stopped working on my keyboard after I was playing around with Virtualbox. I have since reinstalled 9.04 (but not Virtualbox) due to unrelated issues without fixing the problem. My home folder remained intact from before though, so I assume there is a preference file in there somewhere controlling this. Anyone know what I can do to resolve this. I tried going into the preferences menus and setting keys, but that didn't help. My muscle memory is to always use the left key, so I want to fix this issue. Thanks for any guidance you can provide.

---

### Post by the_one(2) on 2009-08-25
I have the same issue. I haven't changed anything that i can think of. This is really annoying! Please Help!

---

### Post by unutbu on 2009-08-25
Perhaps try this:
[http://ubuntuforums.org/showpost.php?p=7357596&postcount=2](http://ubuntuforums.org/showpost.php?p=7357596&postcount=2)

---

### Post by tgeer43 on 2009-08-25
driven1,

Are you sure that it's not a hardware problem with the key/keyboard itself? Try booting from a Live CD and running xev from the terminal. Press the left CTRL key and see what (if anything) it returns. Then do the same from your regular installation. My output looks like this:
```
KeyPress event, serial 35, synthetic NO, window 0x3800001,
    root 0x13c, subw 0x0, time 38453127, (-633,341), root:(198,370),
    state 0x10, keycode 37 (keysym 0xffe3, Control_L), same_screen YES,
    XLookupString gives 0 bytes: 
    XmbLookupString gives 0 bytes: 
    XFilterEvent returns: False

KeyRelease event, serial 35, synthetic NO, window 0x3800001,
    root 0x13c, subw 0x0, time 38453279, (-633,341), root:(198,370),
    state 0x14, keycode 37 (keysym 0xffe3, Control_L), same_screen YES,
    XLookupString gives 0 bytes: 
    XFilterEvent returns: False
```If everything looks OK then we can go from there. If it does turn out to be a hardware issue then you can remap it to a different key (the left Windows key, for instance). If worse come to worst, I just bought a Logitech wireless keyboard/mouse combo from Staples for only $15.00 and it works great.

tgeer

---

### Post by the_one(2) on 2009-08-25
It would seem that the problem is hardware related in my case at least. Thanks for the help anyway:)

---

### Post by driven1 on 2009-08-26
> **tgeer43 said:**
> driven1,

Are you sure that it's not a hardware problem with the key/keyboard itself? Try booting from a Live CD and running xev from the terminal. Press the left CTRL key and see what (if anything) it returns. Then do the same from your regular installation. My output looks like this:
```
KeyPress event, serial 35, synthetic NO, window 0x3800001,
    root 0x13c, subw 0x0, time 38453127, (-633,341), root:(198,370),
    state 0x10, keycode 37 (keysym 0xffe3, Control_L), same_screen YES,
    XLookupString gives 0 bytes: 
    XmbLookupString gives 0 bytes: 
    XFilterEvent returns: False

KeyRelease event, serial 35, synthetic NO, window 0x3800001,
    root 0x13c, subw 0x0, time 38453279, (-633,341), root:(198,370),
    state 0x14, keycode 37 (keysym 0xffe3, Control_L), same_screen YES,
    XLookupString gives 0 bytes: 
    XFilterEvent returns: False
```If everything looks OK then we can go from there. If it does turn out to be a hardware issue then you can remap it to a different key (the left Windows key, for instance). If worse come to worst, I just bought a Logitech wireless keyboard/mouse combo from Staples for only $15.00 and it works great.

tgeer

Thanks for the tip. It was hard for me to imagine that the keyboard failed like that while I was using it, but apparently it did. I ran xev while running the Live CD, and sure enough, the fault followed.

---

