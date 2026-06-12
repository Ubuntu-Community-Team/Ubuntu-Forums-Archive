---
title: "How do I use GIT?"
date: 2009-12-23
forum: General Help
---

### Post by Hawk__0 on 2009-12-23
I want to install vlmc, and I have no idea how "git" works.
git clone git://github.com/VLMC/vlmc.git

That is the command.. I ran it, but don't know how to install it :(

---

### Post by aV Echelon on 2009-12-23
If I were you I would wait for the final release in February. This process is pretty annoying, I keep getting error messages when I try to make it.

---

### Post by Vaphell on 2009-12-23
probably you got the sources from git repository, so now you are supposed to do configure/make/make install combo to compile and install

```
./configure
make
sudo make install
```

---

### Post by Hawk__0 on 2009-12-23
Thanks vaphell, I didn't realize that the command created the source directory! Turns out you have to use qmake in this case.

Edit:

aV Echelon is right.  Make errors for me too.

---

### Post by andrew.46 on 2010-02-20
I have written a guide which allows for the building of vlc-git and vlmc:

Howto: Build the development version of vlc under Ubuntu
[http://ubuntuforums.org/showthread.php?t=1398119](http://ubuntuforums.org/showthread.php?t=1398119)

but it is quite a complex guide and you might consider waiting for the release version of vlmc if the guide looks a little daunting?

Andrew

---

