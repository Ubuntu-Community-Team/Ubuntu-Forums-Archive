---
title: "Problem using dconf"
date: 2012-01-27
forum: General Help
---

### Post by sptutusukanta on 2012-01-27
**I want to change the value of key "/org/gnome/desktop/background/picture-uri" using script.**
The value should be "file:///home/sukanta/syncwall23224".
So I ran the command:
```
dconf write "/org/gnome/desktop/background/picture-uri" "file:///home/sukanta/syncwall23224"
```

But its not working.
I tried to change some integral or boolean datatypes, it worked perfectly.
But whenever I tried to put any string value it is showing:
```
error: 0:expected value
```

Why this is happening? **How to change values of STRING datatype?**

---

### Post by sptutusukanta on 2012-01-27
Oh... I got the solution.

I Have to **wrap the string into a string**.
That is:
```
dconf write "/org/gnome/desktop/background/picture-uri" "'file:///home/sukanta/syncwall23224'"
```

---

