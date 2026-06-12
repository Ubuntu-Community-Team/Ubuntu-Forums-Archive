---
title: "xmodmap for DotA"
date: 2009-09-23
forum: General Help
---

### Post by Blade[ZA] on 2009-09-23
Greetings,

This is my very first post on these forums although i have used it for a few months now. I have managed to find solutions to all of my problems except for one. Back on Windows i used "AutoHotKey" to macro a couple buttons to my inventory keys, eg. Alt + Q = Numpad 7, and it worked wonders. For the life of me i can't seem to get AutoHotKey and Warcraft III to work together so I have done a lot of research and xmodmap seems to be the next best thing, but it is all way too confusing to me and I'm not 100% sure if what i need can be done. Even the slightest bit of help will make me happy. The following is what i want done:

Alt + Q = Numpad 7
Alt + W = Numpad 8
Alt + A = Numpad 4
Alt + S = Numpad 5
Alt + Z = Numpad 1
Alt + X = Numpad 2

Thanks in advance,
-Blade

---

### Post by I[AM]SMRT on 2010-05-10
> **'Blade[ZA] said:**
> Greetings,

This is my very first post on these forums although i have used it for a few months now. I have managed to find solutions to all of my problems except for one. Back on Windows i used "AutoHotKey" to macro a couple buttons to my inventory keys, eg. Alt + Q = Numpad 7, and it worked wonders. For the life of me i can't seem to get AutoHotKey and Warcraft III to work together so I have done a lot of research and xmodmap seems to be the next best thing, but it is all way too confusing to me and I'm not 100% sure if what i need can be done. Even the slightest bit of help will make me happy. The following is what i want done:

Alt + Q = Numpad 7
Alt + W = Numpad 8
Alt + A = Numpad 4
Alt + S = Numpad 5
Alt + Z = Numpad 1
Alt + X = Numpad 2

Thanks in advance,
-Blade
I know this is a bit late but I managed to map a few keys + modifier to numberpad keys ([http://www.in-ulm.de/~mascheck/X11/xmodmap.html](http://www.in-ulm.de/~mascheck/X11/xmodmap.html) and [http://wiki.archlinux.org/index.php/Xmodmap#Structure):](http://wiki.archlinux.org/index.php/Xmodmap#Structure):)

```
clear Lock          !Clear Caps_Lock modifier
clear Mod5                !Clear Mod5 (Mode_switch was originally mod5)
add lock = Mode_switch    !Assign Mode_switch to Caps_Lock MODIFIER
keycode 66 = 0xff7e       !Assign Mode_switch to Caps Lock KEY
keycode 24 = q Q 0xffb7 0xffb7
keycode 25 = w W 0xffb8 0xffb8
keycode 38 = a A 0xffb4 0xffb4
keycode 39 = s S 0xffb5 0xffb5
keycode 52 = z Z 0xffb1 0xffb1
keycode 53 = x X 0xffb2 0xffb2
```

It's all kinda moot though, it doesn't activate the inventory keys for me. When I hit enter in game and chat, typing "CapsLock+q", it outputs a 7 as expected but otherwise does nothing when I try to use items, unfortunately. I think wc3 uses its own keyboard map in game and when typing goes back to the system keyboard map, unfortunately.

---

### Post by Blade[ZA] on 2010-05-11
Good effort though. Since my post I've bought a new computer thats now capable of playing games on windows, before on my old PC it could only play games on Linux.

Peace,
Blade[ZA]

---

