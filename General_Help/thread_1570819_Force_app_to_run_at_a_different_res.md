---
title: "Force app to run at a different res?"
date: 2010-09-08
forum: General Help
---

### Post by _Fordy on 2010-09-08
I can do it in Win, just can't get my head around it here.

I need to be able to see *all* of the program running lol, the bottom portion (around 25px i think) is missing.

Programs only options are, 1024x600 (netbooks native WSVGA res), and 800x600.

I need something like 1024x750...

---

### Post by dcstar on 2010-09-09
> **_Fordy said:**
> I can do it in Win, just can't get my head around it here.

I need to be able to see *all* of the program running lol, the bottom portion (around 25px i think) is missing.

Programs only options are, 1024x600 (netbooks native WSVGA res), and 800x600.

I need something like 1024x750...

You can add a "virtual" resolution to your /etc/xorg.conf, and that should allow you to scroll the screen up and down.

---

### Post by kerry_s on 2010-09-09
alt+left click drag
or
alt+f7

is all you need to move windows in to view.

---

### Post by _Fordy on 2010-09-09
> **kerry_s said:**
> alt+left click drag
or
alt+f7

is all you need to move windows in to view.

Interesting how stupid people can think you are.

I didn't make a thread about resolution because my widow is out of view, and needs to be dragged back. -_-

The program is running at 600 horizontal lines.

The screen (as a WSVGA display) has 600 horizontal lines.

Ubuntu Netbook Remix has a non-movable or auto-hidable (as far as I can tell) panel along the top.

Thus, the programs last 30ish lines are pushed off screen - theres is nowhere to drag it to. I need to see it all at once - scrolling is not really a solution.

---

### Post by realzippy on 2010-09-09
Which graphics card/driver/ubuntu version?
You have a xorg.conf?  (/etc/X11/xorg.conf)
If so,post it please....



...btw,very nice typo:because my widow is out of view (mine too)

---

### Post by _Fordy on 2010-09-09
> **realzippy said:**
> Which graphics card/driver/ubuntu version?
You have a xorg.conf?  (/etc/X11/xorg.conf)
If so,post it please....



...btw,very nice typo:because my widow is out of view (mine too)

No graphics card, it's a netbook :P

Netbook Remix 10.04

Not got it on me atm, I'll post the .conf later.

---

### Post by realzippy on 2010-09-09
*No graphics card, it's a netbook* 

With a display,so kind of graphics card/chip should exist..

---

### Post by _Fordy on 2010-09-09
> **realzippy said:**
> *No graphics card, it's a netbook* 

With a display,so kind of graphics card/chip should exist..

Most netbooks use an Intel Atom CPU (In my case, an N270).

Atom's have integrated graphics processing.

So if that's the answer you want - the "GPU", is an Intel N270.

But there is no dedicated graphics.

---

### Post by kerry_s on 2010-09-09
> Thus, the programs last 30ish lines are pushed off screen - theres is nowhere to drag it to. I need to see it all at once - scrolling is not really a solution.

you move it to scroll the app, just like you would if you where to change the resolution. any which way you'll be scrolling.


example: i'll set my screen to 800x600, so the program go's under my panel. will pretend thats off screen.

---

