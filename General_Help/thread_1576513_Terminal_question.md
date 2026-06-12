---
title: "Terminal question"
date: 2010-09-17
forum: General Help
---

### Post by BULLIT22 on 2010-09-17
Hey guys, gals,

If I entered a o in the file search bar of the gui and it displayed all files in that directory that contained a o. what would be the terminal equivalent to searching for a few files in a directory for one letter not necessarily at the end or beginning of a word, but anywhere in the word?  

Thanks

---

### Post by Bachstelze on 2010-09-17
```
ls *o*
```

or

```
find . -name "*o*"
```

Depending on whether you want to also search in subdirectories.

---

### Post by Grenage on 2010-09-17
```
find / -name *abc*
```

---

### Post by BULLIT22 on 2010-09-17
WOW, I feel like an idiot. I'm taking a linux class and out of 25 questions, all on basic and advance file processing and this was hemming me up since last night. Thanks guys, never thought to add a * before and after.

---

