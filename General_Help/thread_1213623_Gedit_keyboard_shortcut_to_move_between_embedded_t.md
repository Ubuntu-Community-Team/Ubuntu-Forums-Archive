---
title: "Gedit keyboard shortcut to move between embedded terminal and editor box"
date: 2009-07-15
forum: General Help
---

### Post by mdgrech on 2009-07-15
So I have gedit opened using the embedded terminal plugin. Is there a key board shortcut to move the cursor from the editor to embedded terminal? 

This is kind of important b/c sometimes I'll copy text from an external source, go to paste it into the editor, and won't see that the cursor is in embedded terminal and it gets pasted to the wrong spot.

-Helpless in gedit

---

### Post by francesco.spegni on 2010-09-29
hi, 

this thread is quite old but googling i didn't find any solution to this problem, and i'd like to do that.

did anybody come up with a solution? :)

---

### Post by sebx8600 on 2011-03-03
> **mdgrech said:**
> So I have gedit opened using the embedded terminal plugin. Is there a key board shortcut to move the cursor from the editor to embedded terminal? 

This is kind of important b/c sometimes I'll copy text from an external source, go to paste it into the editor, and won't see that the cursor is in embedded terminal and it gets pasted to the wrong spot.

-Helpless in gedit

Use F8 then press the tab key: it works while coding in python

---

### Post by carandraug on 2011-05-31
> **sebx8600 said:**
> Use F8 then press the tab key: it works while coding in python
This seems to work only to get from the text edit window to the terminal but not the other way around.

There's at least 2 bug reports on bugzilla about it. Maybe you should report there that it also affects you?
[https://bugzilla.gnome.org/show_bug.cgi?id=610978](https://bugzilla.gnome.org/show_bug.cgi?id=610978)
[https://bugzilla.gnome.org/show_bug.cgi?id=649120](https://bugzilla.gnome.org/show_bug.cgi?id=649120)

---

### Post by oldnik on 2012-10-26
1. Activate External tools plugin.
2. goto  Tools > Manage External Tools
3. add the code
```
#!/bin/sh
python2.7 $GEDIT_CURRENT_DOCUMENT_NAME
```
and add a hotkey to execute.
That's it folks!

---

