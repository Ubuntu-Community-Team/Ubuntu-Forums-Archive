---
title: "Changing Key Function"
date: 2009-08-27
forum: General Help
---

### Post by hwttdz on 2009-08-27
I just wanted to change the function of the f12 key, namely I want to use it as an extended keypad.  I found
xmodmap -e "keycode 96 = ampersand"
mapped my f12 to the ampersand.  
I thought about putting it in the pause/break button (because I don't think that one does anything (I also couldn't figure out what f12 did)) which would have been
xmodmap -e "keycode 127 = ampersand"

Does anyone know what F12 or pause/break does, or why when doing 
xmodmap -pke
you see so many actions per key, I assume one is default and one is shift+key, what are the others? Thanks.

---

### Post by Johnny B on 2009-08-27
did you see this?
[https://help.ubuntu.com/community/KeyboardShortcuts]("https://help.ubuntu.com/community/KeyboardShortcuts")

---

### Post by Lostin60's on 2009-09-02
> **hwttdz said:**
> I just wanted to change the function of the f12 key, namely I want to use it as an extended keypad.  I found
xmodmap -e "keycode 96 = ampersand"
mapped my f12 to the ampersand.  
I thought about putting it in the pause/break button (because I don't think that one does anything (I also couldn't figure out what f12 did)) which would have been
xmodmap -e "keycode 127 = ampersand"

Does anyone know what F12 or pause/break does, or why when doing 
xmodmap -pke
you see so many actions per key, I assume one is default and one is shift+key, what are the others? Thanks.

From the xmodmap manual:
>  The first keysym is  used  when
               no  modifier  key  is pressed in conjunction with this key, the
               second with Shift, the third when the Mode_switch key  is  used
               with  this  key  and  the  fourth when both the Mode_switch and
               Shift keys are used.

Hope this helps.
[COLOR="White"]aa[/COLOR]

---

