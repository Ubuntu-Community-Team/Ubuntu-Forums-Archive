---
title: "Create New Launcher in Gnome 3"
date: 2011-10-16
forum: General Help
---

### Post by volter on 2011-10-16
After long search and a lot of ways to create launcher I find best way to do so.

1. Install Gnome-Tweak -> in 'Desktop' tab turn on option 'Have file manager handle the desktop'
2. create script with 'gedit' with code ```
gnome-desktop-item-edit ~/Desktop/ --create-new
``` 
3. Save with name "Create New Launcher".
4. Mark the file as executable (Right click -> properties-> Permissions -> Mark 'Allow execute file as a program' ).
5. place the file in home/user_name/.gnome2/nautilus-scripts (to see hide folders Ctrl+h). 

enjoy ;)

I don't know how to correctly write script, but its work just fine for me.

---

### Post by stelfo on 2011-10-18
Fantastic, brilliant. Thousands of people are looking for this at this time. Thank you.:)

---

### Post by Inoki on 2011-12-02
This has to be edited in your own language. E.g. the following string:

```
gnome-desktop-item-edit ~/[COLOR="Red"]Desktop[/COLOR]/ --create-new
```

needs to be changed to what it's called in your language according to the translation. E.g. in my language "Desktop" is called "Plocha", so I had to change that in order to make it work.

---

### Post by Xpander69 on 2011-12-19
sweet. thx a lot for that.
was searching for that :)


now last final issue with gnome3... that damn system tray extension..items have too big spaces between eachother..and when too many open then they start to hide some of the stuff from the "panel"... but thats another topic

---

### Post by alpinekid on 2012-12-07
To create a new launcher on the desktop I just drag the menu item from the applications pull down to the desktop.

If I need a launcher for a executable that is not in the application menu list, I just drag any application and then edit the properties. Change the command, icon etc.

It seems to work for the few times I have had to do it.

---

