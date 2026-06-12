---
title: "Dockbarx. problem"
date: 2010-06-03
forum: General Help
---

### Post by elidoperezmd on 2010-06-03
I just installed Dockbarx...Draged to the pannel...but then opened it and try to figure it out....i Just don know how to make it run.... How can i make the magic happen?

Thanks for the help/replies/time

---

### Post by philinux on 2010-06-03
Moved to own thread.

---

### Post by elidoperezmd on 2010-06-03
> **philinux said:**
> Moved to own thread.

thanks...

---

### Post by M7S on 2010-06-03
Could you be more specific? The program doesn't start at all? All you see is the handle? Do you get an error message?



M7S,
DockbarX developer

---

### Post by elidoperezmd on 2010-06-03
> **M7S said:**
> Could you be more specific? The program doesn't start at all? All you see is the handle? Do you get an error message?



M7S,
DockbarX developer

Sorry that it took so long... i got the program installed and everything, got the applet in the panel... when i open it and sets the changes as i want and then close it, there is no preview on the thumbnails...im wondering if there is something that im supposed to be clicking on the dockbarx x application that im not click, i mean...to get the app going......???? does that makes sense?

---

### Post by M7S on 2010-06-04
So the only problem is previews not showing, right? Assuming you use version x.0.39.1, you have to enable the KDE compability plugin in compiz config manager and in the KDE compability plugin you should enable Support Plasma Thumbails.

---

### Post by elidoperezmd on 2010-06-04
> **M7S said:**
> So the only problem is previews not showing, right? Assuming you use version x.0.39.1, you have to enable the KDE compability plugin in compiz config manager and in the KDE compability plugin you should enable Support Plasma Thumbails.

Yeah. I did all that yheday before yestrdAy. But the magic did not and still not happening.... Uffgeydhhdd ( that's me being mad)

---

### Post by M7S on 2010-06-04
Ok, some dumb questions to be on the safe side.

1) You do have compiz running, right?
2) Check that DockbarX about dialog actually says version x.0.39.1

If you answer yes at both questions, next thing is to check for errors.
Run dockbarx in window with
```
dockbarx_factory.py run-in-window
```
and post the messages you get when you get the popup window opened.

---

### Post by elidoperezmd on 2010-06-04
> **M7S said:**
> Ok, some dumb questions to be on the safe side.

1) You do have compiz running, right?
2) Check that DockbarX about dialog actually says version x.0.39.1

If you answer yes at both questions, next thing is to check for errors.
Run dockbarx in window with
```
dockbarx_factory.py run-in-window
```
and post the messages you get when you get the popup window opened.

Yes to both questions...im sending an attached file because something happened that i want to show you....


See how the thumbnail is showing?  but only for those programs in the dockbarx_factory.py panel....not for the regular panel in the bottom...why is that?

but i have another question...is ther a correct set of options that must be enable in the program itslef to get it going? i mean...anything that must be checked/unchecked?


MS7, thanks 4 ur help..u r the only one helping...means a lot 2 me

---

### Post by the hoplite on 2010-06-07
Setting the KDE compatibility solved it for me. I'm using Gnome. Thanks.

---

### Post by M7S on 2010-06-07
I can't see dockbarx in that panel at all. Do you want previews for the normal window applet? That's done by adding compiz windows previews and has nothing to do with dockbarx. I'm not sure if that's what you mean, though. Can you make a screenshot that shows what's not working?

---

### Post by elidoperezmd on 2010-06-10
ok affter trying many many times back and forth...i got it running but only on the the AWN...sad not on the dock

---

