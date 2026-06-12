---
title: "Problem with forward/back buttons on Logitech MX518"
date: 2006-05-25
forum: General Help
---

### Post by binary visions on 2006-05-25
The information in this forum has helped a lot in getting my new Ubuntu setup tweaked to my liking.

The only unfixable problem I've had is with my forward/back buttons on my Logitech MX518. I've read all the tutorials on how to set it up with xbindkeys, and understand the concepts, but when I use XEV to determine what button numbers each of my mouse buttons correlate to, some of the buttons come up as the same number.

My forward button shows up as the same number event as my right mouse button, so when I assign Alt-Right to button #2, it causes my right mouse button to stop functioning correctly. My back button has the same number as clicking the mouse wheel as well.

I can't seem to find any other references to someone who has this problem. What would cause multiple buttons to be assigned the same number?

---

### Post by colo on 2006-05-25
An inappropriate protocol used by X to interpret what's going on with the buttons of your mouse. "evdev" (jnstead of "ExplorerPS/2, "ImPS/2" and the like) should solve your problems. Google should help you to see how it's done :)

---

### Post by binary visions on 2006-05-26
[QUOTE=colo]An inappropriate protocol used by X to interpret what's going on with the buttons of your mouse. "evdev" (jnstead of "ExplorerPS/2, "ImPS/2" and the like) should solve your problems. Google should help you to see how it's done :)[/QUOTE]

Bingo. Thanks. I didn't need Google, I guess I was just overlooking "ImPS/2" several times and needed someone to slap me and point it out.

Thanks for the help, works perfectly now!

---

