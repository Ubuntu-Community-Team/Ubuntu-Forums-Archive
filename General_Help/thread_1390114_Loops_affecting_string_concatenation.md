---
title: "Loops affecting string concatenation"
date: 2010-01-25
forum: General Help
---

### Post by Mr_Lazy on 2010-01-25
Hi,

I have a number files with some rows of information I want to extract, at the same time I want to add to a string some details from the file. I have found two different ways of looping over rows in a file, but one method doesn't let me concatenarte strings and I don't know why....

The first method sets the IFS environmental variable. I don't really favour this method, but it works..

```
#!/bin/bash -
OLDIFS=$IFS
IFS='
'

STE="cat"
  
for FILE in $( ls *-df | cut -f 4 -d / ); do
  N=0
  for LINE in $( cat $FILE ); do
    N=$((N+1))
    STE="$STE""dog"
  done
done
echo "$STE" && exit
```

and produces:
catdogdogdogdogdogdogdogdogdogdogdogdogdogdogdogdogdogdogdogdogdogdogdogdogdogdogdogdog


Method 2 uses "read" but prevents the concatenation of the string:
```
#!/bin/bash -
STE="cat"
  
for FILE in $( ls *-df | cut -f 4 -d / ); do
  N=0
  cat "$FILE" | while read LINE ; do
    N=$((N+1))
    STE="$STE""dog"
  done
done
echo "$STE" && exit

```

and produces:
cat

Why is there a difference in the two methods? I would rather not be changing environmental variables and a simple loop is my preferred choice. 

Thanks for your help,
Stephen

---

