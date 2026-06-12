---
title: "Shut down when the power button is pressed?"
date: 2006-06-05
forum: General Help
---

### Post by Zarneth on 2006-06-05
Anyone know how to make the power button work like it did back on breezy, where you hit it and it shuts down straight away? instead of popping up shutdown menu.

I just want to be able to hit the power button once an leave. Not have to go back to my mouse and mess around some more. (This is particularly a problem on my home server I just set up that doesn't have a monitor, I can't shut the damn thing down without remote desktoping in)

---

### Post by blackjack6.21.91 on 2006-06-05
Well I think that when you first touch the power button, the splash comes up, but if you keep holding it down it should eventually powerdown.

But if that's not good enough you might be able to tinker with the power manager.

System --> Preferences --> Power Management

---

### Post by viciouslime on 2006-06-05
I've been meaning to ask this question for some time. The power management ....applet (do you call it that?) Anyway, whatever it is, it is quite limited :( 

Anyone else know where you change this?

---

### Post by _simon_ on 2006-06-05
Terminal -> gconf-editor

apps -> gnome-power-manager

---

### Post by viciouslime on 2006-06-05
[QUOTE=_simon_]Terminal -> gconf-editor

apps -> gnome-power-manager[/QUOTE]


Worked perfectly, thanks! :D 

Would be nice if there was a slightly more... user friendly way of doing it though

---

### Post by mat1t on 2006-06-05
[QUOTE=blackjack6.21.91]Well I think that when you first touch the power button, the splash comes up, but if you keep holding it down it should eventually powerdown.[/QUOTE]

This method doesn't shutdown your computer though. It just powers it off.

---

### Post by Zarneth on 2006-06-05
[QUOTE=_simon_]Terminal -> gconf-editor

apps -> gnome-power-manager[/QUOTE]
Worked. Thanks.

---

