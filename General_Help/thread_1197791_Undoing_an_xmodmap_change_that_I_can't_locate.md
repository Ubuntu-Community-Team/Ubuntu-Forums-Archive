---
title: "Undoing an xmodmap change that I can't locate"
date: 2009-06-26
forum: General Help
---

### Post by jlebar on 2009-06-26
I installed Ubuntu on my Macbook pro a few weeks ago.  I'm a native PC user, so one of the first things I did was change my keyboard settings so that the apple key behaved like the alt key and I could alt-tab around.  I didn't really know what I was doing, so I might have changed some other keyboard settings as well.  Anyway it worked fine...

...until today, when I plugged in my Windows keyboard.  Lo and behold, my alt key is mapped to ctrl.  And I can't for the life of me figure out where in the world I made this mapping, so I can't figure out how to turn it off.

Here's the output from running xmodmap:
```

xmodmap:  up to 4 keys per modifier, (keycodes in parentheses):

shift       Shift_L (0x32),  Shift_R (0x3e)
lock        Caps_Lock (0x42)
control     Control_L (0x25),  Control_L (0x40),  Control_R (0x69),  Control_R (0x6c)
mod1        Alt_L (0x85),  Alt_R (0x86),  Meta_L (0xcd)
mod2        Num_Lock (0x4d)
mod3      
mod4        Super_L (0xce),  Hyper_L (0xcf)
mod5        ISO_Level3_Shift (0x5c),  Mode_switch (0xcb)

```
I'm not sure, but I think this reflects what I'm seeing, that alt on my Windows keyboard is mapped to ctrl.

I'd expect to see these mappings in ~/.Xmodmap, but that file doesn't exist.  I've been grepping all morning for things like Control_L all over my drive, but I just can't find it.

Is there a way I can reset my X settings to their defaults and hopefully kill this nefarious setting, wherever I put it?  Alternatively, perhaps someone here knows a way to list the system files I've mucked around with.

Either way...I just want my alt key back.

Thanks in advance for your help,
-Justin

---

### Post by ryanfx on 2009-06-27
I too needed this today.. not the exact same situation but close enough.  Bump for a good question :)

---

### Post by benubird on 2010-09-15
I've got the same problem - has anyone found a solution?

---

