---
title: "sed editing"
date: 2012-03-14
forum: General Help
---

### Post by Drenriza on 2012-03-14
Hi guys.
I was wondering, how can you with sed add the character # at the beginning of a line. But only for the last line in a file?
 
Thanks on advance.
Kind regards.

---

### Post by codemaniac on 2012-03-14
```
awk 'NR==1{print "#"$0}' input_file
```
This would insert a "#" character to the first line of the input file .
```
awk '{ll=$0}END{print "#"ll}'
```
will insert a # before the start of last line .

---

### Post by codemaniac on 2012-03-14
Below are the sed equivalents .

```
sed '1s/^/#/' input_file
sed '$s/^/#/' input_file
```

---

### Post by Drenriza on 2012-03-16
Hi Codemanic.
 
Thanks for your reply.
Worked like a charm.
 
Kind regards.

---

