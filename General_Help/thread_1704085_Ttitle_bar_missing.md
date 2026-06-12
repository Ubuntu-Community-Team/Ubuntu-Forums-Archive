---
title: "Ttitle bar missing"
date: 2011-03-10
forum: General Help
---

### Post by andygait on 2011-03-10
I'm running Ubuntu 10.10 64bit and my title bar keeps going walkabout. Sometimes it's there, sometimes it's not. I installed Gnome Shell a few days ago and that's when the problem started. I then uninstalled it in the hope that this would resolve the issue, but no.

Any ideas?

:)

---

### Post by Rushyang on 2011-03-10
Open terminal, try...

gtk-window-decorator --replace compiz & 

or

compize --replace &

---

### Post by prshah on 2011-03-10
> **andygait said:**
> my title bar keeps going

Is it only the title bar or all window decorations (min/max buttons, borders, etc)? 

It looks like the window decorator is crashing. You can check by giving the following command when next you find this problem; press alt+f2, and give the command ```
gtk-window-decorator --replace
``` If that doesn't work as expected, then try ```
compiz-decorator --replace
``` or ```
x-window-decorator --replace
``` (You can change the order if you feel suitable).

If either of these commands give you back the title bar (and window decorations) then you have to find out why that particular decorator is crashing. Please post back if need suggestions on this.

If neither of these give you back your title bar then probably your entire window manager is affected; try ```
compiz --replace
``` or ```
metacity --replace
```

---

### Post by andygait on 2011-03-10
> **prshah said:**
> Is it only the title bar or all window decorations (min/max buttons, borders, etc)? 

It's the min/max buttons and borders (I lose the border between menu and desktop for example). I reboot and it might come back, it might not. 

At the moment all is OK but I'm sure on a reboot in the next day or two it will go again. 

Thanks for the advice. I'll give it a try.

---

### Post by andygait on 2011-03-11
I used this and all seems to be OK now.
"gtk-window-decorator --replace"


 Thanks again. :D

---

### Post by jorok_tupur on 2011-03-25
> **Rushyang said:**
> Open terminal, try...

gtk-window-decorator --replace compiz & 

or

compiz --replace &

The last one works for me. Thank you.

---

