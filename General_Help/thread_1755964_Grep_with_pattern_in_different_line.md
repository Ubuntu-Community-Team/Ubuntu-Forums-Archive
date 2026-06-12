---
title: "Grep with pattern in different line"
date: 2011-05-11
forum: General Help
---

### Post by bitscarre on 2011-05-11
Can someone please explain what happens in this command: Logfile structure:

IPsrc:IPdst:port:packets

```
Line 1: @ max=`cut -f4 -d: logfile | sort -n -r | head -1`
Line 2: grep "$max"$ logfile | cut -f1,3,4 -d: | sort | uniq
```


I can't understand how the first line is used to define a pattern for grep.

I am using ubuntu to test this.

Any link/explanation is helpful.

Tx.

---

### Post by bitscarre on 2011-05-11
[http://superuser.com/questions/282297/linux-commands-piping-grep-and-matching-pattern](http://superuser.com/questions/282297/linux-commands-piping-grep-and-matching-pattern) answered here

---

