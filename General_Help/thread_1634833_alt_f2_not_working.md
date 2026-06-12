---
title: "alt f2 not working?"
date: 2010-12-01
forum: General Help
---

### Post by TNT1 on 2010-12-01
Toshiba M400, 10.04.1, single Gnome Panel, alt f1 and alt f2 do nothing. What could be the problem? The ctrl alt f* work fine.

---

### Post by anubhavrocks on 2010-12-01
Can you do a 
killall gnome-panel 

and then try again.

---

### Post by 3rdalbum on 2010-12-01
It only works with Metacity or Compiz window managers. If your window manager has crashed, the keyboard shortcut doesn't work. Same applies if you are using another window manager such as Openbox.

---

### Post by TNT1 on 2010-12-01
> **anubhavrocks said:**
> Can you do a 
killall gnome-panel 

and then try again.

Will try that when I get home and report.

---

### Post by TNT1 on 2010-12-01
> **3rdalbum said:**
> It only works with Metacity or Compiz window managers. If your window manager has crashed, the keyboard shortcut doesn't work. Same applies if you are using another window manager such as Openbox.
Compiz, and it is running.

---

### Post by killa.fr0gg on 2010-12-01
Another thing to check (usually stuff like this is simpler than it seems) is whether or not those fn keys have hardware-mapped functions. For example, on my computer, f1 and f2 are set to adjust screen brightness. If this is the case, you will also need to hold down the fn key itself while making the keystroke. Personal exerience, maybe I'm off in your case, but I would recommend looking at that at least for random wanderers-through.

Cheers!

---

### Post by TNT1 on 2010-12-01
> **killa.fr0gg said:**
> Another thing to check (usually stuff like this is simpler than it seems) is whether or not those fn keys have hardware-mapped functions. For example, on my computer, f1 and f2 are set to adjust screen brightness. If this is the case, you will also need to hold down the fn key itself while making the keystroke. Personal exerience, maybe I'm off in your case, but I would recommend looking at that at least for random wanderers-through.

Cheers!

Thanks, I'll look into it, but "alt f2" used to work...

---

### Post by xircon on 2010-12-01
Open ccsm and check Gnome compatibility is ticked and the key bindings are correct.

---

### Post by Jeffrey Magder on 2011-03-12
> **xircon said:**
> Open ccsm and check Gnome compatibility is ticked and the key bindings are correct.
Fantastic, that did the trick!

---

### Post by markackerman8@gmail.com on 2011-04-06
phewwww me too, a pain in the but finally solved, thanks

---

