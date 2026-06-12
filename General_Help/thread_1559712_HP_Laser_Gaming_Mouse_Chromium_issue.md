---
title: "HP Laser Gaming Mouse Chromium issue"
date: 2010-08-23
forum: General Help
---

### Post by reffu on 2010-08-23
I have the HP Laser Gaming Mouse with VoodooDNA and almost everything works fine and is plug and play including the extra mouse buttons and the DPI switch. The problem is how the DPI switch affects Chromium (version is unimportant because I have been having this problem since v5.X.XXX) and Chrome (again version independent). When the DPI switch is set to any setting other than default (800 DPI I think) right clicking in chromium will immediately trigger the top option when the button is released. This is a problem because often I will right click to copy some text or perform another action and it will go back a page. 

This has been a problem in both Ubuntu 9.10 and 10.04 and does not affect Firefox or Windows. 

I have one theory that all mouse events count as two. In chromium right clicking twice without moving the mouse will cause the first right click option to be used, similar to my problem. In Firefox this does not happen. I also believe this double mouse event would not affect most other programs because the mouse events are nearly simultaneous.

I could be wrong and one thing I would like help with is remembering the terminal code to create a mouse capture window that records mouse events.

I would appreciate it greatly if someone could provide me with alternate ideas or solutions.

Sorry if i posted this in the wrong category. I don't know (as of now) whether this is hardware, software, system-wide or application-specific.

Thanks,

Reffu

Update: I think I found the problem. Its that in chromium letting go of the right mouse button over a menu choice will execute that choice. With a higher DPI I think the mouse pointer moves imperceptibly in the time between pressing and releasing the right mouse button. I would still appreciate other suggestions but I think this is the problem.

---

