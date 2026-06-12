---
title: "sed - binary addition"
date: 2011-03-26
forum: General Help
---

### Post by pizet on 2011-03-26
Hello. I would like to simulate a binary addition of *1* just with the program sed (it will get a number *n* on input and replace it with a number, which equals *n+1*).

I know how to solve the problem when the number in base *2* is even. I just swap the last *0 *with* 1*:
```
sed -r 's/^([01]*)0$/\11/'
```.

But how to solve it when the number is odd (there is *1* at the end)? Any ideas?

Thank you.

---

