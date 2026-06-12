---
title: "Gnome Panel (10.04) in middle of screen after reboot"
date: 2010-06-04
forum: General Help
---

### Post by MrVas on 2010-06-04
When I reboot (or startup after shutting down) my Ubuntu 10.04 (x64) system, the Gnome Panel is in the middle of the screen, instead of on top (where I like it).  The only workaround I have found is to select "Expand" under "Panel Properties", but I don't like the panel expanded.  The other annoyance (that came with this feature) is that the panel icons get rearranged every time I reboot.

Any help would be appreciated.

Thank you,

Vas

---

### Post by MrVas on 2010-06-08
I have recreated the top panel, which "fixed" the problem for about a week, but now it's back.  This hasn't been an issue for me in Karmic (9.10), but started with Lucid (fresh install, not an upgrade). More to come...

---

### Post by MrVas on 2010-06-12
It happened again this morning.  I have recreated the upper panel bar in about two minutes, so it's no longer as annoying as it was at first. Does anyone know where the configuration settings are stored in the profile? Somewhere under ~/.gconf?  I'll do some more research and report back.

Vas

---

### Post by MrVas on 2010-07-05
It has been about three weeks since the Gnome Panel "shifted". When I recreated the panel last time, I didn't select the "Expand" checkbox in Properties and so far it's been working without any issues.

Vas

---

### Post by sikumbuzo on 2010-08-06
I am having the same problem.  The GNOME Panel always loads in the correct position when the 'Expand' property is checked.  However, when the 'Expand' property is not checked, the Panel always loads right, smack in the middle of the screen.

The only way I've been able to get the Panel back to the correct position is to check 'Expand' and then uncheck 'Expand'.  For some reason, that places it back against the bottom of the screen.

Obviously, I don't want to keep having to do this.  Could anyone point me to a solution?

---

### Post by Richard85 on 2010-09-12
I'm having this problem too!

I was customizing my desktop and I decided I wanted to try out a dock so I installed docky, cairo dock, and awn via ubuntu tweak. Fortunately for me, docky decided it wanted to boot at startup. When this happened, my applications panel bar appeared right in the middle of the screen.
So I uninstalled docky through ubuntu tweak and it seemed to resolve the problem. Unfortunately for me, I kept trying out the other docks. Opening cairo dock brought about the same problem for the applications panel bar. Something that should be noted is that I do not expand my panel bar. This problem doesn't happen if the panel bar is expanded.
I've uninstalled AWN and Cairo Dock via ubuntu tweak but the problem remains. Attached is a screenshot of what my desktop looks like when I log in.

---

### Post by Richard85 on 2010-09-12
MrVas, my panel is being jumbled in the _exact_ same manner as yours.
Very weird and annoying!](*,)

---

### Post by Richard85 on 2010-09-13
I read on another form about a little program called Pessulus that you can get through Synaptic that lets you mess with gconf. There's an option to lock down the panel. But unfortunately, my panel is still jumbled albeit locked down and not in the middle of the screen.
Hopefully others might have success with this.

---

### Post by MrVas on 2010-11-07
Just a quick update.

After my last update from July 5th, 2010, I haven't see this issue again. I do patch my system on somewhat regular basis (about every two weeks), so I'm not sure if there has been a patch, or if not using the "expand" feature took care of it.

Vas

---

### Post by levesque on 2010-12-19
I had a panel expanded along the bottom and a non-expanded panel along the right edge. When I rebooted the right panel would appear in the middle of the screen. Not only that but my panels are auto-hide, so when I would put my mouse on the right side of the screen the panel would unhide to the middle of the screen and then it would immediatly autohide because my mouse was still on the edge of screen so it would then immediatly unhide again and so on the panel oscillating from the side of the screen to middle.

So, I put my mouse on the right side of the screen right clicking until I managed to get some preference window open from the side panel so the panel then stayed unhiden in the middle of the screen. I'm pretty sure I then managed to open the panel's properties and then I dragged the panel to the right edge of the screen. Then rebooted and all was how it should be: a non-expanded auto-hide panel on the right and a expanded autohide panel on the bottom.

---

