---
title: "osd_clock how to put in a startup script?"
date: 2010-05-11
forum: General Help
---

### Post by Oddbio on 2010-05-11
I am using the "ratpoison" window manager. I have it setup to use a small tray at the bottom of the screen for the wireless nm-applet, so there's a lot of blank space and I would like to add a clock there.

I found a way to do this exactly with nm-applet and the tray I'm using, the command is:
**osd_clock -f $quot;-*-lucidatypewriter-medium-*-*-*-17-*-*-*-*-*-*-*$quot;**

The issue is that I cannot run it with a "&" symbol at the end... for some reason it does not work, so it doesn't work with my startup script.
If I enter it in a terminal it works perfectly but I can't enter the "&" sign at the end, so basically I have to have a terminal open all the time just to keep the clock running, and another terminal for other things.

It's an annoyance. I am sure this is probably a noob question with a simple solution, but I just can't think of it.. honestly I have no idea why the "&" sign wouldn't work
it just says syntax error if I do.

Thanks for any help.

---

### Post by bredman on 2010-05-11
You are using the incorrect type of quotes. It works fine as

**osd_clock -f '-*-lucidatypewriter-medium-*-*-*-17-*-*-*-*-*-*-*' &**

---

### Post by Oddbio on 2010-05-12
Awesome that works, thank you.
I'm sure it's quite obvious to you that I just copied that straight off of a website without understanding it lol..

I know I shouldn't do that, but I couldn't find anything about the strange *-*-*- type of notation and the man pages didn't have anything either, so I just used it the way they had it.


But thanks, the font looks much better like this too  :D

---

