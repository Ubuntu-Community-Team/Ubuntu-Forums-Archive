---
title: "Desktop right-click menu"
date: 2006-04-08
forum: General Help
---

### Post by daiwai on 2006-04-08
I know I can edit a custom right-click menu in the behaviour tab of desktop settings. Now is there a way to organize the entries in folders? 

How can I add commands found in the "actions" section of the kmenu, like logout, switch user etc..?

Where are the settings for those menus stored?

---

### Post by Neeko on 2006-04-08
Creating new actions is quite easy. They are just small text files, located in /usr/share/apps/konqueror/servicemenus/
and named with a .desktop suffix.

Take a look at this tutorial:
[http://developer.kde.org/documentation/tutorials/dot/servicemenus.html]("http://developer.kde.org/documentation/tutorials/dot/servicemenus.html")

---

### Post by daiwai on 2006-04-09
Thanks for your reply!

Sorry for not being clear. I was asking about the right click menu when clicking on the desktop. The tutorial seems to describe how to create menus for konqueror.
I found the location of the custom KDesktop menus it is in ~/.kde/share/config/kdesktop_custom_menu1
But I think it is using a different syntaxt than the service menus from the article. It's just ItemX=commandX and one extra line for the number of items. Like so:

Item1=konsole
Item2=jedit
Item3=opera
NrOfItems=3

All I could find about the syntaxt for those menu config files was a mailing list post that basically described the simple structure as shown above.
Anybody know if organizing entries in this menu in folders and/or adding commands like logout, switch user etc. is possible?

---

### Post by mkuutti on 2007-11-14
Did you ever solve this thing?
I added bugreport:
[http://bugs.kde.org/show_bug.cgi?id=152006]("http://bugs.kde.org/show_bug.cgi?id=152006")
because command line options are ignored, even if I use graphical interface to add f.e. konqueror (kfmclient openProfile webbrowsing -> kfmclient)

Anyway, my opinion is that current menu system is not usable enough. There is kmenuedit for Application menu and own editor for custom-menu which is totally undocumented. All menu entries should have equal system, which would make easier to f.e. add "Lock Session" type of entries in any menu available.

---

### Post by toupeiro on 2007-11-14
You'll have to forgive the cobwebs when it comes to KDE, because I haven't used anything newer than 3.0 thoroughly, but as I recall the file you want to modify is called kdesktoprc
```

vi ~/.kde/share/config/kdesktoprc
```

If this is not doing what you wanted, my mistake.

---

