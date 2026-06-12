---
title: "regex search replace help"
date: 2011-03-27
forum: General Help
---

### Post by ender8282 on 2011-03-27
I have a question about search replace (with vi or sed) using regex.  I want to use regex to match some characters of interest, but then only replace part of match.  For example I want to search for [0-9]:1234: and replace it with [0-9]:7890:.  I only care about matches where the first character is a number but I don't actually want to change the first character.  

Thanks in advance.

---

### Post by Vaphell on 2011-03-27
groups/backreferences to the rescue:
```
echo '1:1234:' | sed -r 's/([0-9]):1234:/\1:7890:/'
1:7890:
```

in short: stuff in () is a group that gets an id (integers counting from 1) and in replacement part you can call it with \1 \2 \3 etc

---

### Post by ender8282 on 2011-03-28
Perfect!!! That was exactly what I needed.  I knew that they had to be a way to do it. Thanks a bunch.

---

