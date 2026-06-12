---
title: "possible to use MELD Diff Viewer in GEdit (compare files side by side)"
date: 2012-09-17
forum: General Help
---

### Post by 777funk on 2012-09-17
MELD Diff viewer works GREAT to see the differences between two filles. Is it possible to use it right in GEdit (say I already have two files open in GEdit) or will I need to open MELD up as an application?

---

### Post by f8l_0e on 2012-09-17
gedit has plug-in functionality.  They can be enabled under Preferences/Plugins tab.
There is a plugin that halfway does what you want.  Check the following link.

[http://www.webupd8.org/2011/01/how-to-integrate-meld-into-gedit-for.html]("http://www.webupd8.org/2011/01/how-to-integrate-meld-into-gedit-for.html")

It starts meld with the current file open and allows you to locate the file to compare it to. 

Another option is to make a custom external tool plugin, this will be more difficult to implement than I hoped, because variables that gedit makes available for scripting only give the filename of the currently active tab in gedit and gedit doesn't keep files open during edit so none of the cli tools to find open files will work.

---

### Post by 777funk on 2012-09-18
That's pretty close! I'd really like to have the MELD plugin work in GEdit because I have other things that work great in GEdit for code language highlighting.

---

