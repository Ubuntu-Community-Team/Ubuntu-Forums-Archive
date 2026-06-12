---
title: "IBM Thinkpad X61 Tablet screen rotation buton as ctrl"
date: 2009-10-19
forum: General Help
---

### Post by Ditschi on 2009-10-19
Hi

My Tablet Pc has a button to rotate the screen (under windws).

The bttons keycode is 199.

I want to set this button to act like a control button because it wold be useful to have a ctrl button in tablet mode.
Also i'd like to set shortcodes to rotate the streen (ctrl + up/down/left/right)

Can someone help??

---

### Post by Favux on 2009-10-19
Hi Ditschi,

Welcome to Ubuntu Forums!

You forgot to mention what version of Ubuntu you are using.  A good resource for the Thinkpads is the thinkwiki.  And for your X61t in particular:  [http://www.thinkwiki.org/wiki/Category:X61_Tablet](http://www.thinkwiki.org/wiki/Category:X61_Tablet)  It should have the answers to most of your questions.

If you are using Jaunty you might want to see:  [https://help.ubuntu.com/community/X61T](https://help.ubuntu.com/community/X61T)

Hope this helps.

---

### Post by Ditschi on 2009-10-19
Hi 

Yes I'm useing Jaunty and already read those two Articles ...

I changed from gentoo to ubuntu so i knew thinkwiki before :)

in the other article i got the idea to set the keycode of the rotate-button to the same as my left ctrl key.. but that didnt worked ... ```
setkeycodes 199 37
```

i think you can't set a keycode for two different keys...  or ???

I want the "rotate" button to act like an ctrl key.

---

### Post by Favux on 2009-10-19
Hi Ditschi,

That's correct.  You can only set a keycode for one key.  You should be able to bind the rotate button to act like a ctrl key.  A very brief discussion of key binding is in this Rotation HOW TO:  [http://ubuntuforums.org/showthread.php?p=6274392](http://ubuntuforums.org/showthread.php?p=6274392)  under "let's get down to rotating".

---

### Post by Ditschi on 2009-10-20
Hi

I read the thread you posted several times but i Have still no idea how to make teh rotate button to act lice a ctrl key :(

Can change the name to Control_L??

output of xev:
when rotate button is pressed
```
KeyRelease event, serial 35, synthetic NO, window 0x3c00001,
    root 0xaa, subw 0x0, time 1287363, (208,-4), root:(877,46),
    state 0x0, keycode 199 (keysym 0x0, NoSymbol), same_screen YES,
    XLookupString gives 0 bytes: 
    XFilterEvent returns: False
```

when ctrl is pressed
```
KeyRelease event, serial 35, synthetic NO, window 0x3c00001,
    root 0xaa, subw 0x0, time 1285025, (208,-4), root:(877,46),
    state 0x4, keycode 37 (keysym 0xffe3, Control_L), same_screen YES,
    XLookupString gives 0 bytes: 
    XFilterEvent returns: False
```


------

> In X11, keysym numbers are used to represent the symbols visible on the keycaps of a keyboard. They represent either characters or function keys.
found on [http://www.x.org/wiki/KeySyms](http://www.x.org/wiki/KeySyms)

One step cold be to set the rotate-button as function key... but HOW??

thanks for your help

---

### Post by Ditschi on 2009-10-20
first sorry for double posting

I might found something helpful:


I have the Arrow keys on my keybord AND a button below my display wich acts like the arrow keys depending on, if its pressed up, down, left or right.

The xev output of the two up buttons is :

Keybord:```
KeyPress event, serial 35, synthetic NO, window 0x3c00001,
    root 0xaa, subw 0x0, time 1565985, (182,290), root:(851,340),
    state 0x0, keycode 111 (keysym 0xff52, Up), same_screen YES,
    XLookupString gives 0 bytes: 
    XmbLookupString gives 0 bytes: 
    XFilterEvent returns: False

KeyRelease event, serial 35, synthetic NO, window 0x3c00001,
    root 0xaa, subw 0x0, time 1566091, (182,290), root:(851,340),
    state 0x0, keycode 111 (keysym 0xff52, Up), same_screen YES,
    XLookupString gives 0 bytes: 
    XFilterEvent returns: False
```

Its the same... 
can I tranfsfer tihis to the ctrl problem ??

Button
```
KeyPress event, serial 35, synthetic NO, window 0x3c00001,
    root 0xaa, subw 0x0, time 1567949, (182,290), root:(851,340),
    state 0x0, keycode 111 (keysym 0xff52, Up), same_screen YES,
    XLookupString gives 0 bytes: 
    XmbLookupString gives 0 bytes: 
    XFilterEvent returns: False

KeyRelease event, serial 35, synthetic NO, window 0x3c00001,
    root 0xaa, subw 0x0, time 1568144, (182,290), root:(851,340),
    state 0x0, keycode 111 (keysym 0xff52, Up), same_screen YES,
    XLookupString gives 0 bytes: 
    XFilterEvent returns: False
```

---

### Post by P4man on 2009-10-20
Maybe this works 
> xmodmap -e 'keycode 111=Control_L'

More info:
[http://www.xfree86.org/4.0/xmodmap.1.html](http://www.xfree86.org/4.0/xmodmap.1.html)

---

### Post by Ditschi on 2009-10-20
Hi 

now the output whwn the rotate key is pressed ..
```
KeyPress event, serial 35, synthetic NO, window 0x3c00001,
    root 0xaa, subw 0x0, time 6178639, (160,-16), root:(824,34),
    state 0x0, keycode 199 (keysym 0xffe3, Control_L), same_screen YES,
    XKeysymToKeycode returns keycode: 37
    XLookupString gives 0 bytes: 
    XmbLookupString gives 0 bytes: 
    XFilterEvent returns: False

KeyRelease event, serial 35, synthetic NO, window 0x3c00001,
    root 0xaa, subw 0x0, time 6178789, (160,-16), root:(824,34),
    state 0x0, keycode 199 (keysym 0xffe3, Control_L), same_screen YES,
    XKeysymToKeycode returns keycode: 37
    XLookupString gives 0 bytes: 
    XFilterEvent returns: False

```

but it still don't acts like a ctrl key (copy, paste ... doesn't work)

the outtput of xmodmap -pk
```
There are 7 KeySyms per KeyCode; KeyCodes range from 8 to 255.

    KeyCode    Keysym (Keysym)    ...
    Value      Value   (Name)     ...
...
 
     37        0xffe3 (Control_L)    0x0000 (NoSymbol)    0xffe3 (Control_L)    0x0000 (NoSymbol)    0xffe3 (Control_L)    

....

     
    197        
    198        
    199        0xffe3 (Control_L)    
    200        

   ...
   
```

Keycode 37 is the crtl key, 199 is the rotate button...

why is there  0xffe3 (Control_L)    0x0000 (NoSymbol)  multiple times (ctrl key)?
might that be the problem??

---

### Post by Ditschi on 2009-10-26
No Ideas ??ß

---

