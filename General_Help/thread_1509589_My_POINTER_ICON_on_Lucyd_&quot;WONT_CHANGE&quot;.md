---
title: "My POINTER ICON on Lucyd &quot;WONT CHANGE&quot;"
date: 2010-06-14
forum: General Help
---

### Post by Click-dot-Bejo on 2010-06-14
Help me, i cant change my POINTER [Cursor Icon]..
anyone can help me?
this sucks.. :confused:

---

### Post by WorMzy on 2010-06-14
Have you changed it in System -> Preferences -> Appearance -> Customise -> Pointer? If so, have you restarted since you did it?

Also, are you using Compiz? You may need to force the system to use the new cursor by creating a text file, called index.theme, at ~/.icons/default. Put the following into there: ```
[Icon Theme]
Name = <anything>
Comment = <anything>
Example = <anything>
Inherits = <name of the cursor theme you want to use>
```

Save it, then restart. It should force the cursor to switch to the one you want.

---

