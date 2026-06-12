---
title: "Explain Assignment of Applications to Submenus"
date: 2011-08-22
forum: General Help
---

### Post by beoweulf on 2011-08-22
When certain games are added to the Games submenu of the Application menu, they are automatically sorted to a submenu of the Games submenu (i.e. Chess is automatically placed in the Board Games submenu of the Games menu). How is this accomplished (in other words, how are applications assigned categories, and how does the menu know what category they belong to)?

---

### Post by Azdour on 2011-08-22
Hi,

If I understand correctly it is done in the following way:

 - Under /usr/share/applications there is a '.desktop' file for every application
 - It is in the .desktop file that defines where in the menu they appear, e.g for chess (glchess.desktop) it is defined in Categories

---

