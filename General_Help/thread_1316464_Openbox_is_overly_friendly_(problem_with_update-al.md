---
title: "Openbox is overly friendly (problem with update-alternatives)"
date: 2009-11-06
forum: General Help
---

### Post by hellomynameisphil on 2009-11-06
Hi all,

Just installed Karmic on my eee pc. Went from the minimal iso so I don't have any desktop environment installed, and so far only openbox and fluxbox as window managers. 

I am trying to use update-alternatives to switch between them so I can ultimately decide which one to use, but after installing openbox, I can't use fluxbox, even if it should be the window manager that gets used. 

```

$ update-alternatives --display x-window-manager
x-window-manager - auto mode
 link currently points to /usr/bin/startfluxbox
/usr/bin/openbox - priority 50
 slave x-window-manager.1.gz: /usr/share/man/man1/openbox.1.gz
/usr/bin/startfluxbox - priority 90
 slave x-window-manager.1.gz: /usr/share/man/man1/fluxbox.1.gz
Current `best' version is /usr/bin/startfluxbox.

```

But despite this, startx always brings me to openbox (I don't currently have a display manager installed, as sometimes I like to work without X).

Any thoughts on why this might be?

---

### Post by nothingspecial on 2009-11-06
Have you got ```
openbox-session
``` in your .xinitrc?

That could be it.

---

### Post by hellomynameisphil on 2009-11-06
I didn't actually have an .xinitrc when I posted this, but I made one and put '/usr/bin/startfluxbox' as the only line and can get into fluxbox that way. If I comment out the line, it goes into openbox. 

So my problem is solved, but it's a workaround rather than a fix. I'm still curious about why update-alternatives isn't doing its job here. What am I missing?

---

### Post by hellomynameisphil on 2009-11-06
And thanks for your reply, by the way.

---

