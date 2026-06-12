---
title: "Top Panel MIA"
date: 2010-10-21
forum: General Help
---

### Post by jlangholzj on 2010-10-21
so my top panel has completely disapeared, only not really. There's a big empty space on the top of my screen when i maximize anything. like its recongnizing that its there, only nothing shows. 

I've tried everything in this thread already

[http://ubuntu-virginia.ubuntuforums.org/showthread.php?t=1526755&page=2](http://ubuntu-virginia.ubuntuforums.org/showthread.php?t=1526755&page=2)

and I've got nothin. I've also tried adding a new panel but its down from the top edge, again like something is still there.

ideas?

---

### Post by plucky on 2010-10-22
Open a terminal and copy and paste each command```
gconftool-2 --shutdown    

rm -rf ~/.gconf/apps/panel

pkill gnome-panel
```

This will reset the panels to default,so if you have anything special setup in the panels it will change and you will have to re-install it.

Good Luck

---

### Post by JOHNNYG713 on 2010-10-22
Try adjusting your monitor screen height, The controls on the monitor itself!

---

### Post by jlangholzj on 2010-10-22
> **plucky said:**
> Open a terminal and copy and paste each command```
gconftool-2 --shutdown    

rm -rf ~/.gconf/apps/panel

pkill gnome-panel
```

This will reset the panels to default,so if you have anything special setup in the panels it will change and you will have to re-install it.

Good Luck


you obviously never spent the time to look through the other thread. And if you did you must have missed it

thats been tried and it isn't working.

adjusting the monitor does nothing.....its not that I'm out of limits, its like the menu is "invisible" but still leaves a footprint.

forgot to mention that I'm using 10.10 now, this happened with 10.04 as well but i could usually get it to come back.

---

### Post by jlangholzj on 2010-10-24
bumpidy? buelller....anyone?

---

