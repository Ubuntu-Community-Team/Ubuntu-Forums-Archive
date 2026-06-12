---
title: "how to launch all applications full screen"
date: 2012-10-09
forum: General Help
---

### Post by rmcellig on 2012-10-09
I am using Xubuntu 12.04.

Is there a way to have all of my applications open maximized instead of always having to resize windows after launching an application? Do I have to put special code in the command for each application and/or can I configure my machine to always open every app maximized?

---

### Post by pqwoerituytrueiwoq on 2012-10-09
i dont think every program even has full screen or did you mean maximized
if it is maximized you can hit [Alt]+[F7] (Applications -> Settings Manager -> Window Manager -> Keyboard) most programs will remember they were maximized
if you meant fullscreen you may prefer unity with the side panel on autohide, maximized will be closer to fullscreen in unity

---

### Post by LewisTM on 2012-10-09
You can install package **maximus**. It will maximize and undecorate windows. You will still see the panels though so it won't be a real fullscreen.

Alt-F11 will make any window fullscreen.

---

### Post by rmcellig on 2012-10-09
Sorry about that I meant always open maximized.

---

### Post by LewisTM on 2012-10-09
Then maximus will work for you.
To keep the window decorations (title bar, buttons) go to gconf-editor/apps/maximus and uncheck 'undercorate'

Cheers!

---

### Post by Merrattic on 2012-10-10
Thanks for this LewisTM, works well and is better with "undecorate" unticked. Does pull in a few gnome related dependencies. Gives a more consistent desktop experience.

```
sudo apt-get install maximus gconf-editor
```

Would be nice to have a floating mini "ALT+TAB" display on screen to go with this, save moving hand from mouse ;)

---

### Post by rmcellig on 2012-10-10
So now all of my windows open maximized, how do I set it so that every window I open is unmaximized?

---

### Post by LewisTM on 2012-10-10
:confused:
You asked how to set windows to open maximized. The solution worked, right? If you don't want it, remove maximus.
Or am I missing something?

EDIT: You probably mean how to prevent windows from opening in maximized mode on launch. I don't think you can set Xfwm4 to do that. Compiz might have that option.

---

### Post by rmcellig on 2012-10-10
I know that it sounds confusing. Maximus worked. So I just have to uninstall maximus and the windows will open without maximizing? I just want to be sure. Sorry for being such a pain. :)

---

### Post by LewisTM on 2012-10-10
> **rmcellig said:**
> I know that it sounds confusing. Maximus worked. So I just have to uninstall maximus and the windows will open without maximizing? I just want to be sure. Sorry for being such a pain. :)
No problem. The windows will revert to their original behavior. If you close a maximized window and then launch the app again, it will spawn maximized. Same for unmaximized windows. The WM will even try to restore the previous window dimensions.

---

### Post by rmcellig on 2012-10-10
Thanks for getting back to me.

---

### Post by Merrattic on 2012-10-10
> **Merrattic said:**
> Would be nice to have a floating mini "ALT+TAB" display on screen to go with this, save moving hand from mouse ;)

Cool just found by accident that if you use the mouse wheel when hovering over the "Windows Buttons" plugin on the panel it scrolls through the the available windows :)

---

