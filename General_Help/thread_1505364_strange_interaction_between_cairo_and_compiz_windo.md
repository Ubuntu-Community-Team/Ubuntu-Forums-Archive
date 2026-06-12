---
title: "strange interaction between cairo and compiz window preview plugin"
date: 2010-06-09
forum: General Help
---

### Post by e64462 on 2010-06-09
Ubuntu 9.10 
Kernel 2.6.32-22-generic

I'm attempting to replace gnome-panel with cairo (also called glx dock), but I'm noticing some strange interaction between cairo and compiz. I have the Window Previews compiz plugin enabled, but the cairo dock only previews the window when the window is already visible on the desktop. If the window is minimized, the plugin doesn't seem to work. Have I missed a crucial configuration option somewhere? I'll attach some screenshots to try to clarify the problem. Notice the placement of the mouse over the left-most icon on my dock in both screenshots.

---

### Post by fabounet on 2010-06-09
the crucial part you're missing is that X does not allow to have thumbnail of a window when it's minimized :)
therfore Compiz can't make a preview in this case.
this is made to optimize ressources (as they say), since a minimized window is supposed to be invisible (of course they didn't think of previews when they did it ^^ )

---

### Post by e64462 on 2010-06-09
well... that's just about the silliest thing I've ever heard. Thanks for the info though! I guess I just get to live with it.

---

