---
title: "Ubuntu asks password when i try to open a folder"
date: 2011-03-03
forum: General Help
---

### Post by kommunisti on 2011-03-03
Everytime i try to open a folder from "Locations" menu, for example "Music", it gives me a password prompt. How do i undo this?

Tried a Google search already.

---

### Post by oliwek on 2011-03-03
maybe try what ubuntu suggests (enable file sharing), or uninstall dropbox (if your problem comes after installing dropbox).

---

### Post by celldweller1591 on 2011-03-03
you must have chosen to encrypt home folder while installing ubuntu i guess..try this command and go along with it :-
> ecryptfs-setup-private --undo
and see if that works.

---

### Post by kommunisti on 2011-03-03
> **celldweller1591 said:**
> you must have chosen to encrypt home folder while installing ubuntu i guess..try this command and go along with it :-

and see if that works.

I didn't chose to encrypt my home folder. When i paste your command in terminal it says "'ecryptfs-setup-private' is not currently installed"

It seems that my ubuntu is like "stuck" in root mode. I don't really know what to do..

---

### Post by kommunisti on 2011-03-03
This is what it looks like when i open a folder (after i have input my password)

---

