---
title: "My delete key is now insert. HELP!!!"
date: 2011-05-22
forum: General Help
---

### Post by colobix on 2011-05-22
I have no idea how or why it happened.
How do I change it back?

---

### Post by kd7swh on 2011-05-22
Check this out:

[http://ubuntuforums.org/showthread.php?t=100590](http://ubuntuforums.org/showthread.php?t=100590)

---

### Post by CharlesA on 2011-05-22
Check your keyboard layout.

---

### Post by colobix on 2011-05-22
Thanks but that didn't help.
The layout is correct.
Also this happened yesterday I believe. THe key used to be DELETE but now works as insert. They key says both delete and insert though. So maybe I'm suppose to press a button or something to switch it back to delete. I don't know.

---

### Post by CharlesA on 2011-05-22
Hrm, is there a fn key on your keyboard?

---

### Post by colobix on 2011-05-22
> **CharlesA said:**
> Hrm, is there a fn key on your keyboard?

Yes. I messed around with it now but the fm key didnt do much.
I also learned that left ctl+DEL deletes the rest of the line.
doesnt help me much.
But right alt plus delete deletes only one letter, so that actually works incase I will not be able to solve this.

---

### Post by CharlesA on 2011-05-22
It sounds like the keyboard layout got messed up somehow, but you said it looked fine.

Maybe try booting from a livecd and seeing if the keyboard works the same way.

---

### Post by colobix on 2011-05-22
> **CharlesA said:**
> It sounds like the keyboard layout got messed up somehow, but you said it looked fine.

Maybe try booting from a livecd and seeing if the keyboard works the same way.

If this is a layout thing, how do I reset it?

---

### Post by CharlesA on 2011-05-22
> **colobix said:**
> If this is a layout thing, how do I reset it?
Not sure, You could compare it to the settings in Keyboard Layouts when booted from a livecd.

---

### Post by colobix on 2011-05-22
Thanks but I don't know how to do that.
SO when I boot into the live cd, what do I do then?

---

### Post by CharlesA on 2011-05-22
What version of Ubuntu are you using?

In 10.04, it's under:

System > Preferences > Keyboard > Layouts.

Not sure where it is in 11.04, tho.

---

### Post by colobix on 2011-05-22
I use 10.10. Yes it was layout under keyboard settings, but I have the same language there as I always had (Norwegian).
I can't delete the layout either.
EDIT  I don't think it is the layout. I Just changed it to danish and back to norwegian, and restarted. Same problem .

---

### Post by CharlesA on 2011-05-23
Did it do the same thing when you booted off the livecd?

---

### Post by colobix on 2011-05-23
yes.
SO there must be a key on the keyboard or something

---

### Post by CharlesA on 2011-05-23
> **colobix said:**
> yes.
SO there must be a key on the keyboard or something
Sure sounds like it.

Does the same thing happen if you hook up another keyboard?

---

### Post by enimeizoo on 2011-05-23
If you can't solve it with layouts, you could check xmodmap and xev. 

To have the delete key work normally, you could do like that : 
1) run xev in terminal. Everytime you hit a key, you should see an output like that :
```

KeyPress event, serial 33, synthetic NO, window 0x5a00001,
    root 0x9c, subw 0x0, time 7771468, (-228,556), root:(756,579),
    state 0x10, keycode 119 (keysym 0xffff, Delete), same_screen YES,
    XLookupString gives 1 bytes: (7f) ""
    XmbLookupString gives 1 bytes: (7f) ""
    XFilterEvent returns: False

KeyRelease event, serial 33, synthetic NO, window 0x5a00001,
    root 0x9c, subw 0x0, time 7771543, (-228,556), root:(756,579),
    state 0x10, keycode 119 (keysym 0xffff, Delete), same_screen YES,
    XLookupString gives 1 bytes: (7f) ""
    XFilterEvent returns: False

```
Hit the delete key and keep the keycode you get in mind. (Mine is 119)

2) to have that key work like a classic delete key, run :
```
xmodmap -e "keycode 119 = Delete NoSymbol Delete"
```Of course, replace 119 by the keycode you get from first step (it might be 119 as well, thought).

This will be lost on reboot, but you could run the second command from your .profile or something.

---

### Post by colobix on 2011-05-23
key code? how do I find that?
ANd I don't have a usb keyboard, so I can't test it with another keyboard.

---

### Post by enimeizoo on 2011-05-23
As I told you, you can find the keycode with xev.
Just run xev in a terminal.
```
xev
```This will display a window. Every event the windows gets (including keypress and keyrelease events) will be output in the terminal you used to run xev.
To get the keycode of you delete key, just press it while the xev window is open. On the third line, of the keypress event, you should see it.

```
KeyPress event, serial 33, synthetic NO, window 0x5a00001,
    root 0x9c, subw 0x0, time 7771468, (-228,556), root:(756,579),
    state 0x10, _**[COLOR=Red]keycode 119[/COLOR]**_ (keysym 0xffff, Delete), same_screen YES,
    XLookupString gives 1 bytes: (7f) ""
    XmbLookupString gives 1 bytes: (7f) ""
    XFilterEvent returns: False

KeyRelease event, serial 33, synthetic NO, window 0x5a00001,
    root 0x9c, subw 0x0, time 7771543, (-228,556), root:(756,579),
    state 0x10, [COLOR=Red]_**keycode 119**_[/COLOR] (keysym 0xffff, Delete), same_screen YES,
    XLookupString gives 1 bytes: (7f) ""
    XFilterEvent returns: False
```

If you have trouble with that, just send me the xev output when you press your key.

---

### Post by Petrolea on 2011-05-23
Since it happened just like that, it might also be a hardware problem (it's not as high possibility as software tho :P). But things like that do happen. Try cleaning the keyboard :)

---

### Post by colobix on 2011-05-23
I have no idea how, but I fixed it. I just tried different key combinations and stuff for a few minutes, and PRESTO! It works.
But thank you so much for your help, guys.
I really appreciate it.

---

