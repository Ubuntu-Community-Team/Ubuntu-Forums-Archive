---
title: "Matching _one_ character in grep"
date: 2009-07-17
forum: General Help
---

### Post by chellrose on 2009-07-17
What is the wildcard for a _single_ character in grep?  For example...

I have a bunch of subdirectories labeled by letters, e.g. set13a, set13b, and so on.  I'd like to figure out how many such "set13" subdirectories I have.  One grep tutorial mentioned that the dot (.) will match exactly one character, so I proceed thus:

```
ls|grep set13.
```The problem is that this matches not only the desired subdirectories, but also things like "set135d" and "set13ParameterList.txt".  How do I wildcard exactly one character?

Thanks! :)

---

### Post by lateralforce on 2009-07-17
Maybe this will do it
```
ls | grep -c set13[a-x]
```

---

