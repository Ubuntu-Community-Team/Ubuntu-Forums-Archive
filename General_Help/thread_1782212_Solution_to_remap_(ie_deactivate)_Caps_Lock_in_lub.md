---
title: "Solution to remap (ie deactivate) Caps Lock in lubuntu"
date: 2011-06-14
forum: General Help
---

### Post by elundmark on 2011-06-14
Just thought I'd throw this up in the ether, took me a while to find this solution.

Open up (lx)terminal and type in the one you want:
# 1. Lubuntu Caps Lock -> Super
```
setxkbmap -option caps:super
```
# 2. Left Control <-> Caps Lock
```
setxkbmap -option ctrl:swapcaps
```
# 3. Caps Lock -> Control
```
setxkbmap -option ctrl:nocaps
```

**EDIT:**

Of course this doesn't get saved persistantly on reboot, so you have to run this for every boot.
I've placed a script called "caps-killer.sh" in /usr/bin/caps-killer.sh and made it run on boot by running:

gksudo leafpad /etc/xdg/lxsession/Lubuntu/autostart

...and inserted this at the end:

```
@/usr/bin/caps-killer.sh
```

Kudos to a commenter on [JJinuxLand]("http://jjinux.blogspot.com/2011/03/linux-lubuntu.html").

---

### Post by dr_leviathan on 2011-06-18
These magic spells worked for me (Xubuntu 11.04).

Googling for this info results in a great deal of legacy results that was helpful back in 2006 but is now just wrong.

---

### Post by Luz77 on 2011-08-09
Hi, I wanted to remap caps lock to escape and escape to caps lock. Here is how it works:

file: 'swap-esc-caps'
```
! Swap caps lock and escape
remove Lock = Caps_Lock
keysym Escape = Caps_Lock
keysym Caps_Lock = Escape
add Lock = Caps_Lock
```

file: 'swap-esc-caps.sh'
```
xmodmap swap-esc-caps
```

---

### Post by The Cog on 2011-11-02
Or to simply disable Caps Lock making it a dead key:
```
setxkbmap -option caps:none
```
and to restore the default (re-enable it):
```
setxkbmap -option
```

I'm still looking for a way to turn Caps Lock into a simple non-locking Shift key though.

---

### Post by amjjawad on 2011-11-03
> **The Cog said:**
> Or to simply disable Caps Lock making it a dead key:
```
setxkbmap -option caps:none
```
and to restore the default (re-enable it):
```
setxkbmap -option
```

I'm still looking for a way to turn Caps Lock into a simple non-locking Shift key though.

Sorry but may I ask what's the point?

---

### Post by The Cog on 2011-11-04
The point is that all too often, I fumble the caps lock button AND END UP TYPING HALF A SENTENCE IN CAPITALS. Generally when I type an 'a' or use the shift key. If I were better at touch typing, I would spend more time looking at the screen instead of at the keyboard and would notice sooner, but I'm not. I prefer to simply disable caps lock, which I almost never use except by accident.

---

### Post by amjjawad on 2011-11-04
> **The Cog said:**
> The point is that all too often, I fumble the caps lock button AND END UP TYPING HALF A SENTENCE IN CAPITALS. Generally when I type an 'a' or use the shift key. If I were better at touch typing, I would spend more time looking at the screen instead of at the keyboard and would notice sooner, but I'm not. I prefer to simply disable caps lock, which I almost never use except by accident.

Oh, got it :)
I'm actually too fast and I do use Touch Typing since 10 years maybe? so I don't have to worry about it. I just thought there is some other point that I missed :)

Thank you :)

---

