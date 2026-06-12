---
title: "Folder appears in trash and cannot be emptied"
date: 2009-11-20
forum: General Help
---

### Post by madwoollything on 2009-11-20
I have a folder that appears in my trash in nautilus that cannot be removed/moved/permissions changed. In short I can do nothing with it.

If I use 

sudo rm -rf ~/.local/share/Trash/files/*

~/.local/share/Trash/files directory is then empty when viewed in nautilus however the 'trash' in nautilus still contains my original file. Is this a bug or am I missing something?
[COLOR=#C20CB9]****[/COLOR][COLOR=#000000][B]

 

[/B][/COLOR]

---

### Post by adaucourt on 2009-11-20
> **Folder appears in trash and cannot be emptied**
 I have a folder that appears in my trash in nautilus that cannot be removed/moved/permissions changed. In short I can do nothing with it.

If I use 

sudo rm -rf ~/.local/share/Trash/files/*

~/.local/share/Trash/files directory is then empty when viewed in nautilus however the 'trash' in nautilus still contains my original file. Is this a bug or am I missing something?

Use ```
gksudo nautilus
``` this allows you elevate privileges so you can remove items from trash.

---

