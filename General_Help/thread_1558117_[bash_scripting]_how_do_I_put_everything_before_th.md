---
title: "[bash scripting] how do I put everything before the word &quot;is&quot; in a variable?"
date: 2010-08-21
forum: General Help
---

### Post by compiz addict on 2010-08-21
I have this script:
```

#!/bin/bash
while [ 1 ]
do
if [ -a ./a.txt  ]
then
read -r com < ./a.txt

## var=everything in $com before the word is

echo $var
rm ./a.txt
fi
done

```

what do I use to put everthing before the word "is" in the string "com" to the variable "var"?

---

### Post by DaithiF on 2010-08-22
```
var=${com%is*}

```

---

