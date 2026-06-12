---
title: "GNOME - left-clicking anywhere in window results in dragging"
date: 2010-03-25
forum: General Help
---

### Post by km0r3 on 2010-03-25
_[SIZE=5]Problem:[/SIZE]_[B]
When I click the window with the left mouse button my window gets dragged, instead that the GUI elements are getting selected.
[/B]
_For example:_

[LIST]
[*]Opening Firefox and selecting the address field doesn't activate the field to write in.
[*]Clicking buttons is impossible.
[/LIST]
Any action in the window seems like blocked.

[I]I'm working this around by holding Shift + Left mouse button; then it's possible to activate the GUI element.
[/I]
_[SIZE=5]Observation:[/SIZE]_

[LIST]
[*]This happened just today when I switched on my computer and seems to affect only me as my user!
[*]Logging in as another user doesn't bring up this error. Everything works as usual as possible.
[*]The Gnome Panel is not affected.
[*]Closing, minimizing/maximizing windows is possible.
[*]Clicking anywhere on the window with the right mouse button opens the window options menu, not the expected options.
[*]Hovering over a button seems to be recognized as it changes its properties, but clicking still drags the window.
[*]Restarting X and restarting Ubuntu doesn't change anything.
[/LIST]
What is happening?

Any help and suggestions are welcome.

**_Platform:_**
Gnome: 2.28.1
Ubuntu: 9.10
Kernel: Linux 2.6.31-20-generic #58-Ubuntu i686 GNU/Linux

I've filed this under launchpad, too, but maybe you know the answer.

---

### Post by km0r3 on 2010-03-25
De-activating Compiz is a work-around. It now doesn't bring up this issue anymore.


If there are no more follow-ups to this topic in the next 24h I'll mark this as Solved.

---

### Post by rahilm on 2010-03-25
If you have compiz config sttings manager installed.. check the Move Windows Plugin in the Windows Management section..

---

### Post by km0r3 on 2010-03-25
> **rahilm said:**
> If you have compiz config sttings manager installed.. check the Move Windows Plugin in the Windows Management section..

In fact, that was the problem. This has been set to be activated on clicking Button1. I changed it to something else, now it doesn't disturb me anymore.

I can't remember setting this at any moment... :?:

You're the man, rahilm!

---

### Post by rahilm on 2010-03-26
glad to help when i can!! just returning the favor..

---

