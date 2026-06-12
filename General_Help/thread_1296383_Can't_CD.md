---
title: "Can't CD"
date: 2009-10-20
forum: General Help
---

### Post by Markjf100 on 2009-10-20
Sorry I'm new to this but I'm in Terminal window and the "ls" command shows my directory's in [COLOR=RoyalBlue]Blue[/COLOR], but when I use the "CD" to change to one of the Blue Directory's I get the message "No such file or directory" as shown below:-


sandy@sandy-laptop:~$ ls
[COLOR=RoyalBlue]Desktop[/COLOR]    examples.desktop  [COLOR=RoyalBlue]Pictures  Public     Videos
Documents  Music             Pub       Templates[/COLOR]
sandy@sandy-laptop:~$ cd music
bash: cd: music: No such file or directory
sandy@sandy-laptop:~$ 

:)  Guess there is a simple answer

Thanks 

Mark

---

### Post by Bachstelze on 2009-10-20
Linux is case-sensitive.

```
cd Music
```

---

### Post by StuartN on 2009-10-20
> **Markjf100 said:**
> sandy@sandy-laptop:~$ ls
[COLOR=RoyalBlue]Desktop[/COLOR]    examples.desktop  [COLOR=RoyalBlue]Pictures  Public     Videos
Documents  **Music**             Pub       Templates[/COLOR]
sandy@sandy-laptop:~$ cd **music**

Linux is case-sensitive, so you need to cd Music, not cd music.

---

### Post by XCan on 2009-10-20
Tip: If you press tab once it will autocomplete if the beginning of the path name is correct. If there are multiple matches, pressing tab twice will show all of them.

---

### Post by bacardiandwatermelon on 2009-10-20
> **XCan said:**
> Tip: If you press tab once it will autocomplete if the beginning of the path name is correct. If there are multiple matches, pressing tab twice will show all of them.

I use this feature alot...

---

### Post by Markjf100 on 2009-10-21
Thanks all for the quick replies, simple when you know how.
 
Mark :)

---

