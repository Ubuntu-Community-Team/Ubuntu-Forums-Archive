---
title: "Turn CapsLock into a Unique Modifier Key"
date: 2010-08-23
forum: General Help
---

### Post by lawschool121 on 2010-08-23
I would like to use Caps Lock as its own UNIQUE modifier key (not merely replace it with Ctrl).  I have figured out how to do this on windows but not yet in Ubuntu.  Here is what I'm looking for:

1. When I press "Caps Lock" on its own, it is equivalent to the Escape key (or at least sends the "escape" command).
2. When I press Caps Lock + <new key>, it does other stuff.

I have figured out how to get EITHER ONE of these to work, but not both at the same time.  For example, I have figured out how to turn Caps Lock into the unique "Super" modifier using xbindkeys and xmacro (this achieves #2).  I have also figured out how to switch the escape and capslocks keys altogether to achieve #1.  But I can't figure out how to get both outcomes at the same time!

Any advice?

---

### Post by mike555 on 2010-08-23
I use "xkeycaps" ,it will let you change most any key ..... when installed type xkeycaps in terminal to run it or make a launcher.

---

### Post by lawschool121 on 2010-08-23
XKeyCaps is only a GUI interface for XbindKeys, which I've tried unsuccessfully to fix my problem.  Any other suggestions?

---

### Post by ealfonso on 2013-02-22
Use xmodmap to remap Caps_Lock to the Hyper key.

```

xmodmap -e 'keycode 66 = Hyper_L'
xmodmap -e 'clear mod3'
xmodmap -e 'add mod3 =Hyper_L'

```

You should now have Caps_Lock as a unique modifier key. Test with 'xev' to make sure Caps_Lock generates the 'Hyper_L' keycode. I haven't tested this directly, so let me know if this works!

---

