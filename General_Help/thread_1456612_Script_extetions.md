---
title: "Script extetions"
date: 2010-04-17
forum: General Help
---

### Post by Moyamo on 2010-04-17
I would like to know of there are any executable extensions in Ubuntu like in windows.

For example

You make a file Script.bat to run it in the cmd you type Script instead of Script.bat

I would like to get this type of extension in Ubuntu so I don't have to type the full name with extension in the terminal.

---

### Post by gmargo on 2010-04-17
In general, only the execute permissions matter.  The file extension (in fact, the entire filename) is irrelevant.  So if you have a shell script named "doogie.sh", you can rename it to "doogie" and it will work identically.

Update: now that I read your question again, maybe you're asking how you can have a file Script.bat but only have to type "Script".  You could do this using a shell alias, but I don't know of a general method for "Script" to be expanded into all possible file extensions.  Except, on the command line, if you type "Script" and then hit the tab key, the automatic program completion should find Script.bat and fill out the rest for you.

---

### Post by Moyamo on 2010-04-20
Thanks

---

