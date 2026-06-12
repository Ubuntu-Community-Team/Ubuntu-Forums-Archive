---
title: "bash scripting help"
date: 2006-04-15
forum: General Help
---

### Post by krismatth3 on 2006-04-15
This one consistently bites me in the rear. Suppose I have the following code:

```

#!/bin/sh
for ENTRY in `cat ~/myfile`; do 
  echo "entry: $ENTRY"
done

```

As long as ~/myfile is like this:
```

entry_one
entry_two
entry_three

```

the mentioned code works fine. Now if we change the file to 

```

entry one
entry_two
entry_three

```

the code produces:

```

entry: entry
entry: one
entry: entry_two
entry: entry_three

```

e.g. the space in "entry one" is causing "entry one" to be read as two items. I have the same problem in this situation:

```

#!/bin/sh
for FILE in `ls`; do 
  echo $FILE
done

```

It works fine, unless you have a filename with a space in it. ](*,)

---

### Post by trent dillman on 2006-04-15
```

#!/bin/bash
for (( i=1 ; i<=`cat ~/file | wc -l` ; i++))
do
     ENTRY=`cat ~/file | sed -n "${i}p"`
     echo "entry: $ENTRY"
done
```

Damn spaces will get you every time...

---

### Post by krismatth3 on 2006-04-16
I found another way:
```

#!/bin/sh
OLDIFS=$IFS && IFS=$'\x0A'$'\x0D'
for ENTRY in `cat ~/myfile`; do 
  echo "entry: $ENTRY"
done
IFS=$OLDIFS

```

These sets IFS (field seperator variable) to consider only the newline OR carrigage return as a field seperator, not whitespace or anything else. Thanks.

---

### Post by simonn on 2006-04-16
If you want the whole line:

```

cat ~/myfile | while read entry
do 
  echo "Entry: ${entry}"
done

```

---

