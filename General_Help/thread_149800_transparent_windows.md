---
title: "transparent windows"
date: 2006-03-24
forum: General Help
---

### Post by chocolatetoothpaste on 2006-03-24
How do people do transparent windows?  I have seen so many nice screenshots, but no one says how to do transparencies.  Is it just part of some themes, or can I turn this on?

---

### Post by krusbjorn on 2006-03-24
There are numerous of ways. The easiest way is probably via [xcompmgr and transset]("http://ubuntuforums.org/showthread.php?t=75527&highlight=vista-ish"), but you might also wanna have a look at [xgl/compiz]("http://ubuntuforums.org/showthread.php?t=148351&highlight=thread+rule").

---

### Post by taurus on 2006-03-24
You can also get a transpanent terminal.  I like aterm and after installing it with apt-get, I just set this in my ~/.bashrc
```

Aterm='aterm -fn 6x14 -tr -trsb -cr green -sl 1000 -fg green -shading 50 &'

```
And whenever I call "Aterm" from a terminal, aterm will open with transparency background...

---

