---
title: "Simple bash for loop help"
date: 2010-05-21
forum: General Help
---

### Post by Morat on 2010-05-21
I am trying to write a simple bash script that performs a command on each **line** of a given input file. I can do it for each **word** with the following:
```
for i in $(cat myfile.txt) ; do
    myprocessing $i
done
```

but I want it done for each line, not each word so I want the carriage return only to be the delimiter, not any white space. I have tried using quotes and explicitly escaping each space character with a backslash but neither of these make any difference.

Any ideas?

--- Morat

---

### Post by DaithiF on 2010-05-21
Hi,

```
while read line
do
   echo $line
   # do other stuff here
done < somefile

```

---

