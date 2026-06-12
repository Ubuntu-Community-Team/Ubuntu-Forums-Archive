---
title: "grep, print only word that matches pattern"
date: 2009-09-27
forum: General Help
---

### Post by meg23 on 2009-09-27
I am trying to get grep to print out a single word pattern. For instance, I want grep to print out any word that has $ attached to it, for instance $zebras. I have tried *grep -o '$*'*, any suggestions on how to achieve this?

---

### Post by StuartN on 2009-09-27
> **meg23 said:**
> any word that has $ attached to it, for instance $zebras

If you mean literally the character "$" in a word, then you would need to escape the special meaning of $ as an end-of-line character. In this case **grep \$zebras** should work.

---

### Post by meg23 on 2009-09-27
When I run grep -o "\$*", the only output I receive is "$"

---

### Post by StuartN on 2009-09-27
> **meg23 said:**
> When I run grep -o "\$*"

What files are you searching? Typically you would have something like **grep -o \$zebra *.txt** to search for words containing $zebra in all files of type .txt, or **grep \$zebra *.txt** to see the whole of each line containing each match.

---

### Post by meg23 on 2009-09-28
I am actually trying to edit a stream from twitter updates. Although, I should probably use sed, a stream editor, I never remember the syntax. Anyways, I am basically grabbing text from twitter and trying to grab any word that has a $ attached to it, $*, and dump it to a text for further processing  

```
twidge lsreplies | grep -m 1 $zebra | grep -l "$" > text.txt
```

---

### Post by diesch on 2009-09-28
Does ```
grep  -o '\$\w*'
``` what you want?

If not please give an example of some input and the output you want from it.

---

### Post by falconindy on 2009-09-28
Nevermind... Diesch's solution is better...

---

