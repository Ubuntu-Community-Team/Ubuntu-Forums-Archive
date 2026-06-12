---
title: "xbindkeys - map mouse button to key + modifier keys"
date: 2011-08-23
forum: General Help
---

### Post by myro21 on 2011-08-23
Hi,
i am trying to start gaming on linux to be able to replace my windows fully and I have the following problem with xbindkeys:

I am currently using xbindkeys to map mouse buttons to F keys.
.xbindkeysrc:
```

"xvkbd  -text "\[F6]""
  b:11

"xvkbd  -text "\[F7]""
  b:12

"xvkbd  -text "\[F8]""
  b:10

```

But now if I press for example shift + b:11, nothing happens. 
Is it possible to map a mouse button + key_modifier to 1 key + key_modifier?

For example: b:11 + key_modifier should be mapped to F6 + key_modifier.

The same problem exists, if i use 'W' for walking forward for example and using b:11 for a game action. Then nothing is done, since W+b:11 is not mapped. 

Is there an any_key dummy to map it to any_key or something similar?

Any tips/links are very welcome.
Thank you for reading.

---

### Post by ncy on 2011-09-02
You may want to try xte or xdotool instead of xvkbd and see if you get different results.

I don't think you should have to define every case of when a modifier key is or isn't pressed.

Try something like:

```

"xte 'key F6'"
  b:11

```

If that doesn't work and you want to play around with the modifier key settings, try:

```

"xte 'keydown Shift_L' 'key F6' 'keyup Shift_L'"
  shift + b:11

```

I found this page very useful:

[http://hanschen.org/2009/10/13/mouse-shortcuts-with-xbindkeys/](http://hanschen.org/2009/10/13/mouse-shortcuts-with-xbindkeys/)

This one also has a workaround for the game "Enemy Territory":

[https://wiki.archlinux.org/index.php/All_Mouse_Buttons_Working#Binding_keyboard_to_mouse_buttons](https://wiki.archlinux.org/index.php/All_Mouse_Buttons_Working#Binding_keyboard_to_mouse_buttons)

---

### Post by apasnuy on 2012-08-05
For Ubuntu 12.04 works flawlessly
[http://forum.pinguyos.com/Thread-HOWTO-Mouse-buttons-to-change-workspaces-in-gnome-shell]("http://forum.pinguyos.com/Thread-HOWTO-Mouse-buttons-to-change-workspaces-in-gnome-shell")

---

