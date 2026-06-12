---
title: "python script not working"
date: 2010-12-15
forum: General Help
---

### Post by ki4jgt on 2010-12-15
I'm trying to run this script in 3.1 IDLE. I get an error with the bolded " below:

```

import os
happy = "sit"
while happy == "sit":
    os.sys('cls')
    F = input("F: ")
    C = (F - 32) * 5 / 9
    print "C:**"**, C

```
Invalid syntax

---

### Post by Ayuthia on 2010-12-15
Python needs tabs for things like while loops or else python will not know where the commands under the while loop ends.

---

### Post by ki4jgt on 2010-12-15
> **Ayuthia said:**
> Python needs tabs for things like while loops or else python will not know where the commands under the while loop ends.

I put the tabs in but the quote thing erased them.

---

### Post by Cheesehead on 2010-12-15
Use the (#) code tags in the forums editor. Or just use "[CODE" and "[/CODE]".

IDLE tells you what line the syntax error is on.
When you get the error, see the liitle red mark on one line? Your problem is on that line (or the one before it).

What is "os.sys('cls')" ?

'print "C:", C' should be 'print("C:", C)'   In Python3, print is considered a function, and what you are printing should be in parenthesis. That's a change from Python2. The lack of parenthesis will cause a syntax error.

---

### Post by ki4jgt on 2010-12-15
> **Cheesehead said:**
> Use the (#) code tags in the forums editor. Or just use "[CODE" and "[/CODE]".

IDLE tells you what line the syntax error is on.
When you get the error, see the liitle red mark on one line? Your problem is on that line (or the one before it).

What is "os.sys('cls')" ?

'print "C:", C' should be 'print("C:", C)'   In Python3, print is considered a function, and what you are printing should be in parenthesis. That's a change from Python2. The lack of parenthesis will cause a syntax error.

My prob is with the last " after the C: os.sys('cls') or os.sys('clear') is to clear the screen so I can do the function over without having to see the previous results on the screen.

It works in 2.6 but not 3.1 :-)

---

