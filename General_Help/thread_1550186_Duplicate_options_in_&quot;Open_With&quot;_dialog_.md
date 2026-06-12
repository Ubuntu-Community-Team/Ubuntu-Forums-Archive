---
title: "Duplicate options in &quot;Open With&quot; dialog box"
date: 2010-08-10
forum: General Help
---

### Post by MCSE_Crossover on 2010-08-10
Does anyone know how to clean up the duplicate options in my "Open With" dialog box? It seems the same things are repeated over and over. See pic for details -

---

### Post by jerenept on 2010-08-10
These are different WINE applications (as you may have guessed). However, there is no real need to get rid of them. I do not think that they are duplicates though.

---

### Post by MCSE_Crossover on 2010-08-10
It isn't just Wine. If you look at the screenshot, Banshee is duplicated too. There are all sorts of entries. It must be some hidden file or folder in my profile that contains those from previous installs. I just can't figure out where...

I just don't want there to be so many entries.

---

### Post by MCSE_Crossover on 2010-08-10
Hmm...found a lot of old entries under

~/.local/share/applications/

---

### Post by drs305 on 2010-08-10
You can also check ~/.local/share/applications/mimeappslist for duplicate entries or entries you don't want for a specific format. Normally you should be able to make changes to this list of stored 'preferred apps' via the screen you linked, but if "Remove" is not an option you could inspect this file manually.

---

### Post by TheWeakSleep on 2010-08-10
I had that issue and just deleted the menu entries in "other" using alacarte :p

---

