---
title: "svn download error"
date: 2009-09-25
forum: General Help
---

### Post by r5r4y on 2009-09-25
Hello,
i'm trying to use svn for the first time, i want to download this: [http://svn.gnome.org/viewvc/nautilus/trunk/src/file-manager/](http://svn.gnome.org/viewvc/nautilus/trunk/src/file-manager/)

but when i'm typing svn co [http://svn.gnome.org/viewvc/nautilus/trunk/src/file-manager/](http://svn.gnome.org/viewvc/nautilus/trunk/src/file-manager/) in terminal it's says:

```
svn: Repository moved temporarily to '/viewvc/nautilus/trunk/src/file-manager/'; please relocate
```

what should i do?

---

### Post by geirha on 2009-09-25
A very cryptic message, indeed. Apparently, gnome has migrated from svn to git, which may explain why you're unable to checkout the subversion repository.

[http://live.gnome.org/Git](http://live.gnome.org/Git)

(You'll want the [git-core](apt://git-core) package to get the git commands. The package called git is a completely different program; gnu interactive tools.)

---

### Post by r5r4y on 2009-09-25
i know git, than how should i download the files there?
git checkout [http://svn.gnome.org/viewvc/nautilus/trunk/src/file-manager/](http://svn.gnome.org/viewvc/nautilus/trunk/src/file-manager/)

fatal: Not a git repository

---

### Post by Ayuthia on 2009-09-25
It looks like the location changed:
git://git.gnome.org/nautilus

---

### Post by r5r4y on 2009-09-25
git checkout git://git.gnome.org/nautilus

still same error: fatal: Not a git repository

---

### Post by geirha on 2009-09-25
I haven't used git much, but I believe «clone» is the equivalent of svn's «checkout» ...

---

### Post by Ayuthia on 2009-09-25
> **geirha said:**
> I haven't used git much, but I believe «clone» is the equivalent of svn's «checkout» ...

You are correct.  It should be:
```
git clone git://git.gnome.org/nautilus
```

---

