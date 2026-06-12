---
title: "Terminal Output to Window and File"
date: 2011-01-18
forum: General Help
---

### Post by Shadow21 on 2011-01-18
I know how to make the Terminal output information to a file using

```
"command" > filename.txt
```

but then it doesn't show the information in the terminal window so how do I make it output to the terminal and to a file at the same time?

---

### Post by piquat on 2011-01-19
> **Shadow21 said:**
> I know how to make the Terminal output information to a file using

```
"command" > filename.txt
```but then it doesn't show the information in the terminal window so how do I make it output to the terminal and to a file at the same time?

With ls:

```
ls | tee test.txt
```

---

