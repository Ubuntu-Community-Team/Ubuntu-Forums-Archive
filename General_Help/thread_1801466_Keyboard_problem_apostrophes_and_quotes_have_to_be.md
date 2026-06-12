---
title: "Keyboard problem: apostrophes and quotes have to be double keyed"
date: 2011-07-10
forum: General Help
---

### Post by bliffle on 2011-07-10
11.04 requires that I double strike apostrophes and quotes or else it displays a special character on the screen. I suspect that somehow I got the wrong keyboard configuration, but I don know how to determine the correct one.

---

### Post by enimeizoo on 2011-07-12
I'm not familiar with gnome/unity settings, but I think you can fix this with xmodmap and xev.

```
xmodmap -pke 
```Will display your keyboard mapping in a way that it can be fed back to xmodmap to be applied. (Not sure this sentence is understandable, I don't speak english fluently yet)

```
xmodmap -pke > xmodmap
```Will output the result in a file that you can edit.

You will need the keysym names for apostrophes and quotes.
```
" = quotedbl
' = apostrophe
```

---

### Post by bliffle on 2011-07-16
Great! I found the following line in ´xmodmap´, and it&#347; the only one with those strings:

```
keycode  48 = dead_acute dead_diaeresis dead_acute dead_diaeresis apostrophe quotedbl
```

But I don know what it means, or how to get what I want.

---

### Post by enimeizoo on 2011-07-17
Well, do you use this key to get them? The apostrophe and quotedbl, I mean. I ask, because with this key, you have to press alt_gr+key for apostrophe, and alt_gr+shift+key for quotedbl. I don't know what keyboard you use, but it is not a common way to get these symbols :P
Actually, if it is the right key, it should work just fine, and I wouldn't know how to fix.


You might have to look for another key. The one(s) you use to get your apostrophes and quotedbl. To get the keycode, you can run 'xev'. It will pop a little white window. Then press your key(s), and you should see something like that in the terminal :
```

KeyPress event, serial 35, synthetic NO, window 0x5000001,
    root 0xa8, subw 0x0, time 10700092, (620,524), root:(622,547),
    state 0x10,** [COLOR=Red]keycode 12[/COLOR] **(keysym 0x22, quotedbl), same_screen YES,
    XLookupString gives 1 bytes: (22) """
    XmbLookupString gives 1 bytes: (22) """
    XFilterEvent returns: False

KeyRelease event, serial 35, synthetic NO, window 0x5000001,
    root 0xa8, subw 0x0, time 10700188, (620,524), root:(622,547),
    state 0x10, keycode 12 (keysym 0x22, quotedbl), same_screen YES,
    XLookupString gives 1 bytes: (22) """
    XFilterEvent returns: False

KeyPress event, serial 35, synthetic NO, window 0x5000001,
    root 0xa8, subw 0x0, time 10700420, (620,524), root:(622,547),
    state 0x10, keycode 13 (keysym 0x27, apostrophe), same_screen YES,
    XLookupString gives 1 bytes: (27) "'"
    XmbLookupString gives 1 bytes: (27) "'"
    XFilterEvent returns: False

KeyRelease event, serial 35, synthetic NO, window 0x5000001,
    root 0xa8, subw 0x0, time 10700500, (620,524), root:(622,547),
    state 0x10, keycode 13 (keysym 0x27, apostrophe), same_screen YES,
    XLookupString gives 1 bytes: (27) "'"
    XFilterEvent returns: False


```The key(s) you are looking for have probably keysyms with the 'dead' prefix associated to it. 

Here is how the xmodmap lines work :
keycode XX = 1 2 3 4 5 6

That means that when you press the key, with no modifier, you get a 1. With shift, you get a 2. With alt_gr, you get a 5. And with shift+alt_gr you get a 6.
Actually, I still don't know how to get the 3 and 4 but that should be possible. (if you find out, tell me :P )

To apply a change, type in a terminal 
```
xmodmap -e "keycode XX = 1 2 3 4 5 6"
```It will be lost on reboot. 
If you are sure about your changes, create a file named ".Xmodmap" in your home directory and put in it the changes you want. It should look like :
```
 
keycode XX = 1 2 3 4 5 6
keycode YY= a z e r t y 

```Where XX and YY are the actual codes of the keys you want to change, and 1, 2, 3, 4, 5, 6, a, z,  e, r, t, y are the keysyms you want in the right order. Just like any line you get with xmodmap -pke.
The file will only be loaded on reboot (you will probably be shown a dilkog, asking if you want to load it or not), but you can manually load it :
```
xmodmap .Xmodmap
```

---

### Post by szal on 2011-07-17
> **bliffle said:**
> 11.04 requires that I double strike apostrophes and quotes or else it displays a special character on the screen.
In that case you’re not talking about apostrophes and quotes, but about accents.

Besides, knowing what keymap you intended to use couldn’t hurt either.

---

