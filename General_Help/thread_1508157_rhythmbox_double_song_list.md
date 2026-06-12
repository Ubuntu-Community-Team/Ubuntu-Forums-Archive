---
title: "rhythmbox double song list"
date: 2010-06-12
forum: General Help
---

### Post by spanky1023 on 2010-06-12
why does rhythmbox list 2 of every song ?   i tried removing the entire list, and then added all my songs to the playlist again, and samething.

any ideas ?

---

### Post by Wardje on 2010-06-14
Go in Preferences and make "Location" a visible column. See where it fetches each file from. My guess is a symlink or something similar makes it index (some?) things twice.

---

### Post by spanky1023 on 2010-06-20
> **Wardje said:**
> Go in Preferences and make "Location" a visible column. See where it fetches each file from. My guess is a symlink or something similar makes it index (some?) things twice.

uhh... i dont see where i have an option to make my "location" a visible column ??

---

### Post by Dngrsone on 2010-06-22
Click on Edit, Preferences and it is under the General tab.

Like Wardje said, it is likely you have the files in two separate locations or you have a symbolic link to the file in a different location, both in folders that you are monitoring with Rhythmbox.

---

### Post by booshire on 2010-09-05
Same issue because of symlink from home to another partition for music, originally had folder pointed to but rhythmbox decided to add home/me/Music automatically. I had to go into /home/[user]/.gconf/apps/rhythmbox/%gconf.xml and remove the extra entry manually. magic I tell you

---

### Post by JakartaDean on 2011-04-12
> **booshire said:**
> Same issue because of symlink from home to another partition for music, originally had folder pointed to but rhythmbox decided to add home/me/Music automatically. I had to go into /home/[user]/.gconf/apps/rhythmbox/%gconf.xml and remove the extra entry manually. magic I tell you

I can confirm that this issue is still present in 0.13.1 and results in extremely unexpected behaviour.  Someone needs to reconsider how users add AND REMOVE directories from the library in an intuitive manner.  Editing preferences seems to show that I only have one directory referenced in my library, but there are two.  I'll try your manual fix.

This seems to be related to Bug 432909 ([https://bugzilla.gnome.org/show_bug.cgi?id=432909](https://bugzilla.gnome.org/show_bug.cgi?id=432909)) and I've placed a note there and linked to this thread.

---

