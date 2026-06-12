---
title: "anyone know how to put an environment variable back to its default?"
date: 2010-03-02
forum: General Help
---

### Post by honey toast on 2010-03-02
Hello all, 
:D
I am happy to say that after almost a week of wandering around the INTERNET and posting desperate questions to our Ubuntu forums on how to set paths etc., I have finally begun to understand just how environment variables and path setting works. I must say, it wasn't all reading this or that, but rather making changes to my paths that helped me to understand. Anyway, if anyone who does not understand environment variables is reading this, then I recommend reading this \
[HTML]
http://java.sun.com/docs/books/tutorial/essential/environment/paths.html
[/HTML]and this
[HTML]
http://www.belugalake.com/java/pathsetting.html
[/HTML]OK- I have 1 last question for my fellow linux users. Lets say I opened up $HOME /.profile and did some editing, and later decided to undo all of my changes but I forgot exactly what changes I made so now I want to set the default in there. How would I accomplish this? How do I set the defaults for any ~/.bashrc or ~/.cshrc type of files that I change. THanks for reading! :)

---

### Post by KiLaHuRtZ on 2010-03-02
```
cp /etc/skel/.profile ~/.
```

---

