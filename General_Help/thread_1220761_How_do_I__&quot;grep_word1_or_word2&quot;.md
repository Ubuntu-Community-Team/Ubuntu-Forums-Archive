---
title: "How do I  &quot;grep word1 or word2&quot;"
date: 2009-07-23
forum: General Help
---

### Post by falkTX on 2009-07-23
Hi there.
Just a quick question:
when I run, for example:
```
ls -l | grep Doc
```
It will print any file/dir that contains the word "Doc"

But I want it to print "Doc", "Mov" and "Pic"
Something like:
```
ls -l | grep Doc || Mov || Pic
```
I know that command doesn't work; that's why I need help on this

Please tell me this is possible

---

### Post by sisco311 on 2009-07-23
```
ls -l | grep -e Doc -e Mov -e Pic
man grep
```

---

### Post by falkTX on 2009-07-23
> **sisco311 said:**
> ```
ls -l | grep -e Doc -e Mov -e Pic
man grep
```

Thanks for the quick reply!

Haven't see that on the man page

---

