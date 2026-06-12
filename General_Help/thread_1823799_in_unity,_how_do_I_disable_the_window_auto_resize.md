---
title: "in unity, how do I disable the window auto resize?"
date: 2011-08-12
forum: General Help
---

### Post by ant2ne on 2011-08-12
Like, if I drag a window to the top of the screen, somehow this is supposed to mean I want the window full screen. Screw that if I wanted it full screen I'd have clicked the button on the top of the menu. Windows 7 does this too and it just as annoying.

---

### Post by JRV on 2011-08-12
```
sudo apt-get install compizconfig-settings-manager
```
```
ccsm
```

Uncheck the "Grid" in the "Window Management" category.

This will stop the window from maximizing when dragged to the top.

The window will still maximize if it fills more than 3/4 of the screen.  The fix for this will be in Oneiric.

---

### Post by ant2ne on 2011-08-12
Thanks!!

---

### Post by bo.vestergaard on 2011-08-13
Thanks a lot. That was annoying but now it works

---

### Post by adasilva on 2011-08-24
Thanks JRV! This is so much better.

---

### Post by abetterlie on 2011-08-25
Lifesaver! Cheers. 
Now I don't have to be afraid of my windows touching the edge of my screen.

---

### Post by johnsquibb on 2011-08-30
Thanks for this fix. This issue was seriously starting to get on my nerves.

---

### Post by thomas87 on 2012-04-04
For the sake of completeness, in case you don't have root access to your box, you can stil go to 

[INDENT]System Settings->Desktop->Screen Edges 
[/INDENT]
and uncheck the option  
[INDENT]"Maximize windows by dragging them to the top of the screen"
[/INDENT]
That did it for me (KDE 4.4.5, Ubuntu squeeze)

---

### Post by Lahmacun on 2013-02-25
Unity still does auto-site windows on my desktop even when disabling "grid".
you have to uncheck "scale windows", too (in deutsch: "Fenster skalieren")
otherwise it will still maximize the y-axis of the window when it touched the borders of the screen.

who did make such things a default option in the first way?
what a ridiculous fail.

[edit] ok, i described it wrong, i guess.
even after i unchecked "grid" some weeks before, ubuntu had a weird auto-resize activated on my desktop. this was just a "vertical" auto-resize. i just now got rid of it by checking some options in the window manager options screen in ccsm and then unchecking them again.
what a pain.

[edit2]
no, didn't fix it at all.
seems to be a bug still present in 12.10
happens from time to time but i havent been able to reproduce it, i will try and fill in a bug report.

---

