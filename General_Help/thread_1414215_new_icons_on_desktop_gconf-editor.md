---
title: "new icons on desktop gconf-editor"
date: 2010-02-23
forum: General Help
---

### Post by gabrielcik on 2010-02-23
Hola!

I know it is possible to add home directory, trash... to the desktop by using gconf-editor.

I would like then to know if it is possible in the same way to add also other links to other directories as video, pictures, downloads... maybe adding a new key to nautilus --> desktop inside gconf-editor?

If not it is possible to put a link on the desktop to one of these directories and remove the typical arrow of these links?

A last question it is better to use gconf-editor ad user or as root?
(i noticed that if i modified it with root and then i lunch it again as user it get different gconf parameters).

Thank you!

---

### Post by Wardje on 2010-02-23
Use gconf-editor as your normal user, not root.

In gconf-editor, go to apps->nautilus->desktop for home, trash, ...

Links to other directories you'll have to add yourself with symlinks (shortcuts), as far as I'm aware.

---

