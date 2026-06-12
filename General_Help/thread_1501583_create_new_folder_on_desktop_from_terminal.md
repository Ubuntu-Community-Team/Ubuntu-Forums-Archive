---
title: "create new folder on desktop from terminal"
date: 2010-06-04
forum: General Help
---

### Post by realzippy on 2010-06-04
what is the command to create an untitled folder **just as** rightclicking/createfolder on Desktop does?

Sorry for that easy question...

---

### Post by llawwehttam on 2010-06-04
cd Desktop
mkdir foldername

---

### Post by karthick87 on 2010-06-04
```
User@Ubuntu-desktop:~$ cd Desktop
User@Ubuntu-desktop:~/Desktop$ mkdir foldername

```

---

### Post by realzippy on 2010-06-04
Sorry,you missunderstood.When you rightclick on the desktop and create a new folder,this folder opens and you can *instantly rename it* without rightclicking that folder first.And if you create more than 1 new folder,the
following folder(s) are named: untitled folder1,untitled folder2,aso.
You cannot do that with that simple mkdir...I would not have asked if it was so easy...

---

### Post by llawwehttam on 2010-06-04
Not sure its possible without a script which would be a waste of time.

---

### Post by Leppie on 2010-06-04
why would you like to create unnamed folders? in other words, why is it that you do not want to give the final names when creating the folders?

---

### Post by realzippy on 2010-06-04
> **llawwehttam said:**
> Not sure its possible without a script which would be a waste of time.

,,,so what rightclickingDesktop/create untitled folder does?

---

### Post by realzippy on 2010-06-04
> **Leppie said:**
> why would you like to create unnamed folders? in other words, why is it that you do not want to give the final names when creating the folders?

...because I do not want to create always the same folder,when I run the command/script.Need it for easystroke gesture recognition,means create new folder on the Desktop by mousegesture.

Edit: ok,forgot that easystroke also accepts shortcuts...so Shift+Ctrl+N solves this problem.

But  now I would like to know what command/script Shift+Ctrl+N calls...

---

