---
title: "Password manager not working in Firefox"
date: 2011-08-31
forum: General Help
---

### Post by Bruv on 2011-08-31
Does anyone know why the password manager in Firefox doesn't work in Natty ?

---

### Post by lovinglinux on 2011-09-05
You probably have a corrupted file in your profile.

Close Firefox, open ~/.mozilla/firefox/<profilename>/ folder and delete (better to move it somewhere else for backup) the files *signons.sqlite* and *key3.db*. Restart Firefox. 

Test if it works. There won't be any passwords saved, because you deleted the password files.

---

