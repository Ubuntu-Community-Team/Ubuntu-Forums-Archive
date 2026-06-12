---
title: "Keeping &quot;Show Hidden Files&quot; unchecked"
date: 2010-01-05
forum: General Help
---

### Post by Eterniam on 2010-01-05
Hey there,

I want hidden files to be hidden, so I open the folder that has the hidden files in it and select View, and untick "Show Hidden Files". However, when I access the folder again the box is ticked and the files are showing. How can I get it to stay hidden permanently?

Thanks

---

### Post by mcduck on 2010-01-05
The option is in the file manager's preferences. (Edit/(Preferences, and on the "View"-tab deselected "Show hidden and backup files").


The option in View menu affects the current directory, the setting in preferences sets the default.

---

### Post by drs305 on 2010-01-05
You should be able to turn them off universally with this command, although I don't know what's turning them back on in your case unless you are looking at different folders:
```

gconftool-2 -t bool -s /desktop/gnome/file_views/show_hidden_files false

```

---

### Post by Eterniam on 2010-01-05
Thank-you. I used the second method, and it worked. :)

---

### Post by hariks0 on 2010-01-05
Wonder why nobody suggested Ctrl+H. 
Anyway, mark it as 'Solved'.

---

### Post by mcduck on 2010-01-05
> **hariks0 said:**
> Wonder why nobody suggested Ctrl+H. 
Anyway, mark it as 'Solved'.

Ctrl-H, like the option in View menu, affects current directory but doesn't set the default.

Both gconf setting and the option in the Nautilus preferences do the same thing. (Nautilus stores it's settings in gconf so it's not even a different setting affecting the same preference, it's exactly the same setting both these tools configure)

---

