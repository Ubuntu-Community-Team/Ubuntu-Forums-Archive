---
title: "Emerald Problem When Maximizing"
date: 2011-01-21
forum: General Help
---

### Post by BlazeFire247 on 2011-01-21
Hi there. I've been having problems with Emerald recently. I can use themes and everything, but whenever I maximize a window, the title bar disappears. Then I have to do "emerald --replace" to get it back. If I use gtk-window-decorator, I get this problem when I maximize the window, but when I open a new one/unmaximize, it doesn't disappear unlike Emerald. 

[IMG]http://ompldr.org/vNzNtbw[/IMG]
This is what happens with gtk-window-decorator. It disappears when maximized, yet appears when unmaximized.

[IMG]http://ompldr.org/vNzNtbg[/IMG]
Here's what happens with Emerald. Once I've maximized one window, every titlebar disappears.

I don't know what's the cause of this, though. Can someone help me?

---

### Post by Elline on 2011-02-09
Geez, I have the same issue.
Now trying any workarounds, but no effect still.
Maybe it is about panel plug-ins? I see you have a menu-panel, but I have a window title (don't remember exactly it's name) plug-in, which holds my window title and controls.
What is similar in our case is are removed decorations on window maximize.

Here's what I have in compiz-config in window decorations >> decorations:
```
!(state=maxvert | maxhorz)
```

What about yours?

---

### Post by Elline on 2011-02-09
I probably found a workaround.
Open the emerald theme manager, go to "Emerald settings" and toggle off the "Use button fade" checkbox.

---

