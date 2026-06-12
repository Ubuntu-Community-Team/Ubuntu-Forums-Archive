---
title: "Renaming places in nautilus sidepane"
date: 2010-06-18
forum: General Help
---

### Post by Ctulhu on 2010-06-18
A potentially very dumb question but still ... I want to create a place that I can choose in the panel at the top left. So I

- go to Nautilus (tree view in sidepane) down in the folders until I see my destination on the left;
- switch to places in the sidepane and drag and drop the folder onto the places thing.

Then, the folder shows up with the name there, which is something like "Web_ABC". So I want to change it to "Web" only. On my 64bit machine, this works, on my 32bit machine, it doesn't. Whenever I change the name and press ENTER, it goes back to the old name. On the 64bit system, it only worked when I went to some other place once, and then fine, but on the 32bit one, no chance. Minor thing, yes, but still, any hints?

---

### Post by Zip247 on 2010-06-18
you could try alt-f2

then run gksudo nautilus

This will open nautilus with sudo(root) permissions.  

Be careful with this.

---

### Post by Ctulhu on 2010-06-20
ok, but where do I find the name of the places for my user name when I access stuff as root? :-|

---

### Post by John Bean on 2010-06-20
In Nautilus I use right-click/Rename for standard places and the "Bookmarks" menu for the others.

---

### Post by Ctulhu on 2010-06-21
@John: right-clicking and renaming doesn't work. I enter the new name, but once I press ENTER, it reverts back to the old name. The bookmarks menu helped tho. (Interestingly, this must be a bug: the bookmarks name was already the correct one, but it didn't show it in the sidepane. Then, when I deleted it and created it again and this time renamed it in bookmarks, it worked).
Thx m8!

---

