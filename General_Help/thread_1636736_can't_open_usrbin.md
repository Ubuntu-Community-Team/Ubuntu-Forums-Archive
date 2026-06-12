---
title: "can't open /usr/bin"
date: 2010-12-03
forum: General Help
---

### Post by Nugget_Mon on 2010-12-03
I am trying to open /usr/bin in nautilus as root. I have used the shell script "Browse as Root" in /.gnome2/nautilus-scripts also I have used nautilus-gksu context menu item. I can access the directory though the terminal, getting to the files isn't the problem, I just can't see why I can't open the directory with nautilus. Any Ideas?

---

### Post by WorMzy on 2010-12-03
Why do you want to?

Open a terminal (Applications -> Accessories -> Terminal), type ```
gksu nautilus /usr/bin
``` and press enter, and it should bring it up. If it doesn't, then it should give some indication as to why it didn't.

---

### Post by Nugget_Mon on 2010-12-03
> **WorMzy said:**
> Why do you want to?

Because it's an option!?


Open a terminal (Applications -> Accessories -> Terminal), type ```
gksu nautilus /usr/bin
``` and press enter, and it should bring it up. If it doesn't, then it should give some indication as to why it didn't.

Window starts to open then closes. The terminal has this:

```

r@Lap-ubu-10:~$ gksu nautilus /usr/bin
Initializing nautilus-dropbox 0.6.2
Initializing nautilus-gdu extension

```

My dropbox just updated to 0.7.10, however I'm not sharing this directory.

---

### Post by WorMzy on 2010-12-03
You want to do it because you can do it? Fair enough I guess, but that seems totally pointless to me.

Can you open nautilus as root in any other directory? What about other apps?

```
gksu nautilus
```

```
gksu gedit
```

---

### Post by Nugget_Mon on 2010-12-04
Yes I can open any other directory I have tried. Any other apps as well.
I stopped dropbox because I noticed it was updating whenever I was trying to open the directory. Yet still had:
"Initializing nautilus-dropbox 0.6.2"
I've checked the system monitor and dropbox wasn't showing up there.

I uninstalled dropbox 0.6.2 through synaptic and lost that "error", however the directory still won't open.

---

### Post by WorMzy on 2010-12-04
From these other directories, can you navigate to /usr/bin, or does it crash nautilus when you try to open it?

---

### Post by bhavin137 on 2010-12-08
Hey, did ne1 find a solution to this problem? I too got the same problem. I suspect it crept when I was changing permission/executibility of files using chown, chmod, etc. Its most probably got 2 do something with permission but don't know for sure.
I'm stuck big tym....som1 pls help [-o<

---

### Post by WorMzy on 2010-12-08
Permissions shouldn't affect nautilus if it's run with gksu. Have you tried the things I've previously suggested?

---

### Post by tenfishsticks on 2011-05-07
I've got the same problem, as well as Nautilus not able to access any of my folders from the toolbar.  Running the command: 
```

$ gksu nautilus /usr/bin
Initializing nautilus-gdu extension

```

The window pops up for a moment, then closes.  Any ideas?

---

