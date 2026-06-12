---
title: "Where are the Application, Places, and System shortcut launchers stored?"
date: 2011-07-20
forum: General Help
---

### Post by Keypel on 2011-07-20
In what directory are the Application, Places, and System shortcut launchers stored?

---

### Post by WorMzy on 2011-07-20
Globally: /usr/share/applications/
Per-user: ~/.local/share/applications/

---

### Post by raja.genupula on 2011-07-20
try this in terminal  , it will provide the path of the application where it is installed . 
```
where Application
```
write application name in "application"

---

### Post by Keypel on 2011-07-20
@raja.genupula

Thanks for the command. Could come in handy some other time. In this case I was just looking for where the launchers where stored. BTW the command is "which" not "where"

@WorMzy

Thanks for the answer I was looking for.

In windows you can add items to your start menu by adding folders and shortcuts to 

C:/Documents and Settings/All Users/Start Menu

I was thinking it would be similar in Ubuntu but I had a look in 

/usr/share/applications/

and does not seem as organized, well not from a human's perspective anyways.

Looks like I will have to use the "Edit Menus" feature instead.

---

### Post by CatKiller on 2011-07-21
> **Keypel said:**
> I was thinking it would be similar in Ubuntu but I had a look in /usr/share/applications/ and does not seem as organized, well not from a human's perspective anyways.

Looks like I will have to use the "Edit Menus" feature instead.

[Launchers]("http://standards.freedesktop.org/desktop-entry-spec/latest/") and [menus]("http://standards.freedesktop.org/menu-spec/latest/") are described at freedesktop.org. The gist is that they are just text files and you can edit them if you'd like.

---

