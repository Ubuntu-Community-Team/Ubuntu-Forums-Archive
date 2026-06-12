---
title: "Remapping Keys with Key Groups"
date: 2011-07-20
forum: General Help
---

### Post by rdnetto on 2011-07-20
Hi,
I have a laptop which has no function keys (F1-F12), but does have a row of arbitrary keys at the top (volume control, multimedia, etc.). I've been able to remap these keys using xmodmap (e.g. 'keycode 000 = F1 NoSymbol F1'). However, this means that I lose the original function.

Is there a way (using xmodmap or otherwise) to set these keys to produce a different keysym (e.g. XF86AudioRaiseVolume) _only_ when the Super* key is pressed?

* I would have preferred Fn, but it doesn't show up in xev so I'm guessing that's not possible.

---

### Post by enimeizoo on 2011-07-20
Well, the fn key is special. It doesn't even send a scancode on most keyboards, but modifies scancodes of keys pressed while it is pressed.
Well, I can think of two ways of doing that.

```

keycode XX = F1 XF86AudioRaiseVolume F1 F1 F1 F1

```Should let you have the key send XF86AudioRaiseVolume while shift is pressed.

```

keycode XX = F1  F1 F1 F1 XF86AudioRaiseVolume F1

```Should let you have the key send XF86AudioRaiseVolume while alt_GR is pressed.

Another requires xbindkeys and xdotool or xte. I'm not sure yet how you send keysyms via xdotool or xte, but it should be possible. The idea is just to bind Super+F1 to 'send keysym XF86AudioRaiseVolume'

(edit) It is actually quite easy : ```
xdotool key XF86AudioPlay
```

Good luck!

---

### Post by rdnetto on 2011-07-21
Thanks, that's just what I was looking for.

EDIT: Just realised there's a GUI in Kubuntu that does the exact same thing automatically. :oops:

---

