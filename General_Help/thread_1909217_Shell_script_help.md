---
title: "Shell script help"
date: 2012-01-14
forum: General Help
---

### Post by wingnut2626 on 2012-01-14
Im working on a shell scripting guide and here is what im typing


#!/bin/zsh
read -p "Please enter type of fruit : " fruit

if [ $fruit = apple ]
        then echo "Good, I like apples"
        else echo "Why dont you like apples"

fi

and when i execute the script it prompts me to enter the type of fruit.  Then regardless of what i use for $fruit i get:

"fruit.sh: 8: [fruit: not found
Why dont you like apples"

Is that the correct execution?  What am I doing wrong.  Thanks!

---

### Post by Telengard C64 on 2012-01-14
If this were Bash, I'd say *quote your variable expansions and string literals*.

FWIW, your script works fine in Bash.

I don't know **zsh**.

**_EDIT_**

From the error message, it looks like your script needs a space character between **[** and **$fruit**. Remember that **[** is just a synonym for **test**.

---

### Post by wingnut2626 on 2012-01-14
Thanks so much!  So simple!

---

### Post by Telengard C64 on 2012-01-14
What was the trouble?

---

### Post by wingnut2626 on 2012-01-15
It actually was the space between "[" and "$fruit"

---

### Post by Telengard C64 on 2012-01-15
So apparently your local copy of the script didn't have the space between **[** and **$**, but the code you posted in your OP did. That's why when I copypasted the script it worked for me without error.

Glad you got it sorted.  :)

---

