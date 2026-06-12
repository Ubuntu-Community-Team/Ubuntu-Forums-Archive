---
title: "copy .jpg to desktop folder in terminal?"
date: 2010-01-27
forum: General Help
---

### Post by DeMartini on 2010-01-27
I have been sitting here practising linux commands and I cannot seem to copy a picture from home/pictures to the desktop, specifically a folder I created on the desktop "test"

---

### Post by t4thfavor on 2010-01-27
```

cd Pictures
cp mypic.jpg ../Desktop/test

or to copy all pics

cp *.jpg ../Desktop/test

```

the ../ means the directory above this one.

Also you cannot forget that Linux is case sensitive so Desktop is a different folder than desktop. same with files 1A.jpg is different than 1a.jpg

---

### Post by DeMartini on 2010-01-27
this is the error I get, keep in mind the .jpg is in home/Pictures


jamie@jamie-laptop:~/Desktop/test$ cp joss-stone1.jpg ../
cp: cannot stat `joss-stone1.jpg': No such file or directory
jamie@jamie-laptop:~/Desktop/test$

---

### Post by t4thfavor on 2010-01-27
your in the directory:
jamie@jamie-laptop:~/Desktop/test$

you need to adjust your path to accomodate it.

from where you are now:
cp ~/Pictures/joss-stone1.jpg ./

./ is for your current directory. ~ is for your home directory.


if you type "pwd" it will print what directory you are in. "ls" will list files in that directory. Just do it without the " marks :)

---

### Post by DeMartini on 2010-01-27
> **t4thfavor said:**
> ```

cd Pictures
cp mypic.jpg ../Desktop/test

or to copy all pics

cp *.jpg ../Desktop/test

```

the ../ means the directory above this one.

Also you cannot forget that Linux is case sensitive so Desktop is a different folder than desktop. same with files 1A.jpg is different than 1a.jpgThank You, just trying to get better at all this

---

