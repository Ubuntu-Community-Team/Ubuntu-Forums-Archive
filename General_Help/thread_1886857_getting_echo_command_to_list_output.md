---
title: "getting echo command to list output"
date: 2011-11-25
forum: General Help
---

### Post by trusdamanr on 2011-11-25
I'm trying to do the following command in the terminal 

echo {a..z}{a..z} > list.txt


My question is how to get my results to display as a list...ex
aa
ab
ac
ad

The current command lists the results in a line ..ex aa ab ac ad ae ....etc

---

### Post by WorMzy on 2011-11-25
Add a newline character.

```
echo -n {a..z}{a..z}\n > list.txt
```

---

### Post by garyed on 2011-11-25
```

for i in {a..z}{a..z}; do echo $i; done > list.txt

```

---

### Post by trusdamanr on 2011-11-25
@Wormzy the newline character still did the same thing and added n to all the combos....

garyed..thank you much sir...that was exactly what I needed!!

---

