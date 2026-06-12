---
title: "Disappearing Toolbars"
date: 2012-04-08
forum: General Help
---

### Post by lemonoid on 2012-04-08
Ever since upgrading to 11.10, my Toolbars always seem to disappear after I've been on my computer for about 5 or ten minutes. This i s really aggravating as I have no option to maximize, minimize, or close a window, and I have to go all the way to the top of the screen to find the toolbar, instead of on top of the window that I'm currently in. This is very aggravating and I don't know as much as I'd like about the internals of this OS and it keeps pushing me away. I have always resorted back to Ubuntu from other things because I love the look of it, and its easy. But I always have ONE problem with every release that isn't HUGE but is big enough to really make me aggravated. I would really like to fix this one, but I've not been able to figure out how to. I can't find it in any of the system settings or preferences unless there is something I have overlooked.   :confused:    If anyone could possibly help me, it would be greatly appreciated. Thank you!

---

### Post by Gremlinzzz on 2012-04-09
Are you useing compiz if so/
u will need to edit a Compiz-Fusion setting, so open System > Preferences > CompizConfig Settings Manager. if it isn’t installed, just run sudo apt-get install compizconfig-settings-manager in a terminal.
Once open, scroll down to the Effects section, where you will see Window Decoration is not enabled. Simply click the check box to the left of it, and you should see your window borders reappear:popcorn:

---

### Post by lemonoid on 2012-04-09
It's funny that you ask that. I just posted a thread in another section relating to Compiz. When I installed 11.10 on this Laptop, I tried hard to get Compiz installed and configured to work right, but it just never seemed like it was working to me. Well, a little while ago (tonight) I realized that if I press Ctrl + Meta, a water effect appears on my screen, and if I move my mouse while holding the combination it looks as if I'm dragging my mouse through the water. Does this mean that Compiz is actually running and working?? The main thing I was trying to get with Compiz was the desktop cube, and then the window border and transition effects, but neither of those things would ever work.

---

### Post by lemonoid on 2012-04-09
Anyways, I just checked my Compiz settings and Window Decoration was already enabled.

---

### Post by Gremlinzzz on 2012-04-09
CompizConfig Settings Manager or CCSM is a configuration tool that can used for manipulating the Compiz settings of Ubuntu 11.10. Before installling the CCSM, you have to check whether your system supports compiz effects or not. For using CCSM, you must have a graphics card supporting 3D effects.

[http://peeqsource.com/2012/installing-compizconfig-settings-managerccsm-in-ubuntu-11-10/](http://peeqsource.com/2012/installing-compizconfig-settings-managerccsm-in-ubuntu-11-10/)

click the pictures on the site to make them zoom

---

