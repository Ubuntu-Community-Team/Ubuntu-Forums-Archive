---
title: "[BASH] How to make it open a new tab?"
date: 2009-08-01
forum: General Help
---

### Post by Screatch on 2009-08-01
I need some operations done at once, therefore i decided to write a bash script that will all at once connect with SSH to all servers. But is there any way, every connection would be done in different tab?

---

### Post by SPr on 2009-08-01
I think you should be reading the manual for whichever terminal you use rather than the bash manual.

---

### Post by tokico on 2009-08-01
> **Screatch said:**
> I need some operations done at once, therefore i decided to write a bash script that will all at once connect with SSH to all servers. But is there any way, every connection would be done in different tab?

If you're using gnome-terminal (ubuntu's default) just:

Ctrl+Shift+T

That should open up a new tab.

---

### Post by shaggy999 on 2009-08-01
You might want to look into 'screen', which is included in ubuntu by default and is terminal-independent.

---

### Post by Screatch on 2009-08-01
> If you're using gnome-terminal (ubuntu's default) just:

Ctrl+Shift+T

That should open up a new tab.


What i mean, is what command will make a command tab open?

---

### Post by wojox on 2009-08-01
```
man gnome-terminal
```

--tab-with-profile=PROFILENAME

  Open a tab in the window with the given  profile.  More  than one  of these options can be provided, to open several tabs .

---

