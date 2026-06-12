---
title: "Making one shortcut for multiple applications?"
date: 2010-09-04
forum: General Help
---

### Post by arcelivez on 2010-09-04
Hello,

is it possible to make one shortcut open multiple apps? I do succeed with this in command line, but the normal shortcuts used in Ubuntu don't work with the same command ( it opens just one of the apps).

Maybe I'm just using the wrong command?
I'm using:
```

java -jar application1 & application2 &

```
(note that the first application is a jar file).
I want both programs to be opened together. Is there a way to do that using shortcuts in Ubuntu (aka launchers?) ?

Thanks.

---

### Post by Smart Viking on 2010-09-04
Yes, do like this:

```
firefox && gnome-terminal --geometry=50x80 &&  gimp
```

And so on. :)

---

### Post by arcelivez on 2010-09-04
Yes, I've tried that, but it just opens one applications, then waits for it to get closed, to open the next one (in terminal), and when I use the command in Ubuntu launcher, nothing happens at all. :S Nothing starts. :S

---

