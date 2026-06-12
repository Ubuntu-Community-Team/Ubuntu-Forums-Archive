---
title: "compose key in Karmic"
date: 2009-11-03
forum: General Help
---

### Post by potiphera on 2009-11-03
I just did a fresh installation of Karmic (not an upgrade) on my desktop computer.  I had previously used Gutsy and Hardy on the same computer with the same keyboard, and I used the right and left Windows keys as compose keys.  Now I can set other keys as compose keys in System>Preferences>Keyboard and they work fine, but the Windows keys won't work when I check them on the list.  How do I fix this?  Thanks!

---

### Post by potiphera on 2009-11-04
(bump)

---

### Post by dvandok on 2009-11-04
H'm, this is a 'me too' i think (see [http://ubuntuforums.org/showthread.php?t=1313941](http://ubuntuforums.org/showthread.php?t=1313941))
 although I'm using a MacBook and I have a propellor key instead of a Win key ;-)

Could you test this with xev? Run it from a terminal and observe the keysyms flashing by.

---

### Post by potiphera on 2009-11-04
> **dvandok said:**
> Could you test this with xev? Run it from a terminal and observe the keysyms flashing by.Here's what happens when I press and release the right Windows key, and then the left one:
```
KeyPress event, serial 30, synthetic NO, window 0x4600001,
    root 0xfc, subw 0x0, time 128478125, (125,48), root:(138,169),
    state 0x10, keycode 134 (keysym 0xff20, Multi_key), same_screen YES,
    XKeysymToKeycode returns keycode: 133
    XLookupString gives 0 bytes: 
    XmbLookupString gives 0 bytes: 
    XFilterEvent returns: True

KeyRelease event, serial 33, synthetic NO, window 0x4600001,
    root 0xfc, subw 0x0, time 128485080, (125,48), root:(138,169),
    state 0x50, keycode 134 (keysym 0xff20, Multi_key), same_screen YES,
    XKeysymToKeycode returns keycode: 133
    XLookupString gives 0 bytes: 
    XFilterEvent returns: False

KeyPress event, serial 33, synthetic NO, window 0x4600001,
    root 0xfc, subw 0x0, time 128489194, (125,48), root:(138,169),
    state 0x10, keycode 133 (keysym 0xff20, Multi_key), same_screen YES,
    XLookupString gives 0 bytes: 
    XmbLookupString gives 0 bytes: 
    XFilterEvent returns: True

KeyRelease event, serial 33, synthetic NO, window 0x4600001,
    root 0xfc, subw 0x0, time 128496152, (125,48), root:(138,169),
    state 0x50, keycode 133 (keysym 0xff20, Multi_key), same_screen YES,
    XLookupString gives 0 bytes: 
    XFilterEvent returns: False
```

---

### Post by dvandok on 2009-11-05
Seems to be ok. One more test: could you try typing something in xterm, or xedit, to see if it works? For me this works. I'm beginning to suspect that the win key is intercepted (in gnome? GTK?) before you can finish your composition. If it works for you in xterm, I'll file a bug.

---

### Post by potiphera on 2009-11-05
Yeah, it works for me in xedit.

(Although the compose key sequences and availability of characters have been different for me in each version of Ubuntu I've used -- I've noticed different behavior for å, ð, þ, and œ between Hardy, Jaunty, and Karmic.  Is there any way to edit the sequences?)

---

### Post by dvandok on 2009-11-05
The low-level way is to create a file called .xmodmap in your homedir; it will be picked up automatically. You'll have to figure out the keycodes by hand though, although running xmodmap -pke and saving the output can be a good start. I simply have

keycode  94 = grave asciitilde grave asciitilde dead_grave dead_tilde dead_grave dead_tilde
keycode 49 = section plusminus

for my MacBook 2,1; those keys are in a funny place so for me this is more consistent with Mac OS X.

---

### Post by dvandok on 2009-11-05
Seems this is a known bug: [https://bugs.launchpad.net/ubuntu/+source/xkeyboard-config/+bug/408397](https://bugs.launchpad.net/ubuntu/+source/xkeyboard-config/+bug/408397)

---

### Post by potiphera on 2009-11-07
Excellent, I applied the patch in that thread, and it works fine now.  Thanks!

---

