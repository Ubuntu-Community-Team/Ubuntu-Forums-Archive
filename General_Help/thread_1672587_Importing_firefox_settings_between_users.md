---
title: "Importing firefox settings between users?"
date: 2011-01-21
forum: General Help
---

### Post by whatthefunk on 2011-01-21
I've set up a new user account on my computer and I want to import all my firefox about:config settings to the new user so that I dont have to spend hours doing them all again.  Is there any way to do this? Lubuntu 10.10 Thanks

---

### Post by Verbeck on 2011-01-21
try copying over prefs.js in  /home/user/.mozilla/firefox/xxxxxxxx.default/

edit: you might need to change the folder paths in that file

---

### Post by mciverza on 2011-01-21
or just copy your entire .mozilla/firefox directory across to the new user

if old username is oldjoe, then...
log in as new user.

Open your file browser (Places --> home)
 Select "Show hidden files" from the View menu
Go up one directory (Go --> open parent)
find your old username's home directory there. enter it.
Right-click to copy the .mozilla directory.
Click on the "home" house icon to go back to your own (new user's) home folder
Right-click "paste"

when you open firefox after this, ALL the settings and preferences would have copied across.
(beware of your saved passwords)

---

### Post by whatthefunk on 2011-01-22
Got it figured out.  Thanks!

---

