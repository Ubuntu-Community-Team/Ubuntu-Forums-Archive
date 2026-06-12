---
title: "what is the command to launch &lt;Alt&gt;&lt;F2&gt; dialog?"
date: 2009-08-10
forum: General Help
---

### Post by sam1948 on 2009-08-10
I want to create a launcher for this because of a problem with that key's bindings in 9.04

---

### Post by jaxxstorm on 2009-08-10
Install the program gmrun from synaptic

```

sudo apt-get install gmrun

```

it provides identical functionality but is lighter on resources. Then make a launcher with the command 
```
gmrun
```

---

### Post by mcduck on 2009-08-10
> **sam1948 said:**
> I want to create a launcher for this because of a problem with that key's bindings in 9.04

There isn't any command for it, as it's not a program but just a built-in feature of the Gnome-panel.

If you want a similar run dialog that can be launched with a command (and works without Gnome-panel), then follow jaxxstorm's suggestion and install gmrun.

..or fix the problem from the other end, and change whatever program you have now conflicting with the shortcut to use some other keys instead. ;)

---

### Post by josephpiche on 2009-08-10
I would try using the "Run Application..." applet or the deskbar applet of the panel. What I do is map the terminal to a keyboard shortcut like Alt-backtick, which works very nicely.

---

