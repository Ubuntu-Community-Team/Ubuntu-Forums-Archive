---
title: "shell scripting homework"
date: 2010-02-09
forum: General Help
---

### Post by seandude on 2010-02-09
I'm trying to make a shell script to help me with basic discrete mathematics.  The script I'm trying to make is to count the number of elements within a given set.

This works when typed directly into the terminal:

cat a|sed 's/ /\n/g'|sort|uniq|wc -l


When I try to put that in an executable called card, replacing the "cat a" with "cat $*" or "cat $1", the terminal outputs:

card: could not find help message for a


Does anyone know a solution?

---

### Post by pbrane on 2010-02-09
Would you post the script? If 'a' is the file containing the set then you probably should use 'cat $1'. And maybe add '-e' arg to sed.

```

#!/bin/bash

cat $1 | sed -e 's/ /\n/g' | sort | uniq | wc -l

exit

```

---

### Post by Richard1979 on 2010-02-09
Try enclosing the entire thing in double quotes.

Or maybe:

cat "a"|sed "'s/ /\n/g'"|sort|uniq|wc "-l"

---

### Post by pbrane on 2010-02-09
The double quotes *should* only be needed to expand variables used in the sed statement. Like **sed "s/ /$token/g"**. It is possible that double quoting **$1** may be needed.

---

