---
title: "Switch of right alt with insert"
date: 2010-09-04
forum: General Help
---

### Post by sentes on 2010-09-04
I have ubuntu 10.04 and I want to switch right alt with insert. It's because I have strange keyboard :P. So I change scancodes in /user/share/X11/xkb/keycodes/evdev, and after reboot it works exactly the same :(. I checked scancodes with xev.

Solved :)

xmodmap -e 'keycode 118=0xfe03'
xmodmap -e 'keycode 108=0xff63'

I used xmodmap -e 'keycode <value>=<action>' and xev to get keysym for action and keycode for value

---

