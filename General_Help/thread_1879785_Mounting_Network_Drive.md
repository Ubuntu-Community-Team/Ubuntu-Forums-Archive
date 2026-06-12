---
title: "Mounting Network Drive"
date: 2011-11-12
forum: General Help
---

### Post by UnsolvedCypher on 2011-11-12
At my organization, we have "public" computers, where when you sign into the server, you can click on a desktop shortcut and it will take you to your personal folder \\SERVERNAMEHIDDENFORSECURITY\firstinitiallastname . We may be converting to Ubuntu, but we cannot unless this works. Does anyone know how to do this? I think the solution might be to write a script with the firstinitiallastname being a variable. Thank you so much!

---

### Post by jonkiribati on 2011-11-12
you can use the mount command this is the syntax 
mount //servername/share /mount/point [-o options]

---

### Post by UnsolvedCypher on 2011-11-12
Thanks, but I'm kind of a beginner. Would I have to write some sort of script?

---

### Post by Morbius1 on 2011-11-12
Open a terminal and type:
```
nautilus smb://SERVERNAMEHIDDENFORSECURITY/firstinitiallastname
```Once it comes up Bookmark it.

---

### Post by UnsolvedCypher on 2011-11-12
Awesome! Thanks! But is there a script I could write to make firstinitiallastname a variable? Multiple people will use the computer, so we can't have a shortcut to each account (too many people)

---

### Post by UnsolvedCypher on 2011-11-13
bump

---

