---
title: "NET Framework 3.5 in Wine"
date: 2012-03-02
forum: General Help
---

### Post by layers on 2012-03-02
I have a patch on Age of Empires II I want to install, but it requires NET Framework 3.5, and from what I remember, it wasn't a favourite application to install on Wine. Can I use mono, and will it "trick" the patch, or do I have to torture myself with NET?

---

### Post by VH-BIL on 2012-03-02
Have you tried installing winetricks?
```
wget http://winetricks.googlecode.com/svn/trunk/src/winetricks
bash winetricks dotnet35
```

The winetricks wiki is here if you want to read about it: [(_winetricks_)]("http://wiki.winehq.org/winetricks")

---

