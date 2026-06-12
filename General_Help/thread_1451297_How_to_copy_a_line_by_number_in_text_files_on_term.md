---
title: "How to copy a line by number in text files on terminal?"
date: 2010-04-10
forum: General Help
---

### Post by shade5 on 2010-04-10
Hi.

I got a text file. Now I want to write a line by its number in a bash variable. That is all. Any ideas?

Thanks.

---

### Post by sisco311 on 2010-04-10
```

FILE="path/to/file"
NUMBER=10
LINE=$(awk -v n=$NUMBER 'NR == n {print;exit}' $FILE)
echo $LINE

```

---

