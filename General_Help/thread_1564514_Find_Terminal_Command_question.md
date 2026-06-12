---
title: "Find Terminal Command question"
date: 2010-08-30
forum: General Help
---

### Post by cloverz7 on 2010-08-30
I need to figure out how to find the first 9 things in two directories that end in .csv


Any help ;P

---

### Post by DaithiF on 2010-08-30
Hi, what do you mean by first -- alphabetical, date, etc?

---

### Post by cloverz7 on 2010-08-30
Well the files are labeled like Aug01.csv Aug02.csv so on and so forth, I just need the Aug01.csv through Aug09.csv and Jul01.csv through Jul09.csv

---

### Post by mr clark25 on 2010-08-30
well, you could do something like this:
```

find /path/to/parent/directory/Aug*.csv

```

the "*" is a wildcard. you will need to replace "Aug" with the beginning of the file you want.

---

### Post by AlphaLexman on 2010-08-30
@mr clark25: I believe you forgot the '-name' identifier, a better choice:
```
find . -name "???0[1-9].csv"
```will give the first nine days of every month with a three character 'date code'

---

### Post by Old *ix Geek on 2010-08-30
> **mr clark25 said:**
> well, you could do something like this:
```

find /path/to/parent/directory/Aug*.csv

```

the "*" is a wildcard. you will need to replace "Aug" with the beginning of the file you want.

But that doesn't limit the results to the first nine files as s/he wants.

Try these:
```
find . -name "Jul0[1-9].csv"
find . -name "Aug0[1-9].csv"
```

The '.' will cause 'find' to look in the directory you're in, plus any subdirectories it may have. You can adjust that depending on where the files are.

---

### Post by cloverz7 on 2010-08-30
Thanks for all the help, kind of used a combination of all things posted. You can use 

find /path/to/search/file/one /path/to/search/file/two 

as for the specific files I used a -name "*0[1-9].csv"

---

