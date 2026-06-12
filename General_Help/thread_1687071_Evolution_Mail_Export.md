---
title: "Evolution Mail Export"
date: 2011-02-13
forum: General Help
---

### Post by kakashi_12 on 2011-02-13
I don't see the selection/option under any menu to export mail messages or backup. Is this existent? Or could I go to the folder where they are located and copy them myself to back them up? Where is that path?

---

### Post by Habitual on 2011-02-13
```
cp -pr ~/.evolution ~/evolution.bak
```

will backup your Evilution directory.
Make certain to close Evilution first.

---

### Post by kakashi_12 on 2011-02-13
[http://www.stchman.com/export_evolution.html](http://www.stchman.com/export_evolution.html)

nvm, i found it. jumped to conclusions as usual.

... what i like about this is that it is in plain text (txt) and easy to manager the file.

---

### Post by philinux on 2011-02-13
> **kakashi_12 said:**
> I don't see the selection/option under any menu to export mail messages or backup. Is this existent? Or could I go to the folder where they are located and copy them myself to back them up? Where is that path?

This was the first hit from google. evolution backup
[http://library.gnome.org/users/evolution/stable/b17qy921.html.en](http://library.gnome.org/users/evolution/stable/b17qy921.html.en)

Quite a good user guide. Also try the help section within evo itself.

---

### Post by kakashi_12 on 2011-02-21
> **Habitual said:**
> ```
cp -pr ~/.evolution ~/evolution.bak
```will backup your Evilution directory.
Make certain to close Evilution first.

Ok, I used this command so that I could back them all up at once. But WHERE did they backup to?

---

### Post by philinux on 2011-02-21
This is the best way. As it packages the ~/.evolution folder. Which can then be used to restore.
[http://library.gnome.org/users/evolution/stable/b17qy921.html.en](http://library.gnome.org/users/evolution/stable/b17qy921.html.en)

The cp command you used would have put the file in your home directory. Places>Home Folder.

---

### Post by sites on 2011-02-21
Under the file menu there's an option to 'Download message for offline usage'.  I'm guessing if you did that then you would only need to copy the evolution folder in your home directory.

Just a hunch.

---

