---
title: "Smeg can't change name of application in menu"
date: 2006-02-05
forum: General Help
---

### Post by annsachd on 2006-02-05
It will change the name in Smeg but when you look at the application in the menu it still has its old name.

How do you get Smeg to actually make the change of the application name in the menu?

Thanks.

---

### Post by Stormx on 2006-02-05
Odd indeed. When you go back into smeg, does it revert to the old name like the menu does, or show the new name?

---

### Post by stoic jed on 2006-02-05
Each applications menu entry has a corresponding .desktop file specifying the name of the entry, the command to execute it, and more. My understanding is that SMEG modifies these .desktop files in your ~/.local/share/applications/ directory, but if there is a .desktop entry of the same name in the /usr/share/applications/ directory its settings will override those of the ~/.local/share/applications/ desktop entry.

So, if you want to change the name of "Text Editor" to "Gedit", for example, you would have to do the following:

```
sudo gedit /usr/share/applications/gedit.desktop
```

Change "Name=Text Editor" to "Name=Gedit".

Then you should be able to change the name of the "Text Editor" entry using SMEG and have it stick.

---

### Post by annsachd on 2006-02-05
Nice Stoic Jed, that did the trick. 

I was trying to change Goobox which is listed as CD Player to Goobox. Kinda makes sense to me that way. Your changing the name in the goobox.desktop file worked. I was then able to get Smeg to make the change.

Thanks for the help.

---

### Post by dcstar on 2006-02-05
[QUOTE=annsachd]It will change the name in Smeg but when you look at the application in the menu it still has its old name.

How do you get Smeg to actually make the change of the application name in the menu?

Thanks.[/QUOTE]
I found that restarting the X-session caused the name changes to then be visible in the menu.

---

