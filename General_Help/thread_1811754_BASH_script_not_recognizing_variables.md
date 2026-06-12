---
title: "BASH script not recognizing variables"
date: 2011-07-25
forum: General Help
---

### Post by chellrose on 2011-07-25
I'm trying to write a bash script, and for some reason Bash doesn't seem to like any of my variables... _except_ the one used in a loop.  What's going on?

Here's a simple version of my bash script which illustrates the problem:
```

#!/bin/bash

MYS = "test string"
echo $MYS

for BL in  0.95 1.00 1.05 1.1 1.2 1.3 1.4 1.5 1.6
do
  echo $BL
done

```And the output:
```

me@mycomp:~ $ ./test.sh
./test.sh: line 6: MYS: command not found

0.95
1.00
1.05
1.1
1.2
1.3
1.4
1.5
1.6

```
The same problem with MYS occurs regardless of its name, whether it is declared or referenced before, after, or inside the loop, and whether it is a string, integer, or floating-point number.  Also, as far as I can tell, everything related to Bash is up to date.

Insight is much appreciated... :)

---

### Post by seawolf167 on 2011-07-25
> **Sissy13 said:**
> 
```

#!/bin/bash

MYS = "test string"
echo $MYS

You need to do the following instead:

[code]MYS="test string"
echo "$MYS"
```

I highly suggest you read through [URL="http://mywiki.wooledge.org/BashGuide"]this BashGuide
[/URL]

---

### Post by kaspar_silas on 2011-07-25
Bash is annoyingly not white-space independent

whilst 

a=5
echo $a

is fine 

a = 5
echo $a
or 
a= 5
echo $a
is not.


Edit: Darn, beaten to the punch.

---

### Post by seawolf167 on 2011-07-25
> **kaspar_silas said:**
> Bash is annoyingly not white-space independent

whilst 

a=5
echo $a

is fine 

a = 5
or 
a= 5

is not.

But even above that, if you store a string in a variable, when expanding that variable, Bash *replaces* the parameter expansion with the string as-is, so the white spaces in the string are now in the expansion which is why quotes are needed around variable expansion

---

### Post by chellrose on 2011-07-25
> **kaspar_silas said:**
> Bash is annoyingly not white-space independent


#-o
And I'm borderline OCD about putting plenty of white-space in my code...
That fixed it.  Thanks, everyone.

*heading over to look at that Bash guide*

---

### Post by seawolf167 on 2011-07-25
No problem - please mark this thread as solved under Thread Tools since it is all working now :)

---

### Post by kaspar_silas on 2011-07-25
O yeah okay. But you only really need quotes when declaring not when he is just echoing, right?

for example I mean:

A="Full of spaces"
B=" is okay."
echo $A$B

Edit: Sorry ignore this I misread your post.

---

### Post by nothingspecial on 2011-07-25
> **seawolf167 said:**
> 

I highly suggest you read through [URL="http://mywiki.wooledge.org/BashGuide"]this BashGuide
[/URL]

Read the pitfalls section as well, not quoting our variables is number one (and two) I think.

---

