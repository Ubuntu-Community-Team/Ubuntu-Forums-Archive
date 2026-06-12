---
title: "xmodmap in xinitrc not sticking"
date: 2010-09-08
forum: General Help
---

### Post by mitchellh on 2010-09-08
So I run "xmodmap" in my xinitrc to make caps lock a second control button, but for some reason its not sticking. I'm not using a desktop environment, just running xmonad.

Here is my Xmodmap file:

```

remove Lock = Caps_Lock
remove Control = Control_L
keysym Caps_Lock = Control_L
add Lock = Caps_Lock
add Control = Control_L

```

And my ~/.xinitrc:

```

#!/bin/sh

xmodmap ~/.Xmodmap
exec xmonad

```

If I run "xmodmap ~/.Xmodmap" once X is started, it works fine, but it won't run in my xinitrc.

Any ideas?

---

### Post by Brandon Williams on 2010-09-08
I think that this has to do with a bad interaction between xkb and xmodmap, where your xmodmap settings are lost when the xkb settings are applied. Run this command to determine whether xkb is used:
```
grep xkb /var/log/Xorg.0.log
```
Do you see a bunch of xkb options in the list? If so, then this is the likely issue.

I don't know enough about xkb to be certain of a solution. I've read that this command is a workable replacement for your xmodmap config in that it should turn the capslock key into a control key.
```
setxkbmap -option ctrl:nocaps
```
If you use something other than the US keyboard layout, you'll probably need this instead (<ID> is the layout id, e.g. gb for UK English layout):
```
setxkbmap -layout <ID> -option ctrl:nocaps
```

---

### Post by mitchellh on 2010-09-08
That "setxkpmap" line worked great. I replaced the xmodmap call with that and it works.

I'm still curious what was going on but I'll have to look later.

Thanks!

---

### Post by Brandon Williams on 2010-09-08
> **mitchellh said:**
> I'm still curious what was going on but I'll have to look later.

The basic thing is that xkb and xmodmap two different ways of managing some of the same things. Any time the xkb settings get applied, such as during X initialization, they will over-ride any changes made with xmodmap. If you start your session via gdm, it won't even attempt to apply your xmodmap settings if it detects that xkb is in use.

---

