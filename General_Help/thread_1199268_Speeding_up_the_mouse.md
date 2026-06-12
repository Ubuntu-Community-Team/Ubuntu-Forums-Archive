---
title: "Speeding up the mouse"
date: 2009-06-28
forum: General Help
---

### Post by Rubedo on 2009-06-28
Anyone know how I can speed up my mouse? Even with the native speed sliders at max it's like moving through molasses. I wish Logitech (or someone) would make some Linux drivers. :mad:

---

### Post by Steelmourne on 2009-06-28
Is that a wireless or Bluetooth or PS/2 mouse?

If its wireless the batteries might be drained.

---

### Post by Rubedo on 2009-06-29
It's got wires.  I need a software speed boost.

---

### Post by t4thfavor on 2009-06-29
If its usb move it to another channel by its self, some things screw up mice by causing interrupts to fire and monopolising that channel.

plug it into a set of USBs without anything in them. ], 


(Hint USB comes in pairs so if you have 4 putit in the set without anything in it.)

---

### Post by viljun on 2009-06-29
It may be your mouse mat if you have an optical mouse. Try using a white A4-paper as a mat.

If it's not optical clean it - take of the ball etc.

I wouldn't suspect the "drivers".

---

### Post by Rubedo on 2009-06-29
It still runs super fast the way I like it on the Windows side, it's not a hardware problem.

---

### Post by themusicalduck on 2009-06-29
System > Preferences > Mouse has options for speeding up the mouse.

---

### Post by acorn22 on 2009-06-29
Wow, did anyone read the original post?? :-k 

He wants to go beyond the sliders. I have been wondering about this as well, but I want to go the the other way :)

---

### Post by themusicalduck on 2009-06-29
Whoops, you're right.. I lost the ability to read this morning.. ;)

---

### Post by moster on 2009-06-29
hm, something is not right. You should not be doing this. If I were you I would get converter for 1$ and stick it in PS/2 or if already in it stick it to USB. 

This article is little old but take a look..
[http://www.linuxquestions.org/questions/slackware-14/how-to-set-mouse-sensitivity-in-xorg.conf-not-window-manager-425552/]("http://www.linuxquestions.org/questions/slackware-14/how-to-set-mouse-sensitivity-in-xorg.conf-not-window-manager-425552/")

if not exactly say in there how to edit, here it is.
```
sudo gedit /etc/X11/xorg.conf
```

and restart after is required. (you can restart ony X if you know how)

---

### Post by rathervague on 2009-06-30
I had the same problem, a slow mouse (microsoft usb with red bit) on a big screen.

Maxed out the pointer speed setting to no effect.

Acceleration: Fast
Sensitivity: High

What actually worked was

Acceleration: Fast
Sensitivity: Low

---

