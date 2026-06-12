---
title: "sort a list in a file using terminal"
date: 2010-10-21
forum: General Help
---

### Post by fasoulas on 2010-10-21
How can i sort a file like this using the sort command;
for column 1 is sort list
 
george	43	car
anton	17	bike
felipe	21	chair
andrew	3	mouse
jordan	67	screen
sunny	2	lawn
peter	55	ring
marcelo	7	dog

I want to be able to sort this list based on column 2(numerical) and then for column 3

i tried the sort -n list but it outputs the same as using just sort.

---

### Post by AlphaLexman on 2010-10-21
```
sort -nk2,3 -t" " filename.txt
```

---

### Post by fasoulas on 2010-10-22
> **AlphaLexman said:**
> ```
sort -nk2,3 -t" " filename.txt
```

thanks

---

