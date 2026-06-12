---
title: "Problem typing &quot;^&quot; in matlab, maple etc."
date: 2006-03-11
forum: General Help
---

### Post by jostein on 2006-03-11
I'm using both maple and matlab in my studies. Both installed just fine, but I have got a really annoying keyboard problem with these applications, and other ones as well. When I type "3^2" the result is:

[LIST]
[*]Matlab: 3 with 2 as a superscript. Looks neat, but gives me syntax errors whenever I try to execute the statement.
[*]Gnuplot: Same as Matlab.
[*]Python interpreter: Like Matlab, but if i type "3^[space]2", I get what I want. That doesn't work anywhere else.
[*]Maple: the number 3 is displayed, the rest disappears into nothingness.
[/LIST]

I suspect ubuntu is doing some kind of substitution, interchanging "^2" with the "superscript 2". If that is the case, does anyone know how to turn it off?

About my computer:
Ubuntu 5.10, Gnome
Laptop with a norwegian keyboard (the keyboard has worked excellent ever since the installation, including the national characters and the special "laptop-keys").

Any help is much appreciated!

Jostein.

---

### Post by colo on 2006-03-11
You could work around that issue by pressing ^[SPACE][NUMBER]. With the nodeadkeys-option set for X11 you'll also get rid of this behaviour.

---

### Post by jostein on 2006-03-12
Hi!

Thanks for your help. The results are:

^[space][number] has no effect - the result is unchanged (I had tried that before). However, nodeadkeys worked superb. This is what I did:

1. Editing the file /etc/X11/xorg.conf, adding the line
```

Option		"XkbVariant"	"nodeadkeys"

```
in the section "InputDevice" (after making sure that this particular section referred to my keyboard, not my mouse (the mouse section is also named "InputDevice")).
2. Reboot.
3. After logging into Gnome, I got a message about gnome and X configurations in disagreement. It asked me which one I wanted to use, and i answeared X.

That was it. Thanks again!

Jostein.

---

