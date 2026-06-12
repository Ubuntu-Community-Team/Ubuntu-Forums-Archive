---
title: "Regular expression help"
date: 2010-06-02
forum: General Help
---

### Post by killthemyth on 2010-06-02
Hi guys, 

I need help regarding regex. I want a single regular expression so that when I use my regular expression in any string thn it should return the result in order. What I need is:

1. fino 24 december 2004
2. fino 24 december 
3. fino december
4. 2004
5. fino
6. december
7. fino 24 december 04


I have done homework, but happens is that when I run my regex thn it miss 4, 5.
Is there any way for regular expression to make it include ([nothing] or [blankspace])
I mean for ex: regex: fino([nothing] or [blankspace])[0-9][0-9] can be able to find 
fino or fino 24

hope u understand ..n thnks in advance for help

---

### Post by ThesaurusRex on 2010-06-02
A question mark means 0 or 1. I'm not sure of the exact syntax, but something like...

```
(other_stuff)?[ ](other_stuff)
```

---

