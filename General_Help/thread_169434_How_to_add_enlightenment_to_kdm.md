---
title: "How to add enlightenment to kdm?"
date: 2006-05-02
forum: General Help
---

### Post by El Menda on 2006-05-02
I've installed Enlightenment 17 following this manual and i'd like to know how can I add an entry to KDM so I could start it.
Im using Kubuntu Breezy

Thanks :mrgreen:

---

### Post by bobbymcsteels on 2006-05-02
[QUOTE=El Menda]I've installed Enlightenment 17 following this manual :[/QUOTE]
Which manual is that then?? :p

---

### Post by El Menda on 2006-05-02
Lol sorry, i did the link but it didnt display:
[http://www.ubuntuforums.org/showthread.php?t=97199](http://www.ubuntuforums.org/showthread.php?t=97199)

I will be happy if u help me! If not ill have to kill a kitten! haha

---

### Post by El Menda on 2006-05-03
It was solved:
I've created this file /usr/share/xsessions/enlightenment.desktop which look like this:

[Desktop Entry]
Encoding=UTF-8
Type=XSession
Exec=/usr/bin/enlightenment
TryExec=/usr/bin/enlightenment
Name=Enlightenment 17

Bye!

---

### Post by barbarian on 2006-05-03
Hmm, strange, shouldn't it placed automaticaly after session restarting? I have installed openbox and I had not to add anything manually..

---

### Post by El Menda on 2006-05-04
yeah, but that only happens when u install it using apt-get. I have compiled it from source

---

### Post by barbarian on 2006-05-04
Aha, yes, my mistake.. I didn't read the entire thread..

---

