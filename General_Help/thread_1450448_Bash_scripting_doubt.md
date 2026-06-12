---
title: "Bash scripting doubt"
date: 2010-04-09
forum: General Help
---

### Post by bala1486 on 2010-04-09
Hello,
 I have a basic doubt in bash scripting.
 I read that "$" symbol is used for expansion. Suppose $var appears in a statement it just substitutes the value of var in that statement.

var=My name is Bala
This is wrong. It needs double quotes as it contains spaces.
right one is 
var="My name is Bala"

Suppose
var="My name is Bala"
con=$var
I thought that the second line is wrong and it should be con="$var".
But bash prints My name is Bala if echo $con is typed. How is this possible? 
The line should have expanded as con=My name is Bala if just substitution is used. What am i misunderstanding in this?

Also command like var=$(ls | grep data) also works the same as var="$(ls | grep data)" even if the result has more than 1 word.

Please explain me..  Thank you..

Thanks,
Bala

---

### Post by darolu on 2010-04-09
Use single quote marks:
```
var='My name is Bala'
con=$var
don='$var'
echo $con
echo $don
```
Which would result in:
```
My name is Bala
$var
```

---

### Post by cjhabs on 2010-04-09
> **darolu said:**
> Use single quote marks:
```
var='My name is Bala'
con=$var
don='$var'
echo $con
echo $don
```
Which would result in:
```
My name is Bala
$var
```

Just to elaborate:
Double quotes allow variable expansion within them, single quotes do not.

---

