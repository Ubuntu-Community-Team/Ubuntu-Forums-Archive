---
title: "bash scripting with mutt"
date: 2012-04-21
forum: General Help
---

### Post by dsmo223 on 2012-04-21
I have a little mailing script that I have been using that looks like the following:

```
#! /bin/bash 

mutt -x -s "SUBJECT LINE HERE" -i email.txt -b email@address -a ./file.html -- email@anotheraddress
```The way that this works for every one of the mutt lines, it asks me to put a '.' on a line by itself (of coarse without the quotes), is there a way to automate the putting the dot on a line by itself?

Thank you for your help

---

