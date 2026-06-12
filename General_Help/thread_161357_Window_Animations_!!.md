---
title: "Window Animations ?!?!"
date: 2006-04-16
forum: General Help
---

### Post by it_broke_again on 2006-04-16
Hello everyone, I'm new to Ubuntu...but so far I've had next to no problems... For now, there's just one really, really, really irritating problem I have with the window animations...

I am running the newest version of Ubuntu, and every single time I minimize a window, there are these trailing black frames that appear until the window is completely minimized. 

Okay...now I did try the fix where you go to the Terminal and type "gconf-editor" and then enable "reduced_resources" under Apps-->Metacity-->General... Now, that solved the window minimizing animation problem, but created a new problem. Now, every time I drag a window to a new location there is this ugly black grid that comes up over the window I'm dragging. (The black grid does disappear when I stop holding down the mouse...) 

I, personally, can't decide which one to get rid of, they're both equally (and **increasingly**) annoying... I really would rather get rid of both of them...so if anyone out there has a fix that could get rid of these, I would really appreciate it...

P/S - Thank you, ahead of time, for any help or suggestions you have... :)

---

### Post by IYY on 2006-04-16
Metacity can be annoying like that. It's possible that you can't change this setting. You could use Gnome with a different wm though: xfwm4 would be my top-choice, since it can use Gnome themes, but you could also try something else.

---

### Post by codejunkie on 2006-04-16
open a terminal and enter ```
gconf-editor
``` navigate to **apps/metacity/general** and check the box that says **reduced_resources** close the configuration editor, then go into **System/Preferences/Assistive Technology Support**, and check the box that says enable assistive technologies and you shouldn't have to worry about the black frames around the windows anymore.

---

### Post by Teilanus on 2006-11-04
> **codejunkie said:**
> open a terminal and enter ```
gconf-editor
``` navigate to **apps/metacity/general** and check the box that says **reduced_resources** close the configuration editor, then go into **System/Preferences/Assistive Technology Support**, and check the box that says enable assistive technologies and you shouldn't have to worry about the black frames around the windows anymore.
Yay!:-D  No more frames, no more grids!:mrgreen:
Thank you!

---

### Post by hardyn on 2006-11-14
im running edgy, any reason i would not have a /System/Preferences/Assistive Technology Support?

i have a System, but there is no preferences below that?

thanks.

---

### Post by aysiu on 2006-11-14
> **hardyn said:**
> im running edgy, and reson i would not have a /System/Preferences/Assistive Technology Support?

i have a System, but there is no preferences below that?

thanks. I'm running Edgy, too, and it's there. Maybe you should use your menu editor to make sure that box is checked?

> **codejunkie said:**
> open a terminal and enter ```
gconf-editor
``` navigate to **apps/metacity/general** and check the box that says **reduced_resources** close the configuration editor, then go into **System/Preferences/Assistive Technology Support**, and check the box that says enable assistive technologies and you shouldn't have to worry about the black frames around the windows anymore. In Dapper, there was a bug that created an "empty" bookmark in Firefox bookmark subfolders when you enabled the Assistive Technology Support. Not sure if that's fixed for Edgy or not.

---

