---
title: "Cutting text."
date: 2010-04-23
forum: General Help
---

### Post by nl4m on 2010-04-23
Lets say the text is:

aaa
aaa
aaa
bbb
ccc
ccc
ccc


Now I want to cut the "bbb" part and all the text above it. Basically just leave the three lines of "ccc"'s. How do I do that ? 

I tried "cut -d"b" -f3-". It did a great job cutting out all the "B"'s in that line, but it left all the "a"'s intact.

---

### Post by phinullfermata on 2010-04-23
You can try using sed. For example, instead of deleting everything from the top to before matching 'ccc' you can think of printing 'ccc' to the end of the file:

```
sed -ne '/ccc/,$p' yourtextfile
```Or, if you only want the lines with 'ccc' to process, you could try using grep:

```
grep 'ccc' yourtextfile
```

---

### Post by nl4m on 2010-04-23
> **phinullfermata said:**
> You can try using sed. For example, instead of deleting everything from the top to before matching 'ccc' you can think of printing 'ccc' to the end of the file:

```
sed -ne '/ccc/,$p' yourtextfile
```Or, if you only want the lines with 'ccc' to process, you could try using grep:

```
grep 'ccc' yourtextfile
```

If the content of a file is:
apple
banana
cherry
kiwi
orange
watermelon

Now if I wanted to delete the first four lines (delete apple, banana, cherry) and just leave in the file "kiwi, orange, watermelon" I would type ```
sed -ne '/kiwi/,$p' yourtextfile
``` ???

---

