---
title: "Unity weirdness/awkward window placement"
date: 2012-08-15
forum: General Help
---

### Post by HuaiDan on 2012-08-15
I recently online-upgraded to Precise on my desktop a couple of days ago, and still working out the kinks. I thought I'd experiment and give the new Unity a shot, as I do much of my work/play on my laptop, which runs OpenSuse12.1/KDE4.8.

Anyway, to cut to the chase, I'm not too happy with the placement Unity chooses for newly-opened window. See [COLOR="Red"]**screenshot 1**[/COLOR].


Notice the terminal window in the upper left. The title bar, along with the minimize/maximize/close buttons, are covered by the Unity panel when I start the terminal. It does, in fact, display the global menu when I focus on that window, but that only gives me the option to file/close or view/full screen the window, but not minimize or maximize. I also can't grab the title bar to move the window, which means I have to press an extra key (alt) if I want to use the mouse to move the window. If I do move the window then maximize it, then I get my mn/mx/close buttons as I'm supposed to.

I can get the window to open with the title bar in view if I go into compiz and enable "place windows" with the "random" option, but this seems really buggy to me. By enabling this option, I can't move the windows to where ever I want them, because compiz will then move the window to where ever it wants to.  For example, if I move the window  half-off the the desktop on the lower right, compiz will then make the window jump to the lower left, fully displayed on the desktop. This option does not let me move any window half-off the screen. See the [COLOR="Red"]**second screenshot**[/COLOR] to get an idea of what IS NOT allowed. Even when I don't want to move a window off the screen as indicated, Compiz usually has its own ideas about where it wants to place the windows.

In the [COLOR="Red"]**third screenshot**[/COLOR], you can see an example of the desired result with the placement of the terminal window upon opening. However, I had to place them manually in this position.

Is there any way I can have the windows open anywhere on the desktop EXCEPT with the title bar hidden by the Unity panel, and such that I can move the window anywhere I want to afterwards?

(tip: from what I discovered, if you want to edit compiz settings without it crashing so frequently, kill unity then disenable the unity compiz plugin befoe making any other changes in compiz. It will still crash occasionally, just not as often.)

---

### Post by HuaiDan on 2012-08-15
So far, the only applications I've noticed this strange behavior with  are terminal, gedit, calc, compiz manager, nautilus, and amarok. Other applications seem ok: Libreoffice, firefox, gimp, transmission. Some applications do it, some don't. What's the difference?
BTW, are global menus always supposed to show the window control buttons of the active app, or only when that window is maximized? If only when maximized, I might consider disabling global menus.

---

### Post by HuaiDan on 2012-08-15
Apparently, the "place" option in compiz wasn't working correctly for some odd reason. I killed Unity, reset compiz with "place" enabled, rebooted, and the problem appears resolved.

---

