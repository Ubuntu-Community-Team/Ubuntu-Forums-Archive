---
title: "Adding applications to menu"
date: 2010-06-29
forum: General Help
---

### Post by sharath.puranik on 2010-06-29
This is the issue I am facing:

I have created a software and I want it to be displayed in the applications menu, so i created a .desktop file and added it to /usr/share/applications, which is the location where all the .desktop files are supposed to be places.

Now the funny thing is when I copy the file to that location, the program appears correctly but its present there only for that session. If I re-login or if I restart, the program mysteriously disappears from the menu.
Another thing i noticed is that if I open the .desktop file in gedit and save it with/without changes, the program reappears in the applications menu.
Its not specific to my system, when my friends tried to do it, they had the same problem as well.

As far as i know there are no issues with the .desktop file otherwise which the program wouldn't have appeared in the menu in the first place.
Pls help

---

### Post by arrange on 2010-06-29
Try putting the *.desktop* file in the **~/.local/share/applications/** directory...

---

### Post by sharath.puranik on 2010-06-30
> **arrange said:**
> Try putting the *.desktop* file in the **~/.local/share/applications/** directory...

But isn't that's only for the current user, I can try that but what if I want it to appear for all the users?

---

### Post by arrange on 2010-07-01
[COLOR="DimGray"]if I want it to appear for all the users?[/COLOR]
This is a strange problem, and I see it scattered all over the Internet, but with no solution. 
For me an interesting fact is, that for example the *viewnior* (image viewer) package only has a */usr/share/applications/viewnior.desktop* file (as far as relevant files are concerned), with no *pre-/post-inst* scripts, and still is able to make the application entry work. Puzzling.

---

