---
title: "Maximus makes my panel invisible"
date: 2010-12-05
forum: General Help
---

### Post by Svento on 2010-12-05
If I use the program Maximus and set it to undecorate the titel bar, after a while my panel goes invisible. If I close a maximized Nautilus window, it always goes invisible immediatly. The panel is not hidden or disappeared, just invisible. I can still click everything in the panel.

Any ideas how to fix this?

---

### Post by drewsus on 2010-12-05
Alt+F2 (or in terminal):
```
killall gnome-panel
```
Should bring it back. Don't know about fixing this permanently.

---

### Post by Svento on 2010-12-05
I can solvethe problem temporarilly by setting the panel to hide automatically. Then it comes back and I can set it not to hide.

But I need a permanent solution - until then I'll try to live with a titelbar in my program windows...

---

### Post by hasanaa on 2010-12-10
any solution please? i have the same problem...

---

### Post by kerry_s on 2010-12-10
go in to gconf-editor & uncheck undecorate for maximus.

it's a maximus + composting problem. 
if your using compiz, use that to maximize your windows & undecorate, there's no need for maximus.

---

### Post by susema on 2010-12-12
This solved with;

```
rm -rf .gconfd .gconf .gnome2 .config
```

---

### Post by drewsus on 2010-12-12
***before you tell people to remove configuration files, advice them how to back them up so they can restore them if you "solution" does not work for them.***

---

### Post by susema on 2010-12-12
> **drewsus said:**
> ***_[COLOR=red][SIZE=4][SIZE=2]before you tell people to remove configuration files, advice them how to back them up so they can restore them if you "solution" does not work for them.[/SIZE] [/SIZE][/COLOR]_***

Yes, you're right. Sorry. Before try, back up those directories (.gconf .gconfd .gnome2 .config, Ctrl + H)  in your home directory, for example move them on desktop.

And you don't have to write too large and red.  I see :)

---

### Post by drewsus on 2010-12-12
I know I know, I just have an exam in 30 minutes and wanted that to be seen. Otherwise, I would have said it much politer and provided how to back the stuff up! I don't want to discourage people helping others!

---

### Post by susema on 2010-12-12
> **drewsus said:**
> I know I know, I just have an exam in 30 minutes and wanted that to be seen. Otherwise, I would have said it much politer and provided how to back the stuff up! I don't want to discourage people helping others!

Ok.. No problem :)

---

