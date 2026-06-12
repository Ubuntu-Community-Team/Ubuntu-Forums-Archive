---
title: "Bash scripting: how to remove or sort lines in curl feed"
date: 2011-09-29
forum: General Help
---

### Post by layr on 2011-09-29
If i fetch data using curl and cut only few characters from it, say cut -c1-2, it cuts those characters from all the lines within the fetched data.
So if data received was:
JJJJ 99304
1234950

then end result after applying cut would be:
JJ
12

How could only JJ be cut from the feed?

EDIT:
answer is the sed command. To cut only, for instance 2nd line, this should be used:
```
 | sed -n 2p
```

---

