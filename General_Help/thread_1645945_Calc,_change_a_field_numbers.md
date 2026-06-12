---
title: "Calc, change a field numbers"
date: 2010-12-15
forum: General Help
---

### Post by Mobidoy on 2010-12-15
I am trying to convert a numbering system in an old dbase file. I have manage to open it in calc and, before I use it as a table in a new database created with base, there is a field (column) I would like to modify.

The actual format is ex : 100-1234-56 I would like to:

add a 1 in front of it, keep the first 3 numbers, remove the dash, keep the next four numbers and remove the dash with the last 2 numbers like this: 

100-1234-56 would be 11001234

What are my options ?

---

### Post by TeoBigusGeekus on 2010-12-15
There you go.

---

### Post by papibe on 2010-12-15
I don't know about the dbase format, but if you're able to convert it to text, you can use a script with combination of awk and sed to convert any format like that. For example if you have a data file like this:
```
$ cat mydata
100-2341-56
200-3412-78
300-4123-90
400-1234-12
500-2341-34
```
You could use sed like this:
```
$ cat mydata | sed -e 's/\(...\)-\(....\)-\(..\)/1\1\2/'
11002341
12003412
13004123
14001234
15002341
```

or awk this other way:
```
$ awk  'BEGIN { FS = "-" }; { printf "1%s%s\n", $1,$2}' mydata
11002341
12003412
13004123
14001234
15002341

```
I hope it helps.

---

