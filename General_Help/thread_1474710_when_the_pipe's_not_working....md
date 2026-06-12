---
title: "when the pipe's not working..."
date: 2010-05-06
forum: General Help
---

### Post by Eraemaajaervi on 2010-05-06
hi,
this is not a problem, but some terminal commands won't accept pipeline connects, e.g.

```

$ echo "FreeSerif.ttf" | dpkg -S

```
gives me an error ("need a filename"), while 
```

$ dpkg -S FreeSerif.ttf

```
gives me exactly what i want.
is there a way to pass the standard output to the program/command as an argument?

thanks

---

### Post by cdenley on 2010-05-06
```
dpkg -S `echo FreeSerif.ttf`
```

---

### Post by kaibob on 2010-05-06
Post deleted by kaibob.

---

### Post by kaibob on 2010-05-06
> **Eraemaajaervi said:**
> hi,
this is not a problem, but some terminal commands won't accept pipeline connects, e.g.
<xnip>
is there a way to pass the standard output to the program/command as an argument?

thanks

I don't know if it would be a very good idea in this particular instance, but I think xargs will do what you want.

[http://manpages.ubuntu.com/manpages/jaunty/man1/xargs.1.html](http://manpages.ubuntu.com/manpages/jaunty/man1/xargs.1.html)

---

### Post by Eraemaajaervi on 2010-05-07
thanks kaibob, xargs does what i need =)

why wouldn't it be a good idea?

--> solved

---

### Post by kaibob on 2010-05-07
> **Eraemaajaervi said:**
> thanks kaibob, xargs does what i need =)

why wouldn't it be a good idea?

--> solved

I shouldn't have said that. I don't know what you'll be doing, and I know next to nothing about dpkg, so I should have kept quiet on this point. I'm glad xargs worked for you.

---

