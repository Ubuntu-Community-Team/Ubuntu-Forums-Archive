---
title: "Laptop's additional keys annoyance"
date: 2010-09-23
forum: General Help
---

### Post by felinoel on 2010-09-23
I just got this "Compaq Presario CQS2-210US Notebook" and it has additional keys along the left side of the keyboard right next to the main keys. I type without looking at my keyboard so feeling those extra keys makes me think they are the keys that would generally be on the far left, especially the control key, so I hold down what I think is the control key to find 42 calculators pop up... closing these is an annoyance to say the least.

Is there any way I can turn off those keys, or better yet turn this calculator key into another control key so when I absentmindedly use it I won't be confused as to why it isn't working?

---

### Post by pbrane on 2010-09-23
If you're using GNOME you should be able to change the key definitions in **System->Preferences->Keyboard Shortcuts**

---

### Post by bgugi on 2010-09-23
as pbrane said, you should check your gnome keyboard shortcuts to remove the shortcuts. after you've done that, in order to turn a key into a "control", you have to do a little more in-depth work. 

first, make sure the key isn't doing anything as it is. just press it, and make sure nothing happens before proceeding. now, in order to figure out what your computer wants to call that key, we use a command called "xev".

open a terminal, and simply type in "xev" then enter. you should see an odd looking window with various boxes. hit the key you're interested in converting, then close the window. you will see EVERY EVENT THIS WINDOW CAN NOTICE. that's a lot of information. when you hit the key, you should see something like the following (approximately):
```
KeyPress event, serial 33, synthetic NO, window 0x5800001,
    root 0xfd, subw 0x0, time 4435550, (766,339), root:(776,438),
    state 0x10, keycode 172 (keysym 0x1008ff14, XF86AudioPlay), same_screen YES,
    XLookupString gives 0 bytes: 
    XmbLookupString gives 0 bytes: 
    XFilterEvent returns: False

KeyRelease event, serial 33, synthetic NO, window 0x5800001,
    root 0xfd, subw 0x0, time 4435797, (766,339), root:(776,438),
    state 0x10, keycode 172 (keysym 0x1008ff14, XF86AudioPlay), same_screen YES,
    XLookupString gives 0 bytes: 
    XFilterEvent returns: False

```
while all of this information might be a little overwhelming at first, the main thing you're looking for is the name of the key... in my case it's "XF86AudioPlay". yours, i imagine, will likely be called something like "XF86Calculator" or something of that nature. now, in order to turn this key into a control, you need to use a command called xmodmap. be careful with this command, as you can really mess your keyboard up.

i'm going to keep using my "XF86AudioPlay" for the rest of this example, but you will need to need your keyname. in order to make that key a "control" i will issue the following command in a terminal:
```
xmodmap -e "add mod1 = XF86AudioPlay"
```
note the use of quotes, and that linux commands are CASE SENSITIVE... keep all the caps the same and you should be fine. after that, you should have a shiny new control key!

---

### Post by felinoel on 2010-09-23
> **pbrane said:**
> If you're using GNOME you should be able to change the key definitions in **System->Preferences->Keyboard Shortcuts**It won't let me remove the calculator being called up, so I just changed the shortcut to alt+7

---

### Post by felinoel on 2010-09-23
> **bgugi said:**
> i'm going to keep using my "XF86AudioPlay" for the rest of this example, but you will need to need your keyname. in order to make that key a "control" i will issue the following command in a terminal:
```
xmodmap -e "add mod1 = XF86AudioPlay"
```
note the use of quotes, and that linux commands are CASE SENSITIVE... keep all the caps the same and you should be fine. after that, you should have a shiny new control key!Hmmm, this seems to have turned it into an alt?

---

### Post by felinoel on 2010-09-29
> **felinoel said:**
> Hmmm, this seems to have turned it into an alt?Does anyone know the config for ctrl?

---

### Post by felinoel on 2010-10-01
> **felinoel said:**
> Does anyone know the config for ctrl?

 .

---

### Post by felinoel on 2010-10-05
> **felinoel said:**
> .

.

---

### Post by felinoel on 2010-10-09
> **felinoel said:**
> .

,

---

### Post by felinoel on 2010-10-14
> **felinoel said:**
> .

.

---

### Post by felinoel on 2011-02-20
> **felinoel said:**
> .

.

---

