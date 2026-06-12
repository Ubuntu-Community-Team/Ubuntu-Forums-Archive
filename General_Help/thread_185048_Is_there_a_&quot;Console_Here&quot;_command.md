---
title: "Is there a &quot;Console Here&quot; command?"
date: 2006-05-31
forum: General Help
---

### Post by ripkirby on 2006-05-31
I have just switched over from Windows (hate.. WGA) and I've been tired using "cd ...." all the time. I was wondering is there a way to add a "Run Console Here" onto the right click menu or at least create shortcuts to my Wine applications.

---

### Post by blackjack6.21.91 on 2006-05-31
You might just be able to right click a directory and open it with "terminal".  But if anyone knows of a script to add to the context menu, that would be even more useful!

---

### Post by chriscando on 2006-05-31
Try using Konqueror (install through synaptic if you dont have it). When browsing your filesystem you can right-click> Actions > open terminal here.

Is this what you were looking for?

---

### Post by ripkirby on 2006-05-31
Yes, that is what I'm looking for. However, Is there still a way to add it in context menu in Ubuntu, like blackjack said?

---

### Post by nanotube on 2006-05-31
yes there is... 
just create a small shell script, with these contents:
```
#!/bin/bash
gnome-terminal
```
and then place it into 
~/.gnome2/nautilus-scripts directory.
then, you can right-click on any directory, and select "terminal" from your scripts submenu, and it will open a terminal there.

---

### Post by tigrux on 2006-05-31
Install nautilus-open-terminal from Universe repo.

---

### Post by indigoblu on 2006-05-31
gnome open-terminal-here 

this and many more at g-scripts website!


[http://g-scripts.sourceforge.net/cat-executing.php#terminal](http://g-scripts.sourceforge.net/cat-executing.php#terminal)

---

