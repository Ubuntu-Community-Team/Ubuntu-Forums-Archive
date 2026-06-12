---
title: "Permissions won't let me delete folders"
date: 2012-02-02
forum: General Help
---

### Post by rollin77 on 2012-02-02
I have a stupid noob question, but I created a couple folders while using a program, (GNS3), but it created the new folders and files as protected, requiring root access to delete or modify them.

When I go into the folder properties I can't change the settings to allow me to delete these.  I'm not real good working in command line so I'd prefer to just delete these in the GUI, but how do I do that?

---

### Post by moffa on 2012-02-02
> **rollin77 said:**
> I have a stupid noob question, but I created a couple folders while using a program, (GNS3), but it created the new folders and files as protected, requiring root access to delete or modify them.

When I go into the folder properties I can't change the settings to allow me to delete these.  I'm not real good working in command line so I'd prefer to just delete these in the GUI, but how do I do that?

Press Alt-F2 and type "gksudo nautilus", it should prompt you for a password, enter it.  Navigate to the folder in question, right-click on it, go to properties, permissions tab and edit the "Others" section.

---

### Post by rollin77 on 2012-02-02
That was it, thanks

---

