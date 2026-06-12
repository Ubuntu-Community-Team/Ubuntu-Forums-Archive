---
title: "Question About the LS Command &amp; Text Files"
date: 2012-08-12
forum: General Help
---

### Post by w201 on 2012-08-12
Does anyone know why the LS command shows duplicate text files in my home folder? I didn't see anything in the man pages that explains why that happens...

Example:
mercedes_190e_parts_germantown~
mercedes_190e_parts_germantown

---

### Post by Nytram on 2012-08-12
The file with the ~ is a backup file, created by some text editors (for example Gedit.)

---

### Post by nmaster on 2012-08-12
the first one is a backup.  some text editors (like emacs) will create these. try using this
```

ls --ignore-backups

```

you can add an alias to your bashrc file.

---

### Post by codemaniac on 2012-08-12
they are just backups of your original files that gedit creates before saving changes to your edited text files.

Go in the gedit menu to Edit > Preferences > Editor there you will find an option that says "Create a backup of files before saving". Uncheck this option and you are done.

---

### Post by w201 on 2012-08-12
Good stuff, guys! Thanks so much.

---

