---
title: "Removing software from the Applications menu (Gnome 3)"
date: 2012-02-10
forum: General Help
---

### Post by Pingouin7 on 2012-02-10
I have attempted to install software from manually compiling its source.
During compilation, everything seemed to work fine and the app's icon appears in the Applications menu, but it does absolutely nothing when I click on it.

I have manually deleted the binary file for the program, but now I need to completely remove its entry in the Applications menu (Which now says it failed to run the program.)

There's absolutely no information about this on Google, so if anyone knows how to do that, help would be appreciated.

---

### Post by cbanakis on 2012-02-10
I think if you install "Main Menu" (In the software center)

You can then use main menu, to manually add/remove programs from your applications menu.

I assume your using Unity, and I have not tried main menu with Unity, but it works with most other interfaces, so I assume it will do the trick for you.

Let me know how it works out.

---

### Post by Cheesemill on 2012-02-10
All of the menu entries come from the .desktop files in /usr/share/applications

If you delete the corresponding file it should remove the program in question from the menu.

---

