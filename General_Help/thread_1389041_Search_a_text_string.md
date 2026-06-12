---
title: "Search a text string?"
date: 2010-01-23
forum: General Help
---

### Post by linuxnovice. on 2010-01-23
how can I search for a text string in ubuntu? its to find lines in php files 

thanks

---

### Post by audiomick on 2010-01-23
Hallo.
Look at the man pages for "find" and "grep". One or the other might be what you are after.
In a terminal
```
man find
```
```
man grep
```

---

### Post by iMisspell on 2010-01-23
I use the 'alias' below.
First move to the dir i want to search in, then run "phpsearch" from terminal.

```


alias phpsearch='echo -n " Search for what ? (must be in dir)" ;
read srt
grep -i "$srt" `find . -name "*.php" -print`
'


```

---

