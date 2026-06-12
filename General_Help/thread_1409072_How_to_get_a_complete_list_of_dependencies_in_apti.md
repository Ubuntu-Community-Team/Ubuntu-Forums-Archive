---
title: "How to get a complete list of dependencies in aptitude"
date: 2010-02-17
forum: General Help
---

### Post by YourSurrogateGod on 2010-02-17
I looked at the package scrot and then at its dependencies in aptitude.  I'm curious how I can get a complete list of those dependencies and the dependencies below them and below those, etc.  Anyone know?

If possible, ideal, I'd like to get a nice visual graph.

---

### Post by nothingspecial on 2010-02-17
This wont give you a nice graph but

```
apt-cache depends --recurse *package*
```

You might want to pipe it through less;)

---

