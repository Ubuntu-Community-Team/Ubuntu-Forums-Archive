---
title: "Question about XFCE, Metacity and Compiz"
date: 2011-05-12
forum: General Help
---

### Post by layers on 2011-05-12
I would like to know what the difference between the three is.

As far, I know that XFCE is in the same category as Gnome, KDE, Fluxbox, etc. and it is officially called a window manager. I do not however know what exactly it does, nor the other two. Can someone try to explain with two words?

---

### Post by 3 frags left on 2011-05-12
In a nutshell:

XFCE: A graphical interface aimed for old/tame hardware PCs. Looks like Gnome, but lighter. My choice of interface btw.
Metacity: A **window manager**, which means he is going to draw the windows style, color, buttons, and stuff like that. I prefer Emerald, but YMMV.
Compiz: A **compositing manager**, responsible for enhancing your graphical interface experience. Its features range from the useful desktop cube screen switch to eye-candy such as minimize animations.

---

### Post by layers on 2011-05-12
> **3 frags left said:**
> In a nutshell:

XFCE: A graphical interface aimed for old/tame hardware PCs. Looks like Gnome, but lighter. My choice of interface btw.
Metacity: A **window manager**, which means he is going to draw the windows style, color, buttons, and stuff like that. I prefer Emerald, but YMMV.
Compiz: A **compositing manager**, responsible for enhancing your graphical interface experience. Its features range from the useful desktop cube screen switch to eye-candy such as minimize animations.
Aah... same here for the the windows manager, but I think whenever I start, metacity starts, then it stops, and then Emerald loads up. Do you have the same thing going on?

And "compiz --replace" starts both compiz and emerald?

---

### Post by 3 frags left on 2011-05-12
Not exactly. It depends on which window manager you have commanded Compiz to open along with it. To set this, go to Effects > Window Decorator; in there, there's a field called Command; to set Metacity, type metacity --replace, or if you want Emerald, type emerald --replace.

Also, to have Compiz at startup, go to Settings > Settings Manager (at your main menu) and select Session and Startup. Under the "Application autostart" tab, add the command "compiz --replace".

---

### Post by layers on 2011-05-12
> **3 frags left said:**
> Not exactly. It depends on which window manager you have commanded Compiz to open along with it. To set this, go to Effects > Window Decorator; in there, there's a field called Command; to set Metacity, type metacity --replace, or if you want Emerald, type emerald --replace.

Also, to have Compiz at startup, go to Settings > Settings Manager (at your main menu) and select Session and Startup. Under the "Application autostart" tab, add the command "compiz --replace".
Then, if I'm not wrong, you do have the same thing happening - something else loads up before the "compiz --replace" command is executed. Is that what you're using?

---

### Post by layers on 2011-05-13
Well, installing fusion-icon, has let me know that I currently have these 4 installed.

Window Managers:
-Compiz
-Xfwm4

Window Decorators:
-GTK Window Decorator
-Emerald

Can someone tell  me how to turn on and off Xfwm4 and GTK Window decorator? MOst importantly, I know that they load in the begnning, and I am trying to make them not to. Help please?

---

