---
title: "Ubuntu 12.04 Gnome Classic  panel problem"
date: 2012-04-29
forum: General Help
---

### Post by hal8000 on 2012-04-29
This is a clean install of Ubuntu 12.04 64bit

I like Unity but also the older gnome-session.

I have installed gnome-session-fallback and can log into the standard gnome classic desktop.

However I can drag icons onto the gnome panels, but not size, move or delete them.
Pressing alt + right click does not bring up any menus. The blog below
works fine in Ubuntu 11.10 but the alt-right click does not work on panels
in 12.04

[http://deviceguru.com/ubuntu-11-10-without-shell-shock/](http://deviceguru.com/ubuntu-11-10-without-shell-shock/)

Anyone else using gnome classic with Ubuntu 12.04 with the same problem?
Thanks in advance.

---

### Post by Zymous on 2012-04-29
Try [Windows-key] + [Alt] + Right-click

-- 
Zym

---

### Post by hal8000 on 2012-05-01
> **Zymous said:**
> Try [Windows-key] + [Alt] + Right-click

-- 
Zym

Thank you Zym,
That was the key combination I was looking for, marked as solved now.

---

### Post by cygnus-X1 on 2012-05-01
Thank both of your **VERY** much! :guitar:
I am essentially moving from 10.04 to 12.04, and I find "*Unity*" to be **excessively** convoluted. Most functionality and control are all but gone. Why do I need to "search" for something when I already know where it lives? 

**Note to Ubuntu: **
Searching on the web makes sense. 
Searching for things you know where they reside on your own system is time consuming.
BRING BACK GNOME AS THE STANDARD AND MAKE UNITY AN "OPTION". Thank you...

---

### Post by codingman on 2012-05-01
Thank you all very much for this, i have found this very educational. Now I can add anything I want to the gnome classic panel. I will definitely refer many users to this thread.

---

### Post by Trapper on 2012-05-01
> **Zymous said:**
> Try [Windows-key] + [Alt] + Right-click

-- 
Zym


Uh ... what about us people that have keyboards without a Windows key? We have a house full of old clackity clack M2 IBM ps2 keyboards. Running out and getting new keyboards is not an option.

---

### Post by pannerrammer on 2012-05-07
> **Trapper said:**
> Uh ... what about us people that have keyboards without a Windows key? We have a house full of old clackity clack M2 IBM ps2 keyboards. Running out and getting new keyboards is not an option.

There are at least two of us out here, same problem

---

### Post by Trapper on 2012-05-07
> **pannerrammer said:**
> There are at least two of us out here, same problem

Sorry to hear that.

As for me. I'm not about to give up bulletproof keyboards that have lasted for many, many years and will last for many more. My choice is a no-brainer. Ubuntu 12.04 and/or Gnome 3 totally lost out. We'll be phasing out U-10.04 over time and will be replacing it with Mint LMDE and MATE desktop environment. It's like never leaving U-10.04.

---

### Post by hal8000 on 2012-05-07
For those of you without a windows key:
Ctrl+ Esc used to emulate the windows key.

I would therefore try:
ctrl+esc+alt and right click

not sure if this will work.

You may be able to use xbindkeys to modify a keymap, here's a link:

[http://www.butlerpc.net/blog/2011/01/using-xbindkeys-on-ubuntu-linux-to-remap-key-commands/](http://www.butlerpc.net/blog/2011/01/using-xbindkeys-on-ubuntu-linux-to-remap-key-commands/)

I'm just using a different linux at the moment but typing xmodmap will
show keybindings:

[anc@orac ~]$ xmodmap
xmodmap:  up to 3 keys per modifier, (keycodes in parentheses):

shift       Shift_L (0x32),  Shift_R (0x3e)
lock        Caps_Lock (0x42)
control     Control_L (0x25),  Control_R (0x69)
mod1        Alt_L (0x40),  Meta_L (0xcd)
mod2        Num_Lock (0x4d)
mod3
mod4        Super_L (0x85),  Super_L (0xce),  Hyper_L (0xcf)
mod5        ISO_Level3_Shift (0x5c),  Mode_switch (0xcb)


There may be someone with greater expertise with the classic gnome shell in Ubuntu 12.04 who can offer further advise on keybinding.

---

### Post by pannerrammer on 2012-05-08
My original IBM keyboard was made in 1988 and is still clattering strongly.

Ctrl+Esc doesn't work (other than on windows). 

However I think that **Alt+AltGr** (plus right clicking the panel) does. Bit of a finger-breaker though!

---

### Post by Clancy_s on 2012-05-08
> **pannerrammer said:**
> My original IBM keyboard was made in 1988 and is still clattering strongly.

Ctrl+Esc doesn't work (other than on windows). 

However I think that **Alt+AltGr** (plus right clicking the panel) does. Bit of a finger-breaker though!

*googles*

apparentl AltGr can be emulated by Ctrl+Alt...;)

---

### Post by pannerrammer on 2012-05-09
> **Clancy_s said:**
> *googles*

apparentl AltGr can be emulated by Ctrl+Alt...;)

Perhaps, but then I'd have to press Alt+Ctrl+Alt .. and there aren't enough Alt keys on my keyboard :(

---

### Post by whitething on 2012-05-20
Thanks guys, helped me a lot.

Maybe in the next release they'll make it a 4 key combo like "F1 + Alt + Break + NumPlus", that you'll have to hit 12 times in a rhythmic pattern. Y'know, to make it clearer for users.:mad:

---

### Post by johnh44 on 2012-10-19
> **cygnus-X1 said:**
> 
BRING BACK GNOME AS THE STANDARD AND MAKE UNITY AN "OPTION". Thank you...

Hear! Hear!

---

### Post by Mintux on 2012-10-26
You don't need the windows key. 

Alt + right click on the panel works just fine. 

Personally I don't even have a windows key, I order my keyboards without it.


Have to say I share your sentiments on Unity though.  It's very simple, and very inefficient.  Not only is it extremely slow and sluggish compared to Gnome, but it's also a lot mor cumbersome to use and eats more screen real estate. I'm not particularly fond of the new look of Gnome either, kudos to the Gnome people for including the classic option.

Unfortunately Ubuntu seems to be less and less compatible with Gnome - still more gnome functionality is not working in 12.4 due to Ubuntu expecting Unity to be used.

---

