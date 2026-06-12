---
title: "gonna try to make a Gens .deb"
date: 2006-02-05
forum: General Help
---

### Post by chronusdark on 2006-02-05
im gonna try to do this but im not familiar on how to make .deb files...can someone point me in the right direction?

---

### Post by cdhotfire on 2006-02-05
First
```

$ sudo apt-get install build-essential dhmake fakeroot

```

Second, unpack the source and cd to folder
```

$ cd folder

```

Third, run dhmake
```

$ dh_make

```
What one usually compiles are single binarys, so press "s" then "enter" when it asks you.

Fourth
```

$ fakeroot debian/rules binary

```

If it encounters any errors during the configuration, it should tell you what to install. 

After its done it should make a "deb" on .. so do
```

$ sudo dpkg -i ../package.deb

```
To install.

Good luck.

---

### Post by chronusdark on 2006-02-05
i cant find dhmake in the brezzy repos

found it its dh_make

---

### Post by cdhotfire on 2006-02-05
[QUOTE=chronusdark]i cant find dhmake in the brezzy repos

found it its dh_make[/QUOTE]

Oops, sorry, it was dh-make. :|

---

