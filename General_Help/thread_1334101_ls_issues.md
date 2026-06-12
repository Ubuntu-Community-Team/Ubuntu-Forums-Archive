---
title: "ls issues"
date: 2009-11-22
forum: General Help
---

### Post by mo.reina on 2009-11-22
i cam across something as i was writing a script that i've never encountered before.  i used to always redirect output of commands such as ls and find to files then redirect input of other commands to those files.  now i'm trying to script without relying so much on file redirection:

```
for line in $(ls); do
    echo $line
done
```

if the file name contains more than 1 word, echo outputs each word on a separate line.  is there any particular way to avoid this or do i have to redirect **ls >** *file*, then just do:

```
for line in *file*; do
    echo $line
done
```

---

### Post by sisco311 on 2009-11-22
```
ls |\
while read file; do
  echo "$file"
done
```

---

### Post by mo.reina on 2009-11-22
so no way to do this with a for loop and ls?

---

### Post by sisco311 on 2009-11-22
```
for file in "$(ls)"; do echo "$file"; done
```

---

### Post by mo.reina on 2009-11-22
cool, what difference did the double quotes make?

---

### Post by mo.reina on 2009-11-22
i just read that the globbing feature can also be used:

```
for line in ./*; do
     echo $line
done
```

where **./*** stands for the present working directory.  AFAIK though this only limited to the listing files, so not applicable for *find*, *locate*, and other commands.

---

