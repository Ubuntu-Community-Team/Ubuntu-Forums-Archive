---
title: "Menu items not painted until mouse over."
date: 2009-08-24
forum: General Help
---

### Post by d-Pixie on 2009-08-24
Recent problem. Any menu created by gnome natively fails to paint the menu items until I mouse over each of them. The problem seams to be local i nature. Menu in Nautilus does not paint properly but "external" programs like firefox and vlc paint the menus like they should. Also it is related to the current user. If I open an instance of Nautilus with gksu as root the menus work fine...

All menus are affected. Right click on desktop, all tray menus, App. Places and system and related sub menus.

All this lead me to believe that it is a setting or other local resource that is bugged.

Any one else had this problem?

Currently running Gnome on Karmic with latest updates. Nothing new installed when the problem started that I know and probably not an update in karmic since I have not found any others with the same problem..

Cheers. Jonas Erlandsson, Sweden

---

### Post by P4man on 2009-08-24
this may sound silly, but can it be a problem in the theme ? Try another theme, and see if it persists.

---

### Post by d-Pixie on 2009-08-26
That seams to be it, strangely enough ;o)

I tried a few other themes and it worked. By switching one part of the theme at a time I now know that it's the "controls" part of the theme that is responsible. Tried reinstalling the theme I use for the controls, "water vapor", but the problem persisted.

Likely there has been an update of the GTK engine that makes the theme fail for some reason.

A few things I don't understand in this context: Why did any menus work? They are all controlled by the theme but still some worked and others didn't. Why do all other themes work? There shouldn't be anything in the theme that could affect how menus are drawn in my world... And if there is a bug in the theme how do you fix it? I really like that theme ;o)

Should this be reported as a bug for the GTK engine or just the theme? Is there any theme guru out there that would mind helping me fix the damn thing? ;o) 

Cheers! Jonas Erlandsson, Sweden.

---

### Post by P4man on 2009-08-26
They changed some stuff in Karmic that breaks a lot of jaunty themes. You'd have to ask the theme creators to update their themes.

As to why some menu's worked.. some apps use GTK, others Qt. Same reason why some themes wont work well, or at all on apps like Openoffice and firefox. Dont know the specifics though..

---

