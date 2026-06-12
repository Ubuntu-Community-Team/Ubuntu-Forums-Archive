---
title: "Missing folders"
date: 2010-12-22
forum: General Help
---

### Post by PistolPete64 on 2010-12-22
I have lost my personal folders on my desktop. I started to get error messages about ICEauthority, I had cahnged my password and seems like it became an issue , after logging in it I would get a message that I needed to create a Peter\home and a Peter\.naulitus folders. After getting in through another account and creating above folders and assigning permissions, I am able to login to my account without errors BUT all of my other data is missing, any thoughts ????

---

### Post by gadolinio on 2010-12-22
I once had a problem like that. The files weren't missing but with wrong permissions. Try opening nautilus as root (in the terminal "gksudo nautilus"), and see if the files are actually there. If that's the case, set the permissions correctly as root. Hope you find this useful...

---

### Post by PistolPete64 on 2010-12-22
I apologize for my ignorance but how do I do that

---

### Post by mendhak on 2010-12-22
Press Alt+F2 (this brings up the run dialog)
Then in there do:

gksudo nautilus

This should prompt you for a password and then bring up nautilus.

You can also install a package called (someone correct me if it's wrong) nautilus-gksu which provides you with a context menu in nautilus "Browse as root", so you can right click a folder and then choose browse as root which opens an administrative nautilus window.

---

### Post by gadolinio on 2010-12-26
> **mendhak said:**
> Press Alt+F2 (this brings up the run dialog)
Then in there do:

gksudo nautilus

This should prompt you for a password and then bring up nautilus.

You can also install a package called (someone correct me if it's wrong) nautilus-gksu which provides you with a context menu in nautilus "Browse as root", so you can right click a folder and then choose browse as root which opens an administrative nautilus window.
Right. If you see the files using this method, then the problem is about permissions. You can right-click your home folder (from the window you opened with gksudo nautilus), and go to the "permissions" tab. There you should have read&write&execute for Owner; read and execute for Group; just execute for Others. Then click apply to all files.

---

### Post by gadolinio on 2010-12-26
Just in case, backup that folder first! make a complete copy of your home folder before changing its permissions.

---

