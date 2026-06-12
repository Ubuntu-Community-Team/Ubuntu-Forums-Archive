---
title: "xkb (setxkbmap &amp; xmodmap) forget their setting within minutes"
date: 2012-04-22
forum: General Help
---

### Post by Willard on 2012-04-22
Hi,

I am trying to make my caps lock key into a control key.

I know how to do this using xmodmap; here's a sample ~/.xmodmaprc:
```
keycode 66 = Control_L
clear Lock
add Control = Control_L
```

I also know what option to throw into setxkbmap; here's a sample command:
```
/usr/bin/setxkbmap -option "ctrl:nocaps"
```

The problem, however, is that with either of these approaches, the keyboard change only "sticks" for a few minutes; then spontaneously, my caps lock key reverts to being caps lock again.

[LIST]
[*]Why is this happening?
[*]If fixable, how do I fix this?
[*]If not fixable, what workaround can I go for?
[/LIST]

Currently I am running this stupid code in the background to be able to work on my machine:
```
while : ; do /usr/bin/setxkbmap -option "ctrl:nocaps" ; sleep 10 ; done
```

In case it matters, my computer is an Asus EEE 1015PEM netbook.

and I am running Xubuntu 11.10.

Thanks,
Willard.

---

### Post by LuckyNeo on 2012-05-14
I have the same problem. Thanks for your "stupid" code, it helped me a lot.

---

