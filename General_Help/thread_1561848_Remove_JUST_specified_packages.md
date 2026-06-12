---
title: "Remove JUST specified packages"
date: 2010-08-26
forum: General Help
---

### Post by Ginswich on 2010-08-26
Hello, I want to remove three concrete packages, and just those three. Precisely, I want to remove libvorbis0a, libvorbisenc2 and libvorbisfile3. The problem is that when I do:

```
sudo aptitude remove libvorbis0a libvorbisenc2 libvorbisfile3
```

Aptitude wants to remove practically the whole Gnome system. I know this is due to interdependencies made between them because they have been installed as a single metapackage. But now, I want to remove just those packages.

If tried some options I found Googling, but anything works so far.

Thank you.

PS: My system is Ubuntu 9.10

---

### Post by WorMzy on 2010-08-26
As far as I know, there's no way of skipping dependency checks in aptitude/apt-get. You may be able to use dpkg to remove the package if you pass it the "--refuse-depends" or "--ignore-depends" flag. Be sure to use the "--no-act" flag to test these before you use one for real, just in case they try to do the same as apt.

e.g.
```
dpkg --no-act --refuse-depends --deinstall libvorbis0a libvorbisenc2 libvorbisfile3
```

run
```
man dpkg
``` for a full list of commands you can use with dpkg.

Of course, unless you have a very good reason for removing these three packages I'd recommend just leaving them alone. Removing them may cause more harm than good.

---

