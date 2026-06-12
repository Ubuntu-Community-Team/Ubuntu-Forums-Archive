---
title: "Problem with History command"
date: 2010-09-20
forum: General Help
---

### Post by RocketMain on 2010-09-20
Hello all.

When I type in history I get /bin/sh: history: not found

How can I fix it so that I can see my past history of commands?



Thanks!

---

### Post by karthick87 on 2010-09-20
What version of ubuntu you are using..?

---

### Post by RocketMain on 2010-09-20
10.04

---

### Post by mali2297 on 2010-09-20
The history command is a feature of [bash](http://en.wikipedia.org/wiki/Bash_(Unix_shell)). My guess is that you for some reason are running [dash]("http://en.wikipedia.org/wiki/Debian_Almquist_shell") instead. You might need to change your login shell to /bin/bash (should have been the default). Type the command
```

chsh -s /bin/bash

```
Log out and in.

---

### Post by RocketMain on 2010-09-20
That fixed it, thanks!!

---

