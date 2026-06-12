---
title: "GUI compiler?"
date: 2006-04-11
forum: General Help
---

### Post by WSTGangsta on 2006-04-11
Is there a compiler software to compile tar gzip source code that uses some kind of GUI?
Thanks.

---

### Post by njf on 2006-04-11
Kompile
[http://www.kde-apps.org/content/show.php?content=30223](http://www.kde-apps.org/content/show.php?content=30223)

Kconfigure
[http://www.kde-apps.org/content/show.php?content=17183](http://www.kde-apps.org/content/show.php?content=17183)

---

### Post by WSTGangsta on 2006-04-12
Thank you!

(posting direct link so that it works with konquerer)
[http://www.brainspace.it/files/kompile_0.2-1_i386.deb](http://www.brainspace.it/files/kompile_0.2-1_i386.deb)

---

### Post by ComplexNumber on 2006-04-12
i use kinstaller. it works(for the most part) for me. i couldn't get kconfigure to install from tarball.

---

### Post by WSTGangsta on 2006-04-12
I tried Kinstaller because it looked nice, but when I try and install the tarball it says  
```
no acceptable C compiler found in $PATH
```
So...were do I get one, it actually says this on a majority of things I try installing.

---

### Post by GeneralZod on 2006-04-12
[QUOTE=WSTGangsta]I tried Kinstaller because it looked nice, but when I try and install the tarball it says  
```
no acceptable C compiler found in $PATH
```
So...were do I get one, it actually says this on a majority of things I try installing.[/QUOTE]



```

sudo apt-get install build-essential

```

---

### Post by WSTGangsta on 2006-04-12
Thanks zod that helped it get alot farther but now I get:
```
checking for X... configure: error: Can't find X includes. Please check your installation and add the correct paths!

```

---

### Post by GeneralZod on 2006-04-12
[QUOTE=WSTGangsta]Thanks zod that helped it get alot farther but now I get:
```
checking for X... configure: error: Can't find X includes. Please check your installation and add the correct paths!

```[/QUOTE]

What are you trying to install? Maybe it (or an earlier version of it) is in the repos, so we can take a shortcut! :)

---

