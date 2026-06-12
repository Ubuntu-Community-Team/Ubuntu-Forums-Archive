---
title: "reading output line by line"
date: 2009-11-19
forum: General Help
---

### Post by mo.reina on 2009-11-19
how does one read output from commands line by line?

ex.
```
awk 'BEGIN { FS="," } { print NF }' $file
```

if i put the above example in a variable:
```
count=$(awk 'BEGIN { FS="," } { print NF }' $file)
```
the data (in this case the number of fields) are displayed in one line

```
cat $count
5 4 3 2 3 4
```

---

### Post by Bachstelze on 2009-11-19
What are the contents of your input file, and what output do you expect?

---

### Post by mo.reina on 2009-11-19
input file looks something like this

1,2,3,4,5
1,2,3,4
1,2,3
1,2

i'm trying to manipulate the output as it is coming out. 
ex.
print "hello" after each line, or if the number of fields (NR) = 5 do something, etc.

i tried the var=$(awk etc..) method thinking i could just read var and manipulate the data in the file, but the output is parsed into one line

---

### Post by mo.reina on 2009-11-19
ok i solved my own problem :rolleyes:

```
for *line* in *`command`*; do
*do_something_here*
done
```

---

