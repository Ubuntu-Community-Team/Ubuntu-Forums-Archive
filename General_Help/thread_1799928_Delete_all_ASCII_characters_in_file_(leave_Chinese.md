---
title: "Delete all ASCII characters in file (leave Chinese characters only)"
date: 2011-07-08
forum: General Help
---

### Post by East Asia Student on 2011-07-08
What command could I use in terminal to delete all ASCII characters? That is, delete a-z, A-Z, 0-9, and all punctuation? I have a file containing Chinese characters, and I want to remove everything else and leave just the Chinese.

I can use grep to leave only the lines that have Chinese in them, but this still leaves a lot of non-Chinese stuff on those lines. Does anyone know how I could actually remove everything that isn't Chinese?

Thanks

---

### Post by sisco311 on 2011-07-08
Welcome to the forums!

In GNU sed you can try something like:
```
sed -e 's/[0-9a-zA-Z]//g' -e 's/[[:punct:]]//g' -e '/^$/d' file
```
Use can use -i flag to edit the file in place:
```
sed -i -e 's/[0-9a-zA-Z]//g' -e 's/[[:punct:]]//g'-e '/^$/d' file
```

EDIT:
Hmm, If you use the POSIX locale, you can use [[:alnum:]] instead of [0-9A-Za-z] (it's more elegant):
```
LC_ALL=POSIX sed -e 's/[[:alnum:]]//g' -e 's/[[:punct:]]//g' -e '/^$/d' file
```
EDIT2:
With extended regular expressions:
```
LC_ALL=POSIX sed -r -e 's/[[:alnum:]]?[[:punct:]]?//g' -e '/^$/d'
```

---

### Post by Chronon on 2011-07-08
This strikes me as a homework problem.  (The choice of user name doesn't help this impression.)

---

### Post by East Asia Student on 2011-07-08
@sisco311
Absolutely perfect, thank you.

@Chronon
It actually isn't, just something that'd be helpful to me (I run a site on East Asian Studies, hence the username. Google it if you like :P)

---

### Post by Chronon on 2011-07-10
Okay.  I believe you.  :)

---

