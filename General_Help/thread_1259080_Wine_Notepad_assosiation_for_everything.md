---
title: "Wine Notepad assosiation for everything?"
date: 2009-09-05
forum: General Help
---

### Post by sethhikari on 2009-09-05
When ever I try to open any text file or hundreds of other types of files that are a document type it tries to open with notepad in WINE. First notepad is no longer on my system so it does not even open. I can change each file assosation to fix this but there is a lot.. a lot lot..

Any ideas on how to purge the idea of notepad out of the system?
Thanks

---

### Post by gunksta on 2009-09-05
Try this (commandline):

```
rm -rf ~/.local/share/mime/
```

Explanation - 
[LIST]
[*]'rm' is the delete command.
[*]'-rf' will let it delete directories.
[*] '~/.local/share/mime/' is the local direcory where this info is stored.
[/LIST]  

I am assuming here that the damage was done to your local mime-type information. Once you have done this, log out and log back in. If all goes well, things will work in a manner that looks a little more normal.

I will confess though that this may not get it. It's possible that Wine somehow managed to damage your global mime-type config. First let's make sure wine is uninstalled:

```
sudo apt-get remove --purge wine
```

Explanation:
[LIST]
[*]'sudo apt-get' handles installing deleting programs from the system.
[*]'remove --purge' makes sure EVERYTHING gets deleted.
[/LIST]  

Once this runs (or tells you that it is unnecessary):

```
sudo update-mime-database /usr/share/mime
```

This will update your mime database and should fix anything that's left.

Then try re-deleting the local stuff. Log out and log back in.

---

### Post by mc4man on 2009-09-05
I would first try opening ~/.local/share/applications and look a .desktop with the display name of notepad.
.local is  a hidden file in your home folder

Delete it and then the association for any file type that was associated with notepad will move to the next available one.


( you can see the associations for mimetypes on a line basis in ~/.local/share/applications/mimeapps.list - first listed is generally the default

edit: didn't notice till now that this thread has a kubuntu tag, not too sure kde has the same setup as gnome in this regard, probably not

---

