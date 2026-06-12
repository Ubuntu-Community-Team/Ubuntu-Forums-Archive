---
title: "how to sort words in order to avoid a1,a11,a2"
date: 2009-11-24
forum: General Help
---

### Post by morelam on 2009-11-24
Hello!
I'm trying to find an answer to this question over net something like 2 or more hrs. Finally I try here. It's very important for me to create list of licences plates in alphabetical order. I can't do such a list couse enties like: a1,a2,a11 are sorted in order of a1, a11, a2. I have used command sort and notepad to sort the list, but now i realize that the list does not looks like in order, and incloudes  only plates numbers. Advise me how to do sort it a1,a2,a11, otherwise I will how to collect informations about model and color, I would like to avoid it. Thank you

---

### Post by Bag-O-Stuff on 2009-11-24
I think you want "sort -n".  If you have a text.txt file with the following in it:

```
a1
a11
a2
```

Then do this:

```
cat text.txt | sort -n
```

The output will be:

```
a1
a2
a11
```

---

