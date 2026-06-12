---
title: "ping output to txt file?"
date: 2011-01-18
forum: General Help
---

### Post by gypsumwolf on 2011-01-18
How do i write ping output to txt file?

---

### Post by dabl on 2011-01-18
In a terminal, from your /home/gypsumwolf prompt:

```
ping www.google.com > googleping.txt
```

Give it a minute, then Ctrl-C to stop it.  Now you can 

```
cat googleping.txt
``` and see the results.

---

### Post by gypsumwolf on 2011-01-18
..

---

### Post by gypsumwolf on 2011-01-18
Thanks, this is what i did as a modification of your response. Works great!

```
$:/stuff# ping -c 1 google.com > ping.txt
$:/stuff# nano ping.txt
```

---

