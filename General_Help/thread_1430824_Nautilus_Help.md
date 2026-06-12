---
title: "Nautilus Help"
date: 2010-03-15
forum: General Help
---

### Post by CheckExplicit on 2010-03-15
I just recently installed Nautilus, or upgraded, from whatever was pre-installed with Ubuntu 9.10.

I accidentally clicked Hide Menu toolbar, which apparently in this, there's no way to unhide it. The only thing showing now is the Sidebar, and I don't know how to get any of the toolbars back. 

[http://tinypic.com/r/a5bx5k/5](http://tinypic.com/r/a5bx5k/5)

---

### Post by kazakore on 2010-03-15
Think I did this and just closing it and reopening worked for me. Although now I can't even find a option to hide the menu...

---

### Post by fragos on 2010-03-15
I saw this happen one to me when a sadistic web site took control while surfing with beta Google Chrome. The only way out was to kill the Chrome. I ended up with this same problem in my system. I couldn't find a way to configure even with the configuration editor. I did a reinstall of Ubuntu.

---

### Post by howefield on 2010-03-16
> **CheckExplicit said:**
> I accidentally clicked Hide Menu toolbar, which apparently in this, there's no way to unhide it.

Try pressing Alt+F2 to get a Run box, and type gconf-editor into it and press enter.

Navigate in the left window pane to apps > nautilus > preferences and near the bottom of the right hand pane you will find a load of "start_with" options. Place a check against"start_with_toolbar" and close your way back out.

Next time you open Nautilus, you should be good to go. (with a toolbar :)  )

---

