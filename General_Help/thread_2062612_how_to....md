---
title: "how to..."
date: 2012-09-25
forum: General Help
---

### Post by idontcheat on 2012-09-25
Can someone know how to create a bash scripting which can read and count vowels (input.txt) in a text files which uses grep commands?

---

### Post by diesch on 2012-09-25
```
grep -oe '[aeiou]' input.txt | wc -l
```

---

