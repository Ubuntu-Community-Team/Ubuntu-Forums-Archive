---
title: "syntax error near unexpected token 'do'"
date: 2009-08-10
forum: General Help
---

### Post by pappysarmie on 2009-08-10
I'm trying to create symbolic links for an oracle installation on ubuntu server 8.04 and i typed this command:
for i in 0 1 2 3 4 5 6 S ; do ln -s /etc/rc$i.d /etc/rc.d/rc$i.d ; done

[FONT=Verdana]and i have the following error

[FONT=Arial]-bash: syntax error near unexpected token 'do'. what m i doing wrong? pls i need urgent help.[/FONT]
[/FONT]

---

### Post by michy99 on 2009-08-10
Try this:```
for i in {0 1 2 3 4 5 6 S} ; do ln -s /etc/rc${i}.d /etc/rc.d/rc${i}.d ; done
```

---

### Post by pappysarmie on 2009-08-11
i still get the same error though after adding the braces. what else can be done or is there another synopsis for the multiple links to be created?

---

### Post by pappysarmie on 2009-08-17
anyone with a solution yet? i need to finish with some oracle installation and i need to get the links created. Thanks

---

