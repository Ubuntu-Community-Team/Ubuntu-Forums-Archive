---
title: "Delete Java Web Start Application"
date: 2012-04-13
forum: General Help
---

### Post by gunksta on 2012-04-13
I installed an app or two via Java Web Start and I'd like to delete all but one of these applications. How do I do that? I looked in ~/.java and this doesn't seem to have what I'm looking for.

---

### Post by jonobr on 2012-04-13
You could try finding the applications using which maybe?
i.e.
```
$ which perl 
```

You need to get the program name though before you can which it

You could also try finding using the cli

```
sudo find / -name appname 
```

You can use * as a wilcard character


```
sudo find / -name  *.py 
```
Find files with a .py extension

---

