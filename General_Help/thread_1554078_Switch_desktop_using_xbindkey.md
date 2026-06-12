---
title: "Switch desktop using xbindkey"
date: 2010-08-16
forum: General Help
---

### Post by Maciej Miklas on 2010-08-16
Hi,

I have Logitech MX1100 mouse. I can assign every button to key action, except Desktop/Workspace manager.

1) I've assigned SuperL+Left to the "Swich to workspace on the left of the current one" - this works fine

2) I've follwoing .xbindkeysrc

[PHP]
"/usr/bin/xvkbd -xsendevent -text "\[Super_L]\[Left]""
m:0x0 + b:10

"/usr/bin/xvkbd -xsendevent -text "\[Super_L]\[Right]""
m:0x0 + b:8

"/usr/bin/xvkbd -xsendevent -text "\[Control_L]\[v]""
m:0x0 + b:9

"/usr/bin/xvkbd -xsendevent -text "\[Alt_L]\[Left]""
m:0x0 + b:6

"/usr/bin/xvkbd -xsendevent -text "\[Alt_L]\[Right]""
m:0x0 + b:7
[/PHP]

all other key assigments are working, only workspace switch does not.

Can someone help me ?

---

### Post by kerry_s on 2010-08-16
it's suppose to be ctrl+alt+left/right

---

### Post by LightningCrash on 2010-08-16
You don't necessarily have to make it send the keystroke.

There's a program called Wmctrl you could have it call...
[http://en.wikipedia.org/wiki/Wmctrl](http://en.wikipedia.org/wiki/Wmctrl)

---

