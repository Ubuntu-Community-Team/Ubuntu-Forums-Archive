---
title: "issue with xkbset and non-us keyboard layout"
date: 2011-05-23
forum: General Help
---

### Post by luca5am on 2011-05-23
Hi,

I am trying to set my laptop menu key (key code 135) so that it maps the middle click of a mouse (for easy paste-of-current-selection since my laptop pad does not have a middle button).

I used this post as a guide: 
[http://linuxaleph.blogspot.com/2008/11/mapping-middle-click-to-keyboard-key.html](http://linuxaleph.blogspot.com/2008/11/mapping-middle-click-to-keyboard-key.html)
which consists in:
installing xkbset
running the following script to assign the menu key to the middle button:
```
#!/bin/bash
# set XKB layout
setxkbmap -layout us
# turn on mousekeys
xkbset m
# stop mousekeys expiring after a timeout
xkbset exp =m
# map the key
xmodmap -e "keycode 135 = Pointer_Button2"
```It works perfectly as is. The problem? If I change the line setting the keyboard layout to a French layout, which I use:
```
setxkbmap -layout fr
```It doesn't work any more. I know that something happens because pressing the Menu key does not show the menu as it does when I don't use xkbset at all.

If I try to use both US and French layout:
```
setxkbmap -layout fr,us
```It does not work either, no matter what layout is currently selected

I checked (by running xev) that the Menu button has the same key code (135) in both layouts and it does. Besides, in both cases, I checked that the key code 135 is bound to "Pointer_Button2" and it is:
```
> xmodmap -pk | grep 135
    135        0xfeea (Pointer_Button2)    0x0000 (NoSymbol)    0xfeea (Pointer_Button2)    
```I also tried with another key (right Alt), same problem.

Thank you in advance for suggestions or other ways to do it.

---

### Post by TeoBigusGeekus on 2011-05-23
Just a thought: setxkbmap with the -layout switch doesn't accept multiple layouts.
So, try changing
```
setxkbmap -layout fr,us
```
to 
```
setxkbmap fr,us
```
and see if it does anything.

---

### Post by luca5am on 2011-05-24
I tried but I have the exact same problem: it only works when only the "us" option is selected in the setxkbmap line.

---

