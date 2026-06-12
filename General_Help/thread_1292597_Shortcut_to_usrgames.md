---
title: "Shortcut to /usr/games"
date: 2009-10-16
forum: General Help
---

### Post by Joezorry on 2009-10-16
I'm a total newbie and running jolicloud, which I understand is Ubuntu with UNR.

I installed Starcraft which runs perfectly through Wine.
But I want a shortcut to Starcraft.exe to appear in the Games folder, which is, from I understand, is located under /usr/games.
How do I move a shortcut there?

I want it to appear under the menu games.

/Joakim

---

### Post by mocoloco on 2009-10-16
You're a little off.  You should already have a menu item for starcraft under the wine sub folder.  I don't have UNR so I'm not sure but there should be something similar to the default menu editor in Gnome (the interface in stock Ubuntu).  You can get to it form System > Preferences > Main menu. If you can't find it the command for it is alacarte, I'm not sure if you get a run dialog by hitting Alt+F2 in UNR.  In there you would find the starcraft item and drag it to "Games".

Anyone have UNR that can confirm you use alacarte, or some other GUI menu editor?

Since you were confused on /usr/games I'll give a little explaination.  I hope I don't confuse you..
Linux native apps install files together by their type  /usr/games only has the executables, not the rest of the files, like the configuration files that cause things to show in the menus which are in /usr/share/applications, documentation goes in /usr/share/doc, and so on.
However wine installations are by default only for the current user, not system wide, so none of their stuff is in put in with the native stuff, instead it's kept in a hidden folder in your home folder, called .wine.  There's another hidden folder called .local that keeps track of your customized menu along with some other things, just for your user.  So when you make any changes to the menus they're saved in .local which overrides the default menus, leaving other users unaffected.  Wine creates menu files and puts them in your /home/<you>/.local/share/applications.

---

### Post by mike555 on 2009-10-16
to add launchers (shortcuts) to your menu you go to System , Preferences , Main menu ,Games.

---

### Post by Joezorry on 2009-10-16
Thank you so much.
It was just under Main Menu under preferences.
I go with the mindset that linux should be hard, when the solutions are so easy. Thanks!

Do you know how to get a custom icon for a wine .exe icon?

---

### Post by Joezorry on 2009-10-16
Thank you so much.
It was just under Main Menu under preferences.
I go with the mindset that linux should be hard, when the solutions are so easy. Thanks!

Do you know how to get a custom icon for a wine .exe icon?

---

### Post by CatKiller on 2009-10-16
> **Joezorry said:**
>  Do you know how to get a custom icon for a wine .exe icon?

Do you mean where you can get one from, or how to apply it?

To apply it, you just right-click on it, select Properties and click on the icon, and then find the icon that you want to use, the same as any other file.

---

