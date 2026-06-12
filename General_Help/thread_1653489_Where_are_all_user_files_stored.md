---
title: "Where are all user files stored ?"
date: 2010-12-26
forum: General Help
---

### Post by microbious on 2010-12-26
If anyone of you guys could tell me where does ubuntu saves user prefference/settings/application settings/menus/themes all that effect only user loged in so i can transfer all of this to another account and have them be the same.

Or maybe there is an app for that ?

I setup my ubuntu to have no users and only root account, but i found that its not made to work correctly with being root at all times, so i created an account and want to export my root prefferences to newly created account, just like i could with windows by exporting files/registry keys etc.

My Home/Root is empty so i dont think any config files or settings are stored anywhere near this place.


Thanks in advance.
Hope to hear from u soon.

---

### Post by efflandt on 2010-12-27
The home for the root user is /root.  All other users normally are under their username in /home/.  But many of the directories/files are hidden to avoid clutter, so you have to press **Ctrl**+**H** in **Places** to see them, or **ls -a** (or **ls -al**) to see them in a terminal.

PS: Note that Linux is case sensitive, so unless you specifically created such a directory, there is no /Home/Root or /Home, but there is /root and /home (but no /home/root unless you made one).

---

### Post by dcstar on 2010-12-28
> **microbious said:**
> If anyone of you guys could tell me where does ubuntu saves user prefference/settings/application settings/menus/themes all that effect only user logged in so i can transfer all of this to another account and have them be the same.
..........

~.config
~.gconf

and various other ~. folders and files.

---

### Post by hawthornso23 on 2010-12-29
They are in your home directory, but hidden. Any file or folder whose name starts with a fullstop is hidden. You can use "ls -a" to list them in a terminal as others have suggested. Or you can click on "View>Show Hidden Files" in Nautilus to see them that way. 

The convention of putting all config files directly in the home directory (but hidden) dates from the early days of unix and is frankly a bloody mess. Sticking them all in a single hidden subdirectory that could at least be moved/backed_up/linked_to easily would make a lot more sense. There was an effort for a while to get people to put stuff in .config, but it sadly never really caught on.

---

