---
title: "Problems With Cairo Dock"
date: 2009-09-07
forum: General Help
---

### Post by vmorgs on 2009-09-07
I've been using Cairo Dock in Jaunty for months now with no problems, until now. Now, regardless of what I change it's position to, it stays docked in the top left corner of my screen. This is rather annoying, and I'd prefer to have it docked at the bottom center of my screen. I've gone into the configuration settings and tried every possible position and it still stays docked in the top left corner. Any ideas on why it's doing this and how to fix it? I almost certain a re-install would fix it, but I'd like to avoid that if possible.

---

### Post by fabounet on 2009-09-07
maybe a right permission ?
try chmod -R 777 ~/.config/cairo-dock

---

### Post by vmorgs on 2009-09-19
How do I do that?

I tried uninstalling it and re-installing it but no luck. Same problem. If I want it positioned at the bottom, it positions it self horizontally in the top left corner. If I want it positioned on the right, it positions it self vertically in the top left corner. What gives?

---

### Post by fabounet on 2009-09-19
you can set up the alignment (in the 'Position' module)

---

### Post by vmorgs on 2009-11-01
> **fabounet said:**
> you can set up the alignment (in the 'Position' module)

Tried that doesn't work.

I'd also try the right permission thing but I don't know how to do that.

---

### Post by vmorgs on 2009-11-02
It appears, upon further investigation, that Cairo Dock seems to think my desktop is just a tiny rectangle in top lefthand corner of screen. So, the real problems seems to be that Cairo Dock isn't recognizing the full size of my desktop and adjusting it self accordingly. Any suggestions?

---

### Post by fabounet on 2009-11-03
if you're using Xinerama with a double-screen, there is an option to make the dock use it properly.

you can try to launch it in a terminal with
cairo-dock -l debug > debug.txt
and paste the content of debug.txt here.

---

### Post by HiImTye on 2009-11-03
have you tried alt+dragging it? it works in most cases :)

---

### Post by vmorgs on 2009-11-15
> **fabounet said:**
> if you're using Xinerama with a double-screen, there is an option to make the dock use it properly.

you can try to launch it in a terminal with
cairo-dock -l debug > debug.txt
and paste the content of debug.txt here.

Here's what came up when I did that...

[IMG]http://img682.imageshack.us/img682/1272/debug.png[/IMG]

Any clue what's causing this problem w/ Cairo Dock?

---

### Post by vmorgs on 2009-11-15
Here's a screen shot: 

[IMG]http://img692.imageshack.us/img692/9315/screenshoter.png[/IMG]

See how the desktop background is weird around Cairo Dock? That's because Cairo dock has made a "mini" desktop in that corner of my screen. Currently the Cairo Dock position settings are bottom and center, and still it stays there. If I alt drag it, the dock doesn't move but the small strip of background around the dock does.

---

### Post by fabounet on 2009-11-16
maybe you're using the "use fake transparency" option.
Check it in the "System" module, and disable it if necessary.

then, to move your dock, just go to the "Position" module, and set up the position as you want (set the offsets to 0, as you probably want the dock to be centerd and stuck to the border of the screen).

Also, be sure to have the latest 2.1.1 version.

If you paste the content of debug.txt here, I may guess if something is wrong.

---

