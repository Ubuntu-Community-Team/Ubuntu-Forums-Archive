---
title: "Where do I change animations?"
date: 2006-01-29
forum: General Help
---

### Post by Elakt on 2006-01-29
I don't find any like settings for whole ubuntu like window animations..and disable stuff..where is it? in any hidden menu?

---

### Post by otey on 2006-01-29
What do you mean by "window animations"??

---

### Post by amisi on 2006-01-30
Hi!

Try to type the following command in your console:
gconftool-2 --type bool --set /apps/metacity/general/reduced_resources true 

I find it this place:
[http://ralph.n3rds.net/index.php?/archives/127-remove-black-rectangle-when-you-minimize-windows.html](http://ralph.n3rds.net/index.php?/archives/127-remove-black-rectangle-when-you-minimize-windows.html)

Enjoy this!

---

### Post by mcduck on 2006-01-30
Gconfeditor can be found from Applications/System Tools/Configuration Editor.

Open that and browse to apps/metacity/general and check 'reduced_resources'.

---

