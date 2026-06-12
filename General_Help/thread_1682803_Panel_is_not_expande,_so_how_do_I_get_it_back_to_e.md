---
title: "Panel is not expande, so how do I get it back to expanded?"
date: 2011-02-06
forum: General Help
---

### Post by jlh68 on 2011-02-06
I somehow un-expanded my panel.  The problem is that now there is NO Open space to click to get the panel menu (panel properties) back to click expand.  So how do I do it?

---

### Post by spaceboy909 on 2011-02-06
Ah yes, one of the many pains of Gnome design.  I've struggled with this countless times.

At the end points of each section of the panel, there is, believe it or not, a teeny tiny little spot that lies between panel sections.  You just have to keep clicking over and over until you land on it.  There's no visual cue to point you to it; just click many times between the panel sections until the proper menu comes up.

Turn up your brightness, use both hands on the mouse, pucker up and pray to whichever god you serve! After about 10 seconds of fiddling around, I can usually nail it.

Maybe someone else here has an easier solution......

---

### Post by Krytarik on 2011-02-06
Yeah, I love this too. Usually occurs when trying to move item in the tray area, I usually manage it after clicking around a while.

But, if you can't manage it, each of those settings can also be adjusted by using "gconf-editor", in your case:
- press Alt+F2
- enter "gconf-editor"
- browse to "/apps/panel/toplevels/bottom_panel_screen0", respectively "/apps/panel/toplevels/top_panel_screen0"
- tick the option "expand"

---

### Post by jlh68 on 2011-02-07
Thanks to both of you: **spaceboy909** and **Krytarik**.  I was able to used **spaceboy909**'s suggestion on the very first click.  I also went back and checked out **Krytarik**'s suggestion.  both were winners.  Thanks for replying.  I also found that if [Configuration Editor] is checked using the Main Panel set up one can get the same menus as **Krytarik**.  I just hope I remember these suggestion the next time I mess up my panels.

---

### Post by Krytarik on 2011-02-07
> **jlh68 said:**
> I also found that if [Configuration Editor] is checked using the Main Panel set up one can get the same menus as **Krytarik**.
Yeah, surely you mean "Main Menu". But I usually want to keep it simple, not having to explain before, how to activate that in the menu, in order to start with the real task.;-)

---

### Post by jlh68 on 2011-02-07
**Krytarik**you are right again, I did mean the Main Menu.  Sometimes the fingers type something other than what the brain meant.

---

