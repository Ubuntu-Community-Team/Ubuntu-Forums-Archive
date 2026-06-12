---
title: "Help with script - read file"
date: 2011-06-08
forum: General Help
---

### Post by JCM_Pico on 2011-06-08
Hi there

How can I read a certain line, from  a certain row within a bash script

like I have a file with a line like:

hello = 10

And I want to take the value 10 to a script variable

---

### Post by AlphaLexman on 2011-06-08
To define a variable in bash there should be **NO** spaces around the equal sign '='
```
hello=10
```

---

### Post by doas777 on 2011-06-08
```
hello='Hello World!'
echo $hello
```

use an = to show you are declaring or setting a var, and $ when you are reading it.

---

### Post by JCM_Pico on 2011-06-08
and if I have a file like test.txt with

```
 apples = 1
oranges = 2
bananas = 3
```

and I want to read the numbers to put into a script... like

```
#!/bin/bash

fruit1 = (the number of apples)

and so on
```

????????

---

### Post by sisco311 on 2011-06-08
Try something like:
```

while IFS="= " read -r fruit nr
do
    if [[ "$fruit" == "apple" ]]
    then
        apple="$nr"
        echo "Nr. of apples = $apple"
    fi
done < file

```

EDIT: Is this your homework?

---

### Post by JCM_Pico on 2011-06-08
thanks

---

### Post by sisco311 on 2011-06-08
You're welcome!

But, you didn't answer my question. :evil:

---

### Post by doas777 on 2011-06-09
> **sisco311 said:**
> You're welcome!

But, you didn't answer my question. :evil:
  somethingtells me that the op wouldn't get away with turning it in anyway, if that is in fact the case. your script is too clean and concise for a beginner, unless they've already shown themselves as quite talented. most teachers have no trouble picking that out.

---

